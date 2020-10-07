---
title: Perguntas frequentes da AEM Screens
seo-title: Perguntas frequentes da AEM Screens
description: Siga esta página para obter respostas para perguntas frequentes relacionadas a um projeto da AEM Screens.
seo-description: Siga esta página para obter respostas para perguntas frequentes relacionadas a um projeto da AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: fc923553c3813e6fd659df641f2e4363f0907827
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 2%

---


# Perguntas frequentes da AEM Screens {#aem-screens-faqs}

A seção a seguir fornece respostas para algumas das perguntas frequentes mais frequentes relacionadas a um projeto da AEM Screens.

## Gerenciamento de canais {#channel-management}

### 1. Qual é a diferença entre um canal on-line e off-line? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Um ***Canal online*** mostrará o conteúdo atualizado no ambiente em tempo real, enquanto um ***Canal offline*** mostrará o conteúdo em cache.

### 2. Como faço para fazer um canal on-line? {#how-do-i-make-a-channel-online}

Selecione o canal e navegue até as propriedades do canal na barra de ações. Verifique o modo **Desenvolvedor (force o canal a ficar on-line)** na guia **Canal** para tornar o canal on-line.

### 3. Qual é o uso do campo Função do Canal? {#what-is-the-use-of-the-channel-role-field}

A função do Canal é a abstração do canal real que é executado para que o autor possa focar diretamente na experiência genérica. Você pode pensar nele como um tipo de tag que identifica exclusivamente o canal em seu contexto (exibição ou programação).

### 4. Como a resolução real do canal acontece? {#how-does-actual-channel-resolution-happen}

Para referências ** estáticas, a resolução segue apenas o caminho especificado.

Para referências ** dinâmicas, a resolução ocorre quando o canal é atribuído à exibição (não ao agendamento). O caminho de exibição torna-se o contexto do canal e a resolução ocorre da seguinte forma (prioridade de mais alta a mais baixa):

1. A exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A exibição tem um nó irmão que corresponde ao nome do canal referenciado
1. O local pai da exibição tem um nó filho que corresponde ao nome do canal referenciado
1. O local principal da exibição tem um nó filho que corresponde ao nome do canal referenciado

E assim por diante, até você chegar à pasta de locais e parar lá no momento (de modo que não seja possível fazer referência a um canal que estaria na pasta canais, por exemplo, apenas canais na subárvore de locais).

## Registro do dispositivo {#device-registration}

### 1. Se eu descobrir pontos de extremidade, como solicitações de integração e registro de dispositivos, posso escrever um grande número de dispositivos e registrar esses dispositivos. Além de bloquear esse acesso a uma ramificação Wi-Fi, é possível proteger essas solicitações? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Atualmente, o registro só é possível na instância do autor. Embora o serviço de registro não esteja autenticado, ele só criará um dispositivo pendente no AEM e não registrará o dispositivo nem atribuirá qualquer exibição.

Para registrar um dispositivo (o que significa criar um usuário para o dispositivo no AEM), ainda é necessário autenticar para AEM e, no momento, seguir manualmente o assistente de registro para concluir o registro. Teoricamente, um usuário mal-intencionado pode criar vários dispositivos pendentes, mas não pode se registrar sem um logon AEM.

### 2. Há alguma forma de transformar solicitações de GET HTTP em POST HTTP com alguma forma de autenticação? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

A solicitação de registro é uma solicitação de POST.

É recomendável obter a ID do dispositivo da sessão em vez de passá-la como parâmetro. Isso limparia os registros do servidor, o cache do navegador e assim por diante. Atualmente, não se trata de um problema de segurança. Observe que a GET semântica é usada quando não há alteração de estado no servidor e a POST é usada quando há uma alteração de estado.

### 3. Há uma maneira de recusar uma solicitação de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Não é possível recusar as solicitações de registro. Em vez disso, as solicitações de registro devem expirar após um tempo limite configurado no [Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). Por padrão, esse valor é definido como um dia e é armazenado em um cache de memória.

## Relatórios de monitoramento e integridade do dispositivo {#device-monitoring-and-health-reports}

### 1. Como soluciono problemas se meu AEM Screens player exibir tela em branco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Verifique as seguintes possibilidades para solucionar o problema de tela em branco:

* AEM não consegue mover o conteúdo offline
* Canal não tem conteúdo
* Nenhum dos ativos está programado para mostrar no momento atual

### 2. O que devo fazer se o AEM Screens player não conseguir se registrar e seu estado for exibido como Falha? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

É necessário ativar o Filtro de Quem indicou Apache Sling Permitir vazio. Isso é necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor AEM Screens.

1. Navegue até Configuração do Console da Web do **Adobe Experience Manager**
1. Verifique a opção **allow.empty** .
1. Clique em **Salvar**.

### 3. Como solucionar problemas se, ao registrar um AEM Screens player, o dispositivo mostrar FAILURE e os registros do console exibirem o erro ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Esse problema pode ocorrer se o player não conseguir localizar o DNS do AEM Screens Server. Você pode tentar usar o endereço IP para se conectar. Para obter o IP do servidor, use: *arp &lt;server_dns_name>*.

