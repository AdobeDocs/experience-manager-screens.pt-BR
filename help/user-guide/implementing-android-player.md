---
title: Implementação do Android&trade; Player
description: Saiba mais sobre a implementação do Android&trade; Watchdog, uma solução que permite recuperar falhas no Android&trade; player.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 06082edf3dadbaea1cea142ff624e83bc6045dfd
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 0%

---

# Implementação do Android™ Player {#implementing-android-player}

Esta seção descreve a configuração do Android™ player. Ele fornece informações do arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

Além disso, **Watchdog** O é uma solução para recuperar o reprodutor de falhas. Um aplicativo deve se registrar no serviço de vigia e enviar periodicamente mensagens ao serviço informando que ele está ativo. Caso o serviço de vigia não receba uma mensagem de manutenção de atividade em um tempo estipulado, o serviço tentará reinicializar o dispositivo. Isso é feito para uma recuperação limpa (se tiver privilégios suficientes) ou reinicia o aplicativo.

## Instalação do Android™ Player {#installing-android-player}

Para implementar o Android™ Player para AEM Screens, instale o Android™ Player para AEM Screens.

Visite o [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Configure um ambiente para o reprodutor Android™ se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum** de **Configuração do console da Web do Adobe Experience Manager** em todas as instâncias de autor e publicação do AEM.

Siga as etapas abaixo:

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** usar `http://localhost:4502/system/console/configMgr`.

1. Pesquisar por *Manipulador de autenticação de token do Adobe Granite*.

1. Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.


### Método Ad-Hoc {#ad-hoc-method}

O método ad-hoc permite instalar o Player mais recente da Android™ (*.exe*). Visite o [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
1. Navegue até **Configuração** no menu de ação esquerdo, digite o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Salvar**.

1. Navegue até a **Dispositivo** **Registro** no menu de ação esquerdo para que você possa verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se a variável **Estado** é **REGISTRADO**, você pode ver que a variável **ID do dispositivo** é preenchido.
>
>Se a variável **Estado** é **NÃO REGISTRADO**, você pode usar o **Token** para registrar o dispositivo.

## Implementação do Watchdog da Android™ {#implementing-android-watchdog}

Devido à arquitetura da Android™, a reinicialização do dispositivo exige que o aplicativo tenha privilégios de sistema. Assine o apk usando as chaves de assinatura do fabricante, caso contrário, o watchdog pode reiniciar o aplicativo de reprodução e não reinicializar o dispositivo.

### Sinalização do Android™ `apks` uso de Chaves do Fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acessar algumas APIs privilegiadas do Android™, como *PowerManager* ou *HDMIControlServices*, assine o Android™ `apk` usando as chaves do fabricante.

>[!CAUTION]
>
>Pré-requisitos:
>
>Você deve ter o Android™ SDK instalado antes de executar as etapas a seguir.

Siga as etapas abaixo para assinar o aplicativo Android™ usando as chaves do fabricante:

1. Baixe o aplicativo da Google Play ou do [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) página
1. Obtenha as chaves de plataforma do fabricante para obter uma *pk8* e uma *pem* arquivo

1. Localize o `apksigner` ferramenta no Android™ SDK usando localizar `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Encontre o caminho para a ferramenta de alinhamento do zip no SDK da Android™
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Instalar ***aemscreensaligned.apk*** usando adb install para o dispositivo

## Noções básicas sobre os serviços de vigia da Android™ {#android-watchdog-services}

O serviço de vigia cross-Android™ é implementado como um plug-in Cordova usando *GerenciadorDeAlarmes*.

O diagrama a seguir mostra a implementação do serviço de vigia:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialização** - No momento da inicialização do plug-in Cordova, as permissões são verificadas para ver se você tem privilégios de sistema e, portanto, a permissão Reinicializar. Se esses dois critérios forem atendidos, uma intenção pendente de reinicialização será criada; caso contrário, uma intenção pendente de reiniciar o aplicativo (com base em sua atividade de inicialização) será criada.

**2. Temporizador Keep Alive** - Um temporizador keep-alive é usado para acionar um evento a cada 15 segundos. Nesse caso, cancele a intenção pendente existente (reinicializar ou reiniciar o aplicativo) e registre uma nova intenção pendente pelos mesmos 60 segundos no futuro (essencialmente adiando a reinicialização).

>[!NOTE]
>
>No Android™, a variável *GerenciadorDeAlarmes* é usado para registrar o *pendingIntents* que pode ser executado mesmo se o aplicativo tiver falhado e o delivery do alarme for inexato da API 19 (Kitkat). Mantenha algum espaçamento entre o intervalo do cronômetro e o *do AlarmManager* *pendingIntent* alarme.

**3. Falha do aplicativo** - Se houver uma falha, o pendingIntent para reinicialização registrado com AlarmManager não será mais redefinido. Portanto, ele executa uma reinicialização ou reinicialização do aplicativo (dependendo das permissões disponíveis no momento da inicialização do plug-in Cordova).

## Provisionamento em massa do Android™ Player {#bulk-provision-android-player}

Ao implantar o reprodutor Android™ em massa, é necessário provisionar o reprodutor para apontar para uma instância AEM e configurar outras propriedades sem inseri-las manualmente na interface do administrador.

>[!NOTE]
>Esse recurso está disponível no Android™ player 42.0.372.

Siga as etapas abaixo para permitir o provisionamento em massa no reprodutor Android™:

1. Crie um arquivo JSON de configuração com o nome `player-config.default.json`.
Consulte uma [Exemplo de política JSON](#example-json) e uma tabela que descreve a utilização dos vários [Atributos da política](#policy-attributes).

1. Use um explorador de arquivos MDM, ADB ou Android™ Studio para soltar esse arquivo JSON de política no *sdcard* no dispositivo Android™.

1. Quando o arquivo for implantado, use o MDM para instalar o aplicativo do reprodutor.

1. Quando o aplicativo de reprodução é iniciado, esse arquivo de configuração é lido e aponta para o servidor AEM aplicável, onde ele é registrado e, em seguida, controlado.

   >[!NOTE]
   >Este arquivo é *somente leitura* na primeira vez que o aplicativo é iniciado e não pode ser usado para configurações subsequentes. Se o reprodutor for iniciado antes que o arquivo de configuração seja descartado, basta desinstalar e reinstalar o aplicativo no dispositivo.

### Atributos da política {#policy-attributes}

A tabela a seguir resume os atributos da política com um exemplo de JSON de política para referência:

| **Nome da política** | **Finalidade** |
|---|---|
| *server* | O URL para o servidor do Adobe Experience Manager. |
| *resolution* | A resolução do dispositivo. |
| *rebootSchedule* | O cronograma para reinicializar se aplica a todas as plataformas. |
| *enableAdminUI* | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como *false* depois que estiver totalmente configurado e em produção. |
| *enableOSD* | Habilite a interface do usuário do alternador de canais para que os usuários alternem canais no dispositivo. Considere configurá-la para *false* depois que estiver totalmente configurado e em produção. |
| *enableActivityUI* | Ative se quiser mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| *enableNativeVideo* | Ative se quiser usar aceleração de hardware nativa para reprodução de vídeo (somente Android™). |

### Exemplo de política JSON {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>Todos os dispositivos Android™ têm uma `*sdcard*` pasta se um real `*sdcard*` foi inserido ou não. Esse arquivo, quando implantado, estaria no mesmo nível que a pasta Downloads. Alguns MDMs, como Samsung Knox, podem ver isso *sdcard* local da pasta como *Armazenamento interno*.

## Provisionamento em massa do Android™ Player usando o Enterprise Mobility Management {#bulk-provisioning}

Ao implantar o Android™ player em massa, é entediante registrar cada player manualmente com AEM. Use uma solução EMM (Enterprise Mobility Management, Gerenciamento de mobilidade corporativa) como [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron ou Samsung Knox para que você possa provisionar e gerenciar remotamente sua implantação. O AEM Screens Android™ player oferece suporte ao EMM AppConfig padrão do setor para permitir o provisionamento remoto.

## Nomeação do Android™ Player {#name-android}

Você pode atribuir um nome de dispositivo amigável ao seu reprodutor Android™, enviando o nome de dispositivo atribuído ao AEM (Adobe Experience Manager). Esse recurso não apenas permite que você dê um nome ao seu reprodutor Android™, mas também permite que você atribua facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no reprodutor Android™:

1. Navegue até **configurações** > **Sobre o dispositivo**
1. Edite e defina o nome do dispositivo para dar um nome ao seu reprodutor Android™

### Implementação do provisionamento em massa do Android™ Player usando o Gerenciamento de mobilidade empresarial {#implementation}

Siga as etapas abaixo para permitir o provisionamento em massa no Android™ Player:

1. Verifique se o dispositivo Android™ é compatível com os serviços da Google Play.
1. Inscreva seus dispositivos Android™ Player com sua solução EMM favorita compatível com AppConfig.
1. Faça logon no console do EMM e extraia o aplicativo AEM Screens Player do Google Play.
1. Clique na configuração gerenciada ou na opção relacionada.
1. Agora você deve ver uma lista de opções do player que podem ser configuradas, como servidor e código de registro em massa.
1. Configure esses parâmetros, salve e implante a política nos dispositivos.

   >[!NOTE]
   >Os dispositivos devem receber o aplicativo junto com a configuração. Ele deve apontar para o servidor AEM correto com a configuração selecionada. Se você optar por configurar o código de registro em massa e mantê-lo conforme configurado no AEM, o reprodutor deverá ser capaz de se registrar automaticamente. Se você tiver configurado uma exibição padrão, ela também poderá baixar e mostrar algum conteúdo padrão (que poderá ser alterado posteriormente de acordo com sua conveniência).

Além disso, verifique com o fornecedor de EMM o suporte ao AppConfig. Os mais populares, como [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm), e [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) entre outros, suportam esse padrão do setor.

### Usar o controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre esse recurso aqui: [Controle remoto Screens](implementing-remote-control.md)
