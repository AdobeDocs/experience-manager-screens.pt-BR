---
title: Implementação do Android Player
seo-title: Implementation of Android Player
description: Siga esta página para saber mais sobre a implementação do Android Watchdog, uma solução para recuperar o reprodutor de falhas.
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 8d4a7b2bc436d822c673a00437ee895c8ef5cb6f
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Implementação do Android Player {#implementing-android-player}

Esta seção descreve a configuração do Android Player. Ele fornece informações do arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

Além disso, **Watchdog** O é uma solução para recuperar o reprodutor de falhas. Um aplicativo precisa se registrar no serviço de vigia e enviar periodicamente mensagens para o serviço informando que ele está ativo. Caso o serviço de vigia não receba uma mensagem de manutenção de atividade em um tempo estipulado, o serviço tentará reinicializar o dispositivo para uma recuperação limpa (se ele tiver privilégios suficientes) ou reiniciar o aplicativo.

## Instalação do Android Player {#installing-android-player}

Para implementar o Android Player para AEM Screens, instale o Android Player para AEM Screens.

Visite o [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Você deve configurar um ambiente para o Android Player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum** de **Configuração do console da Web do Adobe Experience Manager** em todas as instâncias de autor e publicação do AEM.

Siga as etapas abaixo:

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** usar `http://localhost:4502/system/console/configMgr`.

1. Pesquisar por *Manipulador de autenticação de token do Adobe Granite*.

1. Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.


### Método Ad-Hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Player mais recente do Android (*.exe*). Visita [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
1. Navegue até **Configuração** no menu de ação esquerdo, digite o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Salvar**.

1. Navegue até a **Dispositivo** **Registro** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se a variável **Estado** é **REGISTRADO**, você observará o **ID do dispositivo** será preenchido.
>
>Se a variável **Estado** é **NÃO REGISTRADO**, você pode usar o **Token** para registrar o dispositivo.

## Implementação do Watchdog do Android {#implementing-android-watchdog}

Devido à arquitetura do Android, a reinicialização do dispositivo requer que o aplicativo tenha privilégios de sistema. Para fazer isso, você precisa assinar o apk usando as chaves de assinatura do fabricante, caso contrário, o watchdog reiniciará o aplicativo de reprodução e não reinicializará o dispositivo.

### Sinalização de apks Android usando chaves do fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acessar algumas APIs privilegiadas do Android, como *PowerManager* ou *HDMIControlServices*, você precisa assinar o apk android usando as chaves do fabricante.

>[!CAUTION]
>
>Pré-requisitos:
>
>Você deve ter o Android SDK instalado antes de executar as etapas a seguir.

Siga as etapas abaixo para assinar o apk android usando as chaves do fabricante:

1. Baixe o aplicativo da Google Play ou do [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) página
1. Obtenha as chaves de plataforma do fabricante para obter um *pk8* e uma *pem* arquivo

1. Localize a ferramenta apksigner no Android Sdk usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Encontre o caminho para a ferramenta de alinhamento do zip no Android Sdk
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Instalar ***aemscreensaligned.apk*** usando adb install para o dispositivo

## Noções básicas sobre os serviços de Watchdog do Android {#android-watchdog-services}

O serviço de vigia entre Android é implementado como um plug-in cordova usando *GerenciadorDeAlarmes*.

O diagrama a seguir mostra a implementação do serviço de vigia do:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialização** No momento da inicialização do plug-in cordova, as permissões são verificadas para ver se temos privilégios de sistema e, portanto, a permissão Reinicializar. Se esses dois critérios forem atendidos, uma intenção pendente de reinicialização será criada; caso contrário, uma intenção pendente de reiniciar o aplicativo (com base em sua atividade de inicialização) será criada.

**2. Temporizador Keep Alive** Um temporizador keep-alive é usado para acionar um evento a cada 15 segundos. Nesse caso, é necessário cancelar a intenção pendente existente (reinicializar ou reiniciar o aplicativo) e registrar uma nova intenção pendente pelos mesmos 60 segundos no futuro (essencialmente adiando a reinicialização).

>[!NOTE]
>
>No Android, a variável *GerenciadorDeAlarmes* é usado para registrar o *pendingIntents* que pode ser executado mesmo se o aplicativo tiver falhado e o delivery do alarme for inexato da API 19 (Kitkat). Mantenha algum espaçamento entre o intervalo do cronômetro e o *do AlarmManager* *pendingIntent* alarme.

**3. Falha do aplicativo** No caso de uma falha, o pendingIntent para reinicialização registrado com o AlarmManager não é mais redefinido e, portanto, executa uma reinicialização ou reinicialização do aplicativo (dependendo das permissões disponíveis no momento da inicialização do plug-in cordova).

## Provisionamento em massa do Android Player {#bulk-provision-android-player}

Ao implantar o reprodutor Android em massa, é necessário provisionar o reprodutor para apontar para uma instância de AEM, bem como configurar outras propriedades sem inserir manualmente essas propriedades na interface do administrador.

>[!NOTE]
>Esse recurso está disponível no Android player 42.0.372.

Siga as etapas abaixo para permitir o provisionamento em massa no reprodutor Android:

1. Crie um arquivo JSON de configuração com o nome `player-config.default.json`.
Consulte uma [Exemplo de política JSON](#example-json) bem como uma tabela que descreve a utilização dos vários [Atributos da política](#policy-attributes).

1. Use um explorador de arquivos MDM, ADB ou Android Studio para soltar esse arquivo JSON de política no *sdcard* no dispositivo Android.

1. Depois que o arquivo for implantado, use o MDM para instalar o aplicativo do reprodutor.

1. Quando o aplicativo reprodutor for iniciado, ele lerá esse arquivo de configuração e apontará para o servidor AEM aplicável, onde ele poderá ser registrado e controlado subsequentemente.

   >[!NOTE]
   >Este arquivo é *somente leitura* na primeira vez que o aplicativo é iniciado e não pode ser usado para configurações subsequentes. Se o reprodutor for iniciado antes que o arquivo de configuração seja descartado, basta desinstalar e reinstalar o aplicativo no dispositivo.

### Atributos da política {#policy-attributes}

A tabela a seguir resume os atributos da política com um exemplo de JSON de política para referência:

| **Nome da política** | **Propósito** |
|---|---|
| *servidor* | O URL para o servidor do Adobe Experience Manager. |
| *resolução* | A resolução do dispositivo. |
| *rebootSchedule* | O cronograma para reinicializar se aplica a todas as plataformas. |
| *enableAdminUI* | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como *false* depois que estiver totalmente configurado e em produção. |
| *enableOSD* | Habilite a interface do alternador de canal para que os usuários alternem canais no dispositivo. Considere configurar como *false* depois que estiver totalmente configurado e em produção. |
| *enableActivityUI* | Permite mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| *enableNativeVideo* | Permitir o uso da aceleração de hardware nativa para reprodução de vídeo (somente Android). |

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
>Todos os dispositivos Android têm um *sdcard* pasta se um real *sdcard* foi inserido ou não. Esse arquivo, quando implantado, estaria no mesmo nível que a pasta Downloads. Alguns MDMs, como Samsung Knox, podem se referir a isso *sdcard* local da pasta como *Armazenamento interno*.

## Provisionamento em massa do Android Player usando o Enterprise Mobility Management {#bulk-provisioning}

Ao implantar o reprodutor Android em massa, é entediante registrar manualmente cada um dos reprodutores com AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management), como VMWare Airwatch, MobileIron ou Samsung Knox, para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android Player oferece suporte ao EMM AppConfig padrão do setor para permitir o provisionamento remoto.

## Nomeação do reprodutor Android {#name-android}

Você pode atribuir um nome de dispositivo amigável ao seu reprodutor Android, enviando assim o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o player do Android, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no reprodutor Android:

1. Navegue até **configurações** —> **Sobre o dispositivo**
1. Edite e defina o nome do dispositivo para nomear o player do Android

### Implementação do provisionamento em massa do Android Player usando o Gerenciamento de mobilidade empresarial {#implementation}

Siga as etapas abaixo para permitir o provisionamento em massa no Android Player:

1. Verifique se o dispositivo Android oferece suporte aos serviços da Google Play.
1. Inscreva seus dispositivos Android player com sua solução EMM favorita compatível com AppConfig.
1. Faça logon no console do EMM e extraia o aplicativo AEM Screens Player do Google Play.
1. Selecione a configuração gerenciada ou a opção relacionada.
1. Agora você deve ver uma lista de opções do player que podem ser configuradas, como servidor e código de registro em massa.
1. Configure esses parâmetros, salve e implante a política nos dispositivos.

   >[!NOTE]
   >Os dispositivos devem receber o aplicativo junto com a configuração e apontar para o servidor AEM correto com a configuração selecionada. Se você optar por configurar o código de registro em massa e mantê-lo conforme configurado no AEM, o reprodutor deverá ser capaz de se registrar automaticamente. Se você tiver configurado uma exibição padrão, ela também poderá baixar e mostrar algum conteúdo padrão (que poderá ser alterado posteriormente de acordo com sua conveniência).

Além disso, você deve consultar o fornecedor de EMM sobre o suporte ao AppConfig. Os mais populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Ferro móvel](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [UEM do Blackberry](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) entre outros, suportam esse padrão do setor.

### Uso do controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre esse recurso aqui: [Controle remoto do Screens](implementing-remote-control.md)
