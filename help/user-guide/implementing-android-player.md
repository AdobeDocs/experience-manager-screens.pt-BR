---
title: Implementação do Android Player
seo-title: Implementação do reprodutor Android
description: Siga esta página para saber mais sobre a implementação do Android Watchdog, uma solução para recuperar o reprodutor de falhas.
seo-description: Siga esta página para saber mais sobre a implementação do Android Watchdog, uma solução para recuperar o reprodutor de falhas.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administração do Screens, reprodutor do Android
role: Administrador
level: Intermediário
translation-type: tm+mt
source-git-commit: 4dd6d40603f4a54ede67c35b07373ac6c6649d3f
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 1%

---


# Implementação do Android Player {#implementing-android-player}

Esta seção descreve como configurar o Android player. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

Além disso, **Watchdog** é uma solução para recuperar o reprodutor de falhas. Um aplicativo precisa se registrar no serviço de vigilância e enviar mensagens periodicamente ao serviço de que está vivo. Caso o serviço de watchdog não receba uma mensagem keep-alive dentro de um tempo determinado, o serviço tenta reinicializar o dispositivo para uma recuperação limpa (se ele tiver os privilégios suficientes) ou reiniciar o aplicativo.

## Instalar o reprodutor do Android {#installing-android-player}

Para implementar o Android Player no AEM Screens, instale o Android Player no AEM Screens.

Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Você deve configurar um ambiente para o Android player, se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o atributo **SameSite para os cookies do token de login** de **Lax** para **None** de **Configuração do console da Web Adobe Experience Manager** em todas as instâncias de criação e publicação AEM.

Siga as etapas abaixo:

1. Navegue até **Configuração do Adobe Experience Manager Web Console** usando `http://localhost:4502/system/console/configMgr`.

1. Procure por *Adobe Granite Token Authentication Handler*.

1. Defina o atributo **SameSite para os cookies do token de login** de **Lax** para **None**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.


### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Player do Android mais recente (*.exe*). Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel do administrador.
1. Navegue até **Configuration** a partir do menu de ação esquerdo e insira o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Save**.

1. Navegue até o link **Device** **Registration** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se **State** for **REGISTERED**, você notará que o campo **Device id** será preenchido.
>
>Se **State** for **UNREGISTERED**, você poderá usar o **Token** para registrar o dispositivo.

## Implementando o Android Watchdog {#implementing-android-watchdog}

Devido à arquitetura do Android, a reinicialização do dispositivo requer que o aplicativo tenha privilégios de sistema. Para fazer isso, é necessário assinar o apk usando as chaves de assinatura do fabricante; caso contrário, o watchdog reiniciará o aplicativo do reprodutor e não reinicializará o dispositivo.

### Sinalização de aplicativos Android usando Chaves de Fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acessar algumas das APIs privilegiadas do Android, como *PowerManager* ou *HDMIControlServices*, é necessário assinar o painel do Android usando as chaves do fabricante.

>[!CAUTION]
>
>Pré-requisitos:
>
>Você deve ter o SDK do android instalado antes de executar as etapas a seguir.

Siga as etapas abaixo para assinar o aplicativo android usando as chaves do fabricante:

