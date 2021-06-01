---
title: Perguntas frequentes do AEM Screens
seo-title: Perguntas frequentes do AEM Screens
description: Siga esta página para obter respostas para as perguntas frequentes relacionadas a um projeto do AEM Screens.
seo-description: Siga esta página para obter respostas para as perguntas frequentes relacionadas a um projeto do AEM Screens.
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
feature: Sinalização digital, conteúdo
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 1%

---


# Perguntas frequentes do AEM Screens {#aem-screens-faqs}

A seção a seguir fornece respostas para algumas das perguntas frequentes mais frequentes relacionadas a um projeto do AEM Screens.

## Problema de tela em branco {#blank-screen}

>[!NOTE]
>As verificações obrigatórias listadas que devem ser tentadas pelo suporte principal ou pelo suporte do lado do cliente antes de levantar um problema.

### 1. Quais devem ser as etapas de solução de problemas de primeiros socorros para qualquer cliente que enfrente uma tela preta ou não reproduz conteúdo? {#troubleshooting-blank-screen}

* Verifique se a visualização do canal está funcionando.
* Verifique se a visualização de exibição está funcionando
* Tente registrar o reprodutor como uma extensão de navegador em seu sistema para a mesma exibição e verificar se isso está funcionando.
* Com o player em execução no sistema, navegue até `http://localhost:24502`. Verifique se todo o conteúdo foi baixado corretamente.
* Verifique se as representações apropriadas foram criadas e se a representação correta está sendo reproduzida.
* Verifique se há conteúdo programado e se os horários estão corretos. Verifique se o tempo configurado no reprodutor está correto.
* Inspect os registros do console do player e verifique se há erros. Clique com o botão direito do mouse e inspecione para ver os logs do console. Se estiver usando o windows player, pressione `CTRL + ALT +I` para ativar o console dev para visualizar os logs.

### 2. Como resolver o problema de tela cinza no AEM Screens criando um canal ou cronograma padrão?

Para evitar as telas em branco ou em cinza no campo , crie um canal ou programação global padrão, atribuído a cada exibição com a menor prioridade 1. No caso, algo dá errado com atualizações de conteúdo (devido a rede, reprodutor, servidor ou replicação), já que os players têm esse conteúdo já armazenado em cache no disco, que deve ser reproduzido corretamente e evitar as telas cinza.

Todo o outro conteúdo, como canais ou agendamentos, terá prioridade maior que 1, portanto, o outro conteúdo tem prioridade e o conteúdo de canal global ou agendamento (com prioridade 1) será reproduzido somente como uma opção de fallback.

## Gerenciamento de canal {#channel-management}

### 1. Qual é a diferença entre um canal online e offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Um ***Canal online*** mostrará o conteúdo atualizado no ambiente em tempo real, enquanto um ***Canal offline*** mostrará o conteúdo em cache.

### 2. Como faço para criar um canal online? {#how-do-i-make-a-channel-online}

Selecione o canal e navegue até as propriedades do canal na barra de ações. Marque o **Modo do desenvolvedor (forçar o canal a ficar online)** na guia **Canal** para tornar o canal online.

### 3. Qual é o uso do campo Função do canal? {#what-is-the-use-of-the-channel-role-field}

A Função do canal é a abstração do canal real que é executado para que o autor possa se concentrar diretamente na experiência genérica. Pense nele como um tipo de tag que identifica exclusivamente o canal em seu contexto (exibição ou programação).

### 4. Como a resolução de canal real acontece? {#how-does-actual-channel-resolution-happen}

Para *referências estáticas*, a resolução segue apenas o caminho especificado.

Para *referências dinâmicas*, a resolução ocorre quando o canal é atribuído à exibição (não ao agendamento). O caminho de exibição torna-se o contexto do canal e a resolução acontece da seguinte maneira (da prioridade mais alta à mais baixa):

1. A exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A exibição tem um nó irmão que corresponde ao nome do canal referenciado
1. O local pai da exibição tem um nó filho que corresponde ao nome do canal referenciado
1. O local principal da exibição tem um nó filho que corresponde ao nome do canal referenciado

E assim por diante, até atingir a pasta de localizações e parar lá no momento (de modo que não seja possível fazer referência a um canal que estaria na pasta de canais, por exemplo, apenas canais na subárvore de localizações).

## Registro do dispositivo {#device-registration}

