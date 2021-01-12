---
title: Implementação do Android Player
seo-title: Implementação do Android Player
description: Siga esta página para saber como implementar o Android Watchdog, uma solução para recuperar o player de falhas.
seo-description: Siga esta página para saber como implementar o Android Watchdog, uma solução para recuperar o player de falhas.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: 2b72d9a83735beb327f519a66e8b3c0e8bf04409
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 1%

---


# Implementação do Android Player {#implementing-android-player}

Esta seção descreve como configurar o Android player. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis e recomendações sobre quais configurações usar para desenvolvimento e teste.

Além disso, **Watchdog** é uma solução para recuperar o player de falhas. Um aplicativo precisa se registrar no serviço de vigilância e depois enviar periodicamente mensagens ao serviço de que ele está vivo. Se o serviço de monitoramento não receber uma mensagem de manutenção de atividade dentro de um tempo estipulado, o serviço tentará reinicializar o dispositivo para uma recuperação limpa (se ele tiver os privilégios suficientes) ou reiniciar o aplicativo.

## Instalação do Android Player {#installing-android-player}

Para implementar o Android Player para AEM Screens, instale o Android Player para AEM Screens.

Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Configuração do Ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Você deve configurar um ambiente para o Android player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o atributo **SameSite para os cookies de token de login** de **Lax** para **None** de **Configuração do Adobe Experience Manager Web Console** em todas as instâncias de autor e publicação AEM.

Siga as etapas abaixo:

1. Navegue até **Configuração do Adobe Experience Manager Web Console** usando `http://localhost:4502/system/console/configMgr`.

1. Procure *Adobe Granite Token Authentication Handler*.

1. Defina o atributo **SameSite para os cookies de token de login** de **Lax** para **None**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.


### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Android Player mais recente (*.exe*). Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Depois de baixar o aplicativo, siga as etapas no player para concluir a instalação ad-hoc:

1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
1. Navegue até **Configuração** no menu de ação esquerdo e digite o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Salvar**.

1. Navegue até o link **Dispositivo** **Registro** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se **State** for **REGISTERED**, você observará que o campo **Device id** será preenchido.
>
>Se **State** for **UNREGISTERED**, poderá utilizar o **Token** para registrar o dispositivo.

## Implementação do Android Watchdog {#implementing-android-watchdog}

Devido à arquitetura do Android, a reinicialização do dispositivo requer que o aplicativo tenha privilégios de sistema. Para fazer isso, é necessário assinar o aplicativo usando as chaves de assinatura do fabricante; caso contrário, o watchdog reiniciará o aplicativo do player e não reinicializará o dispositivo.

### Sinalização de aplicativos Android usando Chaves de Fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acessar algumas das APIs privilegiadas do Android, como *PowerManager* ou *HDMIControlServices*, é necessário assinar o aplicativo Android usando as chaves do fabricante.

>[!CAUTION]
>
>Pré-requisitos:
>
>Você deve ter o Android SDK instalado antes de executar as etapas a seguir.

Siga as etapas abaixo para assinar o aplicativo android usando as teclas do fabricante:

