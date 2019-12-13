---
title: Perguntas frequentes sobre o AEM Screens
seo-title: Perguntas frequentes sobre o AEM Screens
description: Siga esta página para obter respostas para perguntas frequentes relacionadas a um projeto do AEM Screens.
seo-description: Siga esta página para obter respostas para perguntas frequentes relacionadas a um projeto do AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Perguntas frequentes sobre o AEM Screens {#aem-screens-faqs}

A seção a seguir fornece respostas para algumas das perguntas frequentes relacionadas a um projeto do AEM Screens.

## Gerenciamento de canal {#channel-management}

### 1.Qual é a diferença entre um canal online e um canal offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***Online Channel***, will show the updated content in the real time environment whereas an ***Offline Channel***, shows the cached content.

### 2.Como faço para fazer um canal on-line? {#how-do-i-make-a-channel-online}

Selecione o canal e navegue até as propriedades do canal na barra de ações. Verifique o modo **Desenvolvedor (force o canal a ficar on-line)** na guia **Canal** para tornar o canal on-line.

### 3.Qual é o uso do campo Função de canal? {#what-is-the-use-of-the-channel-role-field}

A Função do canal é a abstração do canal real que é executado para que o autor possa se concentrar diretamente na experiência genérica. Você pode pensar nele como um tipo de tag que identifica exclusivamente o canal em seu contexto (exibição ou programação).

### 4.Como a resolução real do canal acontece? {#how-does-actual-channel-resolution-happen}

Para referências ** estáticas, a resolução segue apenas o caminho especificado.

Para referências ** dinâmicas, a resolução ocorre quando o canal é atribuído à exibição (não ao agendamento). O caminho de exibição torna-se o contexto do canal e a resolução acontece da seguinte forma (da prioridade mais alta à mais baixa):

1. A exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A exibição tem um nó irmão que corresponde ao nome do canal referenciado
1. O local pai da exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A localização principal da exibição tem um nó filho que corresponde ao nome do canal referenciado

E assim por diante, até que você alcance a pasta de locais e pare ali no momento (de modo que não seja possível fazer referência a um canal que estaria na pasta de canais, por exemplo, somente os canais na subárvore de locais).

## Registro do dispositivo {#device-registration}

### 1.Se eu descobrir pontos de extremidade, como solicitações de integração e registro de dispositivos, posso escrever um grande número de dispositivos e registrar esses dispositivos. Além de bloquear esse acesso a uma ramificação Wi-Fi, é possível proteger essas solicitações? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Atualmente, o registro só é possível na instância do autor. Embora o serviço de registro não esteja autenticado, ele só criará um dispositivo pendente no AEM e não registrará o dispositivo nem atribuirá qualquer exibição.

Para registrar um dispositivo (o que significa criar um usuário para o dispositivo no AEM), ainda é necessário autenticar no AEM e, no momento, seguir manualmente o assistente de registro para concluir o registro. Teoricamente, um usuário mal-intencionado pode criar vários dispositivos pendentes, mas não pode se registrar sem um logon do AEM.

### 2.Há alguma forma de transformar solicitações HTTP GET em HTTP POST com alguma forma de autenticação? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

A solicitação de registro é uma solicitação POST.

É recomendável obter a ID do dispositivo da sessão em vez de passá-la como parâmetro. Isso limparia os registros do servidor, o cache do navegador e assim por diante. Atualmente, não se trata de um problema de segurança. Observe que GET semântico é usado quando não há alteração de estado no servidor e POST é usado quando há uma alteração de estado.

### 3.Há uma maneira de recusar uma solicitação de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Não é possível recusar as solicitações de registro. Em vez disso, as solicitações de registro devem expirar após um tempo limite configurado no console [da Web do](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)Adobe Experience Manager. Por padrão, esse valor é definido como um dia e é armazenado em um cache de memória.

## Relatórios de monitoramento e integridade do dispositivo {#device-monitoring-and-health-reports}

### 1.Como soluciono problemas se meu player do AEM Screens mostrar tela em branco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Verifique as seguintes possibilidades para solucionar o problema de tela em branco:

* O AEM não consegue mover o conteúdo offline
* O canal não tem nenhum conteúdo
* Nenhum dos ativos está programado para mostrar no momento atual

### 2.O que fazer se o AEM Screens player não conseguir se registrar e seu estado for exibido como Falha? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

É necessário ativar o Filtro de referência Apache Sling Permitir vazio. Isso é necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor AEM Screens.

1. Navegue até Configuração do console da Web do **Adobe Experience Manager**
1. Verifique a opção **allow.empty** .
1. Clique em **Salvar**.

### 3.Como solucionar problemas se, ao registrar um player do AEM Screens, o dispositivo mostrar FAILURE e os registros do console exibirem o erro ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Esse problema pode ocorrer se o player não conseguir localizar o DNS do servidor do AEM Screens. Você pode tentar usar o endereço IP para se conectar. Para obter o IP do servidor, use: *arp &lt;server_dns_name&gt;*.

### 4.O AMS recomenda implementar um Android Watchdog em todos os dispositivos? O plug-in Watchdog (Cordova) está incluído no APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Um monitor Android de plataforma cruzada usando APIs Android puras já faz parte do aplicativo. Nenhum software adicional é necessário, mas dependendo do dispositivo usado, talvez seja necessário renunciar ao aplicativo para obter privilégios de sistema para um ciclo de alimentação completo (PowerManager api). Se não for demitido usando as teclas do fabricante, ele encerrá e reiniciará o aplicativo, mas não iniciará o ciclo de alimentação.

Para obter mais informações sobre como implementar o Android Player, consulte [**Implementação do Android Player**](implementing-android-player.md).

### 5.Que ferramentas de monitoramento remoto e alerta de terceiros (software) a Adobe/AMS recomenda para monitorar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependendo do que você deseja para fora do monitoramento e dos alertas, um novo recurso AEM Screens Notifications Service notifica você se um dispositivo não tiver feito o ping em algum tempo. As ferramentas de terceiros dependerão do sistema operacional (SO), dos recursos e das necessidades específicas do cliente.

Para obter mais informações sobre onde você pode monitorar a atividade do dispositivo, consulte o Serviço [**de notificações do**](screens-notifications-service.md)AEM Screens.

## Player do AEM Screens {#aem-screens-player}

### 1.Como instalar o ChromeOS player como plug-in Chrome Browser? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

O ChromeOS player pode ser instalado como plug-in do Chrome Browser no modo de desenvolvedor, sem a necessidade de um dispositivo de player de cromo. Para a instalação, siga as etapas abaixo:

1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
1. Descompacte e salve no disco.
1. Abra o navegador Chrome e clique no menu de 3 pontos e selecione **Mais ferramentas** —&gt; **Extensões** no canto superior direito ou navegue diretamente para ***chrome://extensions***.
1. Ligue o modo **Desenvolvedor** no canto superior direito.
1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
1. Verifique o plug-in do Chrome Player **do** AEM Screens se estiver disponível na lista de extensões.
1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
1. Clique em **AEM Screens** Plugin para iniciar o Chrome Player. Por padrão, o player é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.

### 2.Como solucionar problemas se o Screens player não puder ser autenticado por meio da instância de publicação com o manipulador de erros personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Quando o AEM Screens player é iniciado, faz uma solicitação para ***/content/screens/svc.ping.json***, quando o player recebe um erro 404. O player inicia uma solicitação de autenticação para autenticação na instância de publicação. Se houver um manipulador de erros personalizado na instância de publicação, verifique se você retorna o código de status 404 para usuário anônimo em ***/content/screens/svc.ping.json***.

### 3.Como definir a tela do dispositivo para permanecer em um Android Player? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga as etapas abaixo para ativar a opção Fique acordado em qualquer player Android:

1. Navegue até as configurações do Android Player —&gt; **Sobre**
1. Toque 7 vezes no número de compilação para ativar as Opções **** do desenvolvedor nas **Configurações**
1. Navegue até Opções **do desenvolvedor**
1. Habilitar **permanência**

## Dicas gerais de solução de problemas {#general-troubleshooting-tips}

### 1.Como desativar o Livefyre para evitar erros de tela A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para desativar o Livefyre para evitar erros de registro:

1. ***Desative o pacote Livefyre:***

   * Vá até `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Procure o pacote do AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`
   * Clique em **Parar**

1. ***Desative o Livefyre poller:***

   * No CRXDE Lite, navegue até `/etc/importers/polling/livefyre-poller/jcr:content`
   * Adicionar uma nova propriedade *ativada* tipo *Booliano*
   * Definir propriedade **** ativada como **falsa**