### 1. Se eu descobrir endpoints como solicitações de integração e registro de dispositivos, posso criar scripts para um grande número de dispositivos e registrar esses dispositivos. Além de bloquear isso em uma ramificação Wi-Fi, é possível proteger essas solicitações? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Atualmente, o registro só é possível na instância do autor. Embora o serviço de registro não esteja autenticado, ele só criará um dispositivo pendente no AEM e não registrará o dispositivo ou atribuirá qualquer exibição.

Para registrar um dispositivo (o que significa criar um usuário para o dispositivo no AEM), ainda é necessário autenticar para AEM e, no momento, seguir manualmente o assistente de registro para concluir o registro. Teoricamente, um usuário mal-intencionado pode criar vários dispositivos pendentes, mas não pode registrar nenhum sem um logon AEM.

### 2. Existe uma maneira de transformar solicitações HTTP GET em HTTP POST com alguma forma de autenticação? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

A solicitação de registro é uma solicitação de POST.

É recomendável obter a ID do dispositivo da sessão em vez de passá-la como parâmetro. Isso limparia os logs do servidor, o cache do navegador e assim por diante. No momento, não é um problema de segurança. Observe que a GET semântica é usada quando não há alteração de estado no servidor e a POST é usada quando há uma alteração de estado.

### 3. Existe uma maneira de recusar uma solicitação de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Não é possível recusar as solicitações de registro. Em vez disso, as solicitações de registro devem expirar após um tempo limite configurado no [Adobe Experience Manager Web Console](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl). Por padrão, esse valor é definido como um dia e armazenado em um cache de memória.

## Relatórios de monitoramento e integridade de dispositivo {#device-monitoring-and-health-reports}

### 1. Como soluciono o problema, se o meu reprodutor AEM Screens exibir tela em branco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Verifique as seguintes possibilidades para solucionar o problema de tela em branco:

* O AEM não pode enviar o conteúdo offline
* O canal não tem conteúdo
* Nenhum dos ativos está programado para ser exibido no momento atual

### 2. O que devo fazer se o reprodutor do AEM Screens não conseguir se registrar e seu estado for exibido como Falha? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Você precisa ativar o Filtro de referenciador do Apache Sling Permitir vazio. Isso é necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor AEM Screens.

1. Navegue até **Configuração do Console Web do Adobe Experience Manager**
1. Marque a opção **allow.empty**.
1. Clique em **Salvar**.

### 3. Como solucionar problemas se, durante o registro de um reprodutor do AEM Screens, o dispositivo mostrar FAILURE e os registros do console exibirem o erro ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Esse problema pode ocorrer se o reprodutor não conseguir localizar o DNS do AEM Screens Server. Tente usar o endereço IP para se conectar. Para obter o IP do servidor, use: *arp &lt;server_dns_name>*.

### 4. O AMS recomenda a implementação de um Android Watchdog em todos os dispositivos? O plug-in Watchdog (Cordova) é incluído como parte do APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Um observatório Android de várias plataformas usando APIs puras do Android já faz parte do aplicativo. Nenhum software adicional é necessário, mas dependendo do dispositivo usado, talvez seja necessário renunciar ao aplicativo para obter privilégios de sistema para um ciclo completo de energia (api do Powermanager). Se não for demitido usando as teclas do fabricante, o aplicativo será fechado e reiniciado, mas não o ciclo de alimentação.

Para obter mais informações sobre como implementar o Android Player, consulte [**Implementação do Android Player**](implementing-android-player.md).

### 5. Quais ferramentas de monitoramento remoto e alerta (software) de terceiros o Adobe/AMS recomenda para monitorar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependendo do que você deseja para fora do monitoramento e dos alertas, um novo recurso do serviço de Notificações da AEM Screens notifica você se um dispositivo não tiver pingado por algum tempo. As ferramentas de terceiros dependerão do seu sistema operacional (SO), de seus recursos e das necessidades específicas do cliente.

Para obter mais informações sobre onde você pode monitorar a atividade do dispositivo, consulte [**AEM Screens Notifications Service**](screens-notifications-service.md).

## Player do AEM Screens {#aem-screens-player}

### 1. Como instalar o player do ChromeOS como plug-in do navegador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

O player do ChromeOS pode ser instalado como plug-in do navegador Chrome no modo de desenvolvedor sem precisar do dispositivo do player do Chrome. Para instalação, siga as etapas abaixo:

1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Player mais recente do Chrome.
1. Descompacte-o e salve-o no disco.
1. Abra o navegador Chrome e selecione **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
1. Ative o **Modo de desenvolvedor** a partir do canto superior direito.
1. Clique em **Carregar descompactado** do canto superior esquerdo e carregue o Chrome Player descompactado.
1. Verifique o plug-in **AEM Screens Chrome Player** se estiver disponível na lista de extensões.
1. Abra uma nova guia e clique no ícone **Apps** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
1. Clique no plug-in **AEM Screens** para iniciar o Chrome Player. Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.

### 2. Como solucionar problemas se o reprodutor do Screens não conseguir se autenticar por meio da instância de publicação com o manipulador de erros personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Quando o reprodutor do AEM Screens é iniciado, ele faz uma solicitação para ***/content/screens/svc.ping.json***, quando o reprodutor recebe um erro 404. O reprodutor inicia uma solicitação de autenticação para autenticação na instância de publicação. Se houver um manipulador de erro personalizado na instância de publicação, retorne o código de status 404 para usuário anônimo em ***/content/screens/svc.ping.json***.

### 3. Como definir a tela do dispositivo para permanecer em um Android Player? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga as etapas abaixo para ativar e ativar a opção Permanecer ativo em qualquer player Android:

1. Navegue até as configurações do player do Android —> **Sobre**
1. Toque 7 vezes no número de compilação para ativar **Opções do Desenvolvedor** em **Configurações**
1. Navegue até **Opções do Desenvolvedor**
1. Ativar **Estar Awake**

### 4. Como ativar o modo de janela para o Windows player?{#enable-player}

Não há um modo de janela no Windows Player. É sempre o modo de tela cheia.

### 5. Como solucionar problemas se um reprodutor do AEM Screens enviar solicitações de logon continuamente?{#requests-login}

Siga as etapas abaixo para solucionar problemas de um reprodutor do AEM Screens que envia continuamente solicitações para `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. Quando o reprodutor do AEM Screens é iniciado, ele solicita `/content/screens/svc.json`. Quando o reprodutor recebe um código de status 404 na resposta, ele inicia uma solicitação de autenticação usando `/libs/granite/core/content/login.validate/j_security_check` na instância *publish*. Se houver um manipulador de erro personalizado na instância *publish*, retorne o código de status 404 para usuário anônimo em `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Verifique se a configuração do dispatcher permite essas solicitações no `/filters`.

   Consulte [Configuração de filtros do Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters) para obter mais detalhes.

1. Verifique se as regras de reescrita do dispatcher estão reescrevendo qualquer um dos caminhos de tela para um caminho diferente.

1. Verifique se você tem regras `/etc/map` na instância *author* ou *publish* e os caminhos de tela são correspondidos a `sling:match` e redirecionados internamente para um caminho diferente. Resolver o url exato em `/system/console/jcrresolver` ajuda a identificar se a instância *publish* está reescrevendo esses URLs para qualquer outro caminho.

1. Verifique se a configuração da Fábrica do Resolvedor de Recursos do Apache Sling está causando regravações internas.

### 6. Como obter os detalhes do monitor e do dispositivo da API do reprodutor?

Você pode obter os detalhes da exibição e do dispositivo por meio de:

* **uma API JS interna**
* **um armazenamento** do ContextHub: Três armazenamentos do ContextHub são definidos no  `/libs/screens/clientlibs/contexthub` para expor canais, dispositivos e informações de exibição.

   Siga as etapas abaixo para usar esses valores de armazenamento do ContentHub:

   * Edite as propriedades do canal e defina o caminho do ContextHub na guia de personalização como o valor (como mencionado acima)
   * No JS do canal, você pode usar:

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## Dicas gerais de solução de problemas {#general-troubleshooting-tips}

### 1. Como desativar o Livefyre para evitar erros de telas A/P? {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Para desativar o Livefyre para evitar erros de log:

1. ***Desative o pacote Livefyre:***

   * Vá até `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * Procure pelo pacote AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`
   * Clique em **Parar**

1. ***Desative o Livefyre poler:***

   * No CRXDE Lite, navegue até `/etc/importers/polling/livefyre-poller/jcr:content`
   * Adicionar uma nova propriedade *enabled* tipo *Boolean*
   * Defina **propriedade ativada** para **false**

### 2. Como adicionar informações sobre o índice Oak? {#add-oak-index-info}

O AEM Screens cria definições de índice para as consultas usadas pelo produto.
Se houver *AVISOs de passagem de consulta* no `error.log`, crie um índice personalizado para sua consulta. Consulte [Configuração de Índices](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#configuring-the-indexes) para obter mais detalhes.

Também é possível consultar um recurso adicional em [Documentação do Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