### 4. O AMS recomenda implementar um Android Watchdog em todos os dispositivos? O plug-in Watchdog (Cordova) está incluído no APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Um monitor Android de plataforma cruzada usando APIs Android puras já faz parte do aplicativo. Nenhum software adicional é necessário, mas dependendo do dispositivo usado, talvez seja necessário renunciar ao aplicativo para obter privilégios de sistema para um ciclo de alimentação completo (PowerManager api). Se não for demitido usando as teclas do fabricante, ele encerrá e reiniciará o aplicativo, mas não iniciará o ciclo de alimentação.

Para obter mais informações sobre como implementar o Android Player, consulte [**Implementação do Android Player**](implementing-android-player.md).

### 5. Que ferramentas de monitoramento remoto e alerta de terceiros (software) o Adobe/AMS recomenda para monitorar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependendo do que você deseja para fora do monitoramento e dos alertas, um novo recurso do serviço AEM Screens Notifications notifica você se um dispositivo não tiver feito o ping em algum tempo. As ferramentas de terceiros dependerão do sistema operacional (SO), dos recursos e das necessidades específicas do cliente.

Para obter mais informações sobre onde você pode monitorar a atividade do dispositivo, consulte o Serviço [**de notificações da**](screens-notifications-service.md) AEM Screens.

## Player do AEM Screens {#aem-screens-player}

### 1. Como instalar o ChromeOS player como plug-in Chrome Browser? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

O ChromeOS player pode ser instalado como plug-in do Chrome Browser no modo de desenvolvedor, sem a necessidade de um dispositivo de player de cromo. Para a instalação, siga as etapas abaixo:

1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
1. Descompacte e salve no disco.
1. Abra o navegador Chrome e selecione **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
1. Ligue o modo **Desenvolvedor** no canto superior direito.
1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
1. Verifique se o plug-in do **AEM Screens Chrome Player** está disponível na lista de extensões.
1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
1. Clique em **AEM Screens** Plugin para iniciar o Chrome Player. Por padrão, o player é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.

### 2. Como solucionar problemas se o Screens player não puder ser autenticado por meio da instância de publicação com o manipulador de erros personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Quando o AEM Screens player for start, ele solicitará a ***/content/screens/svc.ping.json***, quando o player receber um erro 404. O player inicia uma solicitação de autenticação para autenticação na instância de publicação. Se houver um manipulador de erros personalizado na instância de publicação, verifique se você retorna o código de status 404 para usuário anônimo em ***/content/screens/svc.ping.json***.

### 3. Como definir a tela do dispositivo para permanecer em um Android Player? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga as etapas abaixo para ativar a opção Fique acordado em qualquer player Android:

1. Navegue até as configurações do player do Android —> **Sobre**
1. Toque 7 vezes no número de compilação para ativar as Opções **** do desenvolvedor nas **Configurações**
1. Navegue até Opções **do desenvolvedor**
1. Habilitar **permanência**

### 4. Como ativar o modo de janela para o Windows player?{#enable-player}

Não há modo de janela no Windows player. É sempre o modo de tela cheia.

### 5. Como solucionar problemas se um reprodutor do Screens envia solicitações de login continuamente?{#requests-login}

Siga as etapas abaixo para solucionar problemas de um AEM Screens player que envia solicitações continuamente para `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. Quando o AEM Screens player for start, ele solicitará `/content/screens/svc.json`, quando o player receber um código de status 404 na resposta, que o player inicie uma solicitação de autenticação para autenticação `/libs/granite/core/content/login.validate/j_security_check` na instância de publicação. Se houver um manipulador de erros personalizado na instância de publicação, verifique se você retorna o código de status 404 para o usuário anônimo ativado `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Verifique se a configuração do seu dispatcher permite essas solicitações na `/filters` seção. Consulte [Configuração de Filtros](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) de telas para obter mais detalhes.

1. Verifique se as regras de regravação do despachante estão regravando qualquer um dos caminhos de tela para um caminho diferente.

1. Verifique se você tem `/etc/map` regras na instância do *autor* ou da *publicação* e os caminhos de telas são correspondentes a `sling:match` e redirecionados internamente para um caminho diferente. Resolver o url exato em /`system/console/jcrresolver` ajuda a identificar se a instância de *publicação* está regravando esses urls para qualquer outro caminho.

1. Verifique se você tem alguma configuração do Apache Sling Resource Resolver Fatory que está causando regravações internas.

## Dicas gerais de solução de problemas {#general-troubleshooting-tips}

### 1. Como desativar o Livefyre para evitar erros de tela A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para desativar o Livefyre para evitar erros de registro:

1. ***Desative o pacote Livefyre:***

   * Vá até `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Procure o pacote AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`
   * Clique em **Parar**

1. ***Desative o Livefyre poller:***

   * No CRXDE Lite, navegue até `/etc/importers/polling/livefyre-poller/jcr:content`
   * Adicionar uma nova propriedade *ativada* tipo *Booliano*
   * Definir propriedade **** ativada como **falsa**