1. Baixe o aplicativo do Google Play ou da página [Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
1. Obtenha as chaves da plataforma do fabricante para obter um arquivo *pk8* e *pem*

1. Localize a ferramenta para o assinante no sdk do Android usando localizar ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Encontre o caminho para a ferramenta de alinhamento de zip no android sdk
1. &lt;pathto> /zipalignment -fv 4 aemscreensplayer.apk aemscreensalinhado.apk
1. Instale ***aemscreensalinhado.apk*** usando a instalação do adb no dispositivo

## Noções básicas sobre os serviços do Android Watchdog {#android-watchdog-services}

O serviço de monitoramento entre Android é implementado como um plug-in do cordova usando *AlarmManager*.

O diagrama a seguir mostra a implementação do serviço de vigilância:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialização** No momento da inicialização do plug-in cordova, as permissões são verificadas para ver se temos privilégios de sistema e, portanto, a permissão Reinicializar. Se esses dois critérios forem atendidos, um Propósito de reinicialização pendente será criado, caso contrário, um Propósito pendente de reiniciar o aplicativo (com base na Atividade de inicialização) será criado.

**2. Temporizador Keep Alive** Um temporizador keep live é usado para acionar um evento a cada 15 segundos. Nesse evento, você precisa cancelar o propósito pendente existente (reiniciar ou reiniciar o aplicativo) e registrar um novo propósito pendente pelos mesmos 60 segundos no futuro (essencialmente adiando a reinicialização).

>[!NOTE]
>
>No Android, o *AlarmManager* é usado para registrar os *pensamentos pendentes* que podem ser executados mesmo que o aplicativo tenha travado e seu delivery de alarme seja inexato da API 19 (Kitkat). Mantenha algum espaçamento entre o intervalo do temporizador e o alarme *AlarmManager&#39;s* *pendenteIntent*.

**3. Falha do aplicativo** Em caso de falha, o pendenteIntent para reinicialização registrado no AlarmManager não é mais redefinido e, portanto, executa uma reinicialização ou reinicialização do aplicativo (dependendo das permissões disponíveis no momento da inicialização do plug-in cordova).

## Provisionamento em massa do Android Player {#bulk-provision-android-player}

Ao implantar o player Android em massa, é necessário provisionar o player para apontar para uma instância AEM, bem como configurar outras propriedades sem inseri-las manualmente na interface do usuário do Admin.

>[!NOTE]
>Este recurso está disponível no Android player 42.0.372.

Siga as etapas abaixo para permitir o provisionamento em massa no player Android:

1. Crie um arquivo JSON de configuração com o nome `player-config.default.json`.
Consulte uma [Exemplo de Política JSON](#example-json), bem como uma tabela que descreve o uso dos vários [Atributos de Política](#policy-attributes).

1. Use um explorador de arquivos MDM ou ADB ou Android Studio para soltar esse arquivo JSON de política na pasta *sdcard* no dispositivo Android.

1. Depois que o arquivo for implantado, use o MDM para instalar o aplicativo do player.

1. Quando o aplicativo do player for iniciado, ele lerá esse arquivo de configuração e apontará para o servidor AEM aplicável, onde ele poderá ser registrado e subsequentemente controlado.

   >[!NOTE]
   >Este arquivo é *somente leitura* na primeira vez que o aplicativo é iniciado e não pode ser usado para configurações subsequentes. Se o player for iniciado antes que o arquivo de configuração seja descartado, basta desinstalar e reinstalar o aplicativo no dispositivo.

### Atributos de política {#policy-attributes}

A tabela a seguir resume os atributos de política com um exemplo de política JSON para referência:

| **Nome da política** | **Propósito** |
|---|---|
| *server* | O URL para o servidor Adobe Experience Manager. |
| *resolução* | A resolução do dispositivo. |
| *rebootSchedule* | O agendamento para reinicialização se aplica a todas as plataformas. |
| *enableAdminUI* | Ative a interface de usuário do administrador para configurar o dispositivo no site. Defina como *false* quando estiver totalmente configurado e em produção. |
| *enableOSD* | Ative a interface do comutador de canais para que os usuários alternem canais no dispositivo. Considere a configuração como *false* depois de estar totalmente configurada e em produção. |
| *enableActivityUI* | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desabilite-o assim que estiver totalmente configurado e em produção. |
| *enableNativeVideo* | Ative para usar a aceleração de hardware nativa para reprodução de vídeo (somente Android). |

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
>Todos os dispositivos Android têm uma pasta *sdcard* se um *sdcard* real está inserido ou não. Esse arquivo quando implantado seria do mesmo nível da pasta Downloads. Alguns MDMs, como Samsung Knox, podem se referir ao *local da pasta sdcard* como *armazenamento interno*.