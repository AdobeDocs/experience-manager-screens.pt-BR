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
source-git-commit: a179b6be273b0b0ca166bae755399f8254091ee6
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---


# Implementação do Android Player {#implementing-android-player}

Esta seção descreve como configurar o Android player. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis e recomendações sobre quais configurações usar para desenvolvimento e teste.

Além disso, o **Watchdog** é uma solução para recuperar o player de falhas. Um aplicativo precisa se registrar no serviço de vigilância e depois enviar periodicamente mensagens ao serviço de que ele está vivo. Se o serviço de monitoramento não receber uma mensagem de manutenção de atividade dentro de um tempo estipulado, o serviço tentará reinicializar o dispositivo para uma recuperação limpa (se ele tiver os privilégios suficientes) ou reiniciar o aplicativo.

## Instalação do Android Player {#installing-android-player}

Para implementar o Android Player para AEM Screens, instale o Android Player para AEM Screens.

Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) .

### Configuração do Ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

Você deve configurar um ambiente para o Android player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o atributo **SameSite para os cookies** de token de login do **Lax** para **None** do **Adobe Experience Manager Web ConsoleConfiguration** em todas as instâncias de autor e publicação AEM.

Siga as etapas abaixo:

1. Navegue até **Adobe Experience Manager Web ConsoleConfiguration** usando `http://localhost:4502/system/console/configMgr`.

1. Procure por *Adobe Granite Token Authentication Handler*.

1. Defina o atributo **SameSite para os cookies** do token de login de **Lax** para **None**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.


### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Android Player mais recente (*.exe*). Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) .

Depois de baixar o aplicativo, siga as etapas no player para concluir a instalação ad-hoc:

1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
1. Navegue até **Configuração** no menu de ação esquerdo e digite o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Salvar**.

1. Navegue até o link **Device** **Registration** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se o **Estado** for **REGISTRADO**, você observará que o campo ID **do** dispositivo será preenchido.
>
>Se o **estado** for **NÃO REGISTRADO**, você poderá usar o **token** para registrar o dispositivo.

## Implementação do Android Watchdog {#implementing-android-watchdog}

Devido à arquitetura do Android, a reinicialização do dispositivo requer que o aplicativo tenha privilégios de sistema. Para fazer isso, é necessário assinar o aplicativo usando as chaves de assinatura do fabricante; caso contrário, o watchdog reiniciará o aplicativo do player e não reinicializará o dispositivo.

### Sinalização de aplicativos Android usando chaves do fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acessar algumas das APIs privilegiadas do Android, como *PowerManager* ou *HDMIControlServices*, é necessário assinar o aplicativo android usando as chaves do fabricante.

>[!CAUTION]
>
>Pré-requisitos:
>
>Você deve ter o Android SDK instalado antes de executar as etapas a seguir.

Siga as etapas abaixo para assinar o aplicativo android usando as teclas do fabricante:

1. Baixe o aplicativo do Google Play ou da página Downloads [do](https://download.macromedia.com/screens/) AEM Screens Player
1. Obtenha as chaves da plataforma do fabricante para obter um arquivo *pk8* e um arquivo *pem*

1. Localize a ferramenta para o assinante no sdk do Android usando localizar ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Encontre o caminho para a ferramenta de alinhamento de zip no android sdk
1. &lt;pathto> /zipalignment -fv 4 aemscreensplayer.apk aemscreensalinhado.apk
1. Instale o ***aemscreensalinhado.apk*** usando a instalação do adb no dispositivo

## Implementação do Android Watchdog {#android-watchdog-implementation}

O serviço de vigia entre Android é implementado como um plug-in do cordova usando o *AlarmManager*.

O diagrama a seguir mostra a implementação do serviço de vigilância:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Inicialização** No momento da inicialização do plug-in cordova, as permissões são verificadas para ver se temos privilégios de sistema e, portanto, a permissão Reinicialização. Se esses dois critérios forem atendidos, um Propósito de reinicialização pendente será criado, caso contrário, um Propósito pendente de reiniciar o aplicativo (com base na Atividade de inicialização) será criado.

**2. Manter temporizador** ativoUm temporizador de manutenção ativo é usado para disparar um evento a cada 15 segundos. Nesse evento, você precisa cancelar o propósito pendente existente (reiniciar ou reiniciar o aplicativo) e registrar um novo propósito pendente pelos mesmos 60 segundos no futuro (essencialmente adiando a reinicialização).

>[!NOTE]
>
>No Android, o *AlarmManager* é usado para registrar os *pensamentos* pendentes que podem ser executados mesmo se o aplicativo falhar e seu delivery de alarme não for exato da API 19 (Kitkat). Mantenha algum espaçamento entre o intervalo do timer e o alarme do *AlarmManager&#39;* *pendenteIntent* .

**3. Falha** do aplicativo Em caso de falha, o pendenteIntent for Reboot registrado no AlarmManager não é mais redefinido e, portanto, executa uma reinicialização ou reinicialização do aplicativo (dependendo das permissões disponíveis no momento da inicialização do plug-in cordova).