1. Baixe o apk do Google Play ou da página [Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
1. Obtenha as chaves da plataforma do fabricante para obter um *pk8* e um arquivo *pem*

1. Localize a ferramenta do assinante no sdk do android usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Encontre o caminho para a ferramenta zip align no android sdk
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instale o ***aemscreensalign.apk*** usando a instalação do adb no dispositivo

## Noções básicas sobre os serviços do Android Watchdog {#android-watchdog-services}

O serviço de monitoramento entre Android é implementado como um plug-in cordova usando *AlarmManager*.

O diagrama a seguir mostra a implementação do serviço de vigilância:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialização** No momento da inicialização do plug-in cordova, as permissões são verificadas para ver se temos privilégios de sistema e, portanto, a permissão Reinicialização . Se esses dois critérios forem atendidos, um Propósito pendente de reinicialização será criado; caso contrário, um Propósito pendente de reiniciar o aplicativo (com base em sua Atividade de inicialização) será criado.

**2. Keep Alive Timer** Um temporizador keep alive é usado para acionar um evento a cada 15 segundos. Nesse caso, você precisa cancelar a intenção pendente existente (para reiniciar ou reiniciar o aplicativo) e registrar uma nova intenção pendente por 60 segundos no futuro (essencialmente adiar a reinicialização).

>[!NOTE]
>
>No Android, o *AlarmManager* é usado para registrar o *pendingIntents* que pode ser executado mesmo que o aplicativo tenha travado e a entrega do alarme seja inexata da API 19 (Kitkat). Mantenha algum espaçamento entre o intervalo do cronômetro e o alarme *AlarmManager&#39;s* *pendingIntent&#39;s*.

**3. Falha do aplicativo** No caso de uma falha, o pendingIntent for Reboot registrado com o AlarmManager não é mais redefinido e, portanto, executa uma reinicialização ou reinicialização do aplicativo (dependendo das permissões disponíveis no momento da inicialização do plug-in cordova).

## Provisionamento em massa do reprodutor Android {#bulk-provision-android-player}

Ao implantar o reprodutor do Android em massa, é necessário provisionar o reprodutor para apontar para uma instância do AEM, bem como configurar outras propriedades sem inseri-las manualmente na interface do usuário do administrador.

>[!NOTE]
>Esse recurso está disponível no Android player 42.0.372.

Siga as etapas abaixo para permitir o provisionamento em massa no reprodutor Android:

1. Crie um arquivo JSON de configuração com o nome `player-config.default.json`.
Consulte um [Exemplo de política JSON](#example-json), bem como uma tabela que descreve o uso dos vários [Atributos de política](#policy-attributes).

1. Use um explorador de arquivos MDM ou ADB ou Android Studio para soltar esse arquivo JSON de política na pasta *sdcard* no dispositivo Android.

1. Depois que o arquivo for implantado, use o MDM para instalar o aplicativo do reprodutor.

1. Quando o aplicativo do reprodutor for iniciado, ele lerá esse arquivo de configuração e apontará para o servidor de AEM aplicável, onde ele pode ser registrado e controlado posteriormente.

   >[!NOTE]
   >Este arquivo é *somente leitura* na primeira vez que o aplicativo é iniciado e não pode ser usado para configurações subsequentes. Se o reprodutor for iniciado antes da queda do arquivo de configuração, basta desinstalar e reinstalar o aplicativo no dispositivo.

### Atributos de política {#policy-attributes}

A tabela a seguir resume os atributos de política com um exemplo de JSON de política para referência:

| **Nome da política** | **Propósito** |
|---|---|
| *server* | O URL para o servidor Adobe Experience Manager. |
| *resolução* | A resolução do dispositivo. |
| *reotSchedule* | O agendamento para reinicialização se aplica a todas as plataformas. |
| *enableAdminUI* | Ative a interface do usuário do administrador para configurar o dispositivo no site. Defina como *false* assim que estiver totalmente configurado e em produção. |
| *enableOSD* | Ative a interface do usuário do seletor de canal para que os usuários alternem os canais no dispositivo. Considere configurar para *false* assim que estiver totalmente configurado e em produção. |
| *enableActivityUI* | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative assim que estiver totalmente configurado e em produção. |
| *enableNativeVideo* | Ative o uso da aceleração de hardware nativa para reprodução de vídeo (somente Android). |

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
>Todos os dispositivos Android têm uma pasta *sdcard* se um *sdcard* real estiver inserido ou não. Esse arquivo, quando implantado, estaria no mesmo nível da pasta Downloads. Alguns MDMs como Samsung Knox podem se referir a esse local de pasta *sdcard* como *Internal storage*.

## Provisionamento em massa do reprodutor Android usando o Enterprise Mobility Management {#bulk-provisioning}

Ao implantar o reprodutor Android em massa, é entediante registrar manualmente cada reprodutor com AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron ou Samsung Knox para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android player é compatível com o EMM AppConfig padrão do setor para permitir provisionamento remoto.

### Implementação do provisionamento em massa do Android Player usando o Enterprise Mobility Management {#implementation}

Siga as etapas abaixo para permitir o provisionamento em massa no Android Player:

1. Certifique-se de que o dispositivo Android seja compatível com os serviços do Google Play.
1. Registre seus dispositivos Android player com sua solução EMM favorita compatível com o AppConfig.
1. Faça logon no console do EMM e extraia o aplicativo AEM Screens Player do Google Play.
1. Selecione a configuração gerenciada (ou a opção relacionada).
1. Agora, você deve ver uma lista de opções do player que podem ser configuradas (como servidor e código de registro em massa).
1. Configure esses parâmetros, salve e implante a política nos dispositivos.

   >[!NOTE]
   >Os dispositivos devem receber o aplicativo junto com a configuração e apontar para o servidor de AEM correto com a configuração selecionada. Se você optar por configurar o código de registro em massa e mantê-lo igual ao configurado no AEM, o reprodutor deverá ser capaz de se registrar automaticamente. Se você tiver configurado uma exibição padrão, ela também poderá baixar e mostrar algum conteúdo padrão (que poderá ser alterado posteriormente de acordo com sua conveniência).

Além disso, verifique com seu fornecedor de EMM o suporte ao AppConfig. Os mais populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox 1/> entre outros, são compatíveis com esse padrão do setor.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)
