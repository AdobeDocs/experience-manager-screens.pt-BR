---
title: Perguntas frequentes sobre o AEM Screens
description: Leia respostas das perguntas frequentes relacionadas a um projeto do AEM Screens.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
TQID: https://experienceleague.adobe.com/7M-3FuDthc-4z4OSHp49eL7QHWvt1acjKfA7C1BGWy0
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 2299
ht-degree: 1%

---

# Perguntas frequentes sobre o AEM Screens {#aem-screens-faqs}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Este tópico fornece respostas para as perguntas frequentes relacionadas a um projeto do AEM Screens.

## Problema de tela em branco {#blank-screen}

>[!NOTE]
>As verificações obrigatórias listadas que o suporte principal ou o suporte do cliente deve tentar antes de levantar um problema.

### &#x200B;1. Quais devem ser as etapas da solução de problemas de primeiros socorros para qualquer cliente que esteja diante de uma tela preta ou que não esteja reproduzindo conteúdo? {#troubleshooting-blank-screen}

* Verifique se a visualização do canal está funcionando.
* Verificar se a visualização está funcionando
* Tente registrar o reprodutor como uma extensão de navegador no sistema para a mesma exibição e verifique se ele está funcionando.
* Com o reprodutor em execução no seu sistema, navegue até `http://localhost:24502`. Verifique se todo o conteúdo foi baixado corretamente.
* Verifique os ativos para garantir que as representações apropriadas sejam criadas e que a representação correta esteja sendo reproduzida.
* Verifique se há conteúdo agendado e se os horários estão corretos. Verifique se a hora configurada no reprodutor está correta.
* Inspecione os registros do console do reprodutor e verifique se há erros. Clique com o botão direito do mouse e inspecione para ver os logs do console. Se você estiver usando o Windows Player, pressione `CTRL + ALT +I` para exibir os arquivos de log e abrir o console de desenvolvimento.

### &#x200B;2. Como resolver problemas de tela cinza no AEM Screens ao criar um canal ou agendamento padrão?

Para evitar as telas em branco ou cinza no campo, crie um canal global ou agendamento padrão, atribuído a cada exibição com menos prioridade 1. Caso algo dê errado com as atualizações de conteúdo porque os reprodutores já têm esse conteúdo em cache no disco. Ele deve ser reproduzido perfeitamente e evitar as telas cinzas.

Todo o restante do conteúdo, como canais ou agendamentos, tem prioridade maior que 1, de modo que o outro conteúdo tem prioridade e o conteúdo global do canal ou agendamento (com prioridade 1) é reproduzido apenas como uma opção de fallback.

## Gerenciamento de canal {#channel-management}

### &#x200B;1. Qual é a diferença entre um canal online e um canal offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Um ***Canal Online*** mostra o conteúdo atualizado no ambiente em tempo real, enquanto um ***Canal Offline*** mostra o conteúdo em cache.

### &#x200B;2. Como faço para criar um canal online? {#how-do-i-make-a-channel-online}

Clique no canal e navegue até as propriedades do canal na barra de ações. Verifique o **Modo de desenvolvedor (forçar canal a ficar online)** na guia **Canal** para colocar o canal online.

### &#x200B;3. Qual é o uso do campo Função do canal? {#what-is-the-use-of-the-channel-role-field}

A Função do canal é a abstração do canal real que é executada para que o autor possa se concentrar diretamente na experiência genérica. Pense nele como um tipo de tag que identifica exclusivamente o canal em seu contexto (exibição ou programação).

### &#x200B;4. Como ocorre a resolução real do canal? {#how-does-actual-channel-resolution-happen}

Para *referências estáticas*, a resolução apenas segue o caminho especificado.

Para *referências dinâmicas*, a resolução ocorre assim que o canal é atribuído à exibição (não o agendamento). O caminho de exibição se torna o contexto do canal e a resolução ocorre da seguinte maneira (prioridade mais alta a mais baixa):

1. A exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A exibição tem um nó irmão que corresponde ao nome do canal referenciado
1. O local principal da exibição tem um nó secundário que corresponde ao nome do canal referenciado
1. O local de exibição principal tem um nó secundário que corresponde ao nome do canal referenciado

E assim por diante, até chegar à pasta de locais. Pare aí no momento (para que você não possa referenciar um canal que estaria na pasta de canais por exemplo, somente canais na subárvore de local).

### &#x200B;5. Como definir a configuração personalizada clientlib offline no canal do AEM Screens?

Ao usar um código personalizado de cliente `clientlib` em um canal do AEM Screens, as etapas a seguir são necessárias. As etapas garantem que os arquivos `clientlib` sejam carregados com êxito no canal (`manifest.json`) e contenham o caminho do `clientlib`.

Siga as etapas abaixo no editor de canal:

1. Clique em um canal e em **Editar** na barra de ações.
1. Clique no componente ao qual você deseja adicionar o `clientlib` personalizado.
1. Clique no botão de configuração (a chave inglesa ).
1. Navegue até a guia **Configuração offline** e adicione o caminho à clientlib personalizada em **Bibliotecas do lado do cliente**.

## Registro do dispositivo {#device-registration}

### &#x200B;1. Se eu descobrir pontos de extremidade, como solicitações de integração e registro de dispositivos, poderei criar scripts para vários dispositivos e registrá-los. Além de bloqueá-lo em uma ramificação Wi-Fi, é possível proteger essas solicitações? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Atualmente, o registro só é possível na instância do autor. Embora o serviço de registro não seja autenticado, ele só cria um dispositivo pendente no AEM e não registra o dispositivo ou atribui nenhuma exibição.

Para registrar um dispositivo (criando um usuário para o dispositivo no AEM), autentique no AEM e siga manualmente o assistente de registro para concluir o registro. Teoricamente, um usuário mal-intencionado pode criar vários dispositivos pendentes, mas não pode registrar nenhum se não tiver um logon no AEM.

### &#x200B;2. Há uma maneira de transformar solicitações HTTP GET em HTTP POST com alguma forma de autenticação? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

A solicitação de registro é uma solicitação POST.

É recomendável obter a ID do dispositivo da sessão em vez de ser passada como parâmetro. Isso limparia os logs do servidor, o cache do navegador e assim por diante. Não é um problema de segurança. Semanticamente. GET é usado quando não há alteração de estado no servidor e POST é usado quando há uma alteração de estado.

### &#x200B;3. Há uma maneira de recusar uma solicitação de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Você não pode recusar as solicitações de registro. Em vez disso, as solicitações de registro devem expirar após um tempo limite configurado em `Adobe Experience Manager Web Console`. Por padrão, esse valor é definido como um dia e armazenado em um cache de memória.

## Relatórios de Integridade e Monitoramento de Dispositivos {#device-monitoring-and-health-reports}

### &#x200B;1. Como solucionar problemas se o AEM Screens Player mostrar uma tela em branco?

Verifique as seguintes possibilidades para solucionar o problema de tela em branco:

* O AEM não pode enviar o conteúdo offline
* O canal não tem conteúdo
* Nenhum dos ativos está agendado para exibição no momento atual

### &#x200B;2. O que devo fazer se o AEM Screens Player não puder se registrar e seu estado for exibido como Failure?

Ative a permissão Vazia de filtro de referência do Apache Sling. Necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor do AEM Screens.

1. Navegue até **Configuração do Adobe Experience Manager Web Console**
1. Verifique a opção **allow.empty**.
1. Clique em **Salvar**.

### &#x200B;3. Como solucionar problemas se, durante o registro de um AEM Screens Player, o dispositivo mostrar FAILURE e os registros do console exibirem um erro ENAME_NOT_FOUND?

Esse problema pode ocorrer se o reprodutor não conseguir encontrar o DNS do servidor do AEM Screens. Tente usar o endereço IP para se conectar. Para obter o IP do servidor, use: *arp &lt;nome_dns_servidor>*.

### &#x200B;4. O AMS recomenda implementar um Watchdog Android™ em todos os dispositivos? O plug-in Watchdog (Cordova) está incluído como parte do APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Um vigilante de várias plataformas da Android™ usando APIs puras da Android™ já faz parte do aplicativo. Nenhum software adicional é necessário. No entanto, dependendo do dispositivo usado, você pode renunciar ao apk para obter privilégios de sistema para um ciclo de alimentação completo (`Powermanager` api), se necessário. Se ele não for reenviado usando as chaves do fabricante, ele encerrará e reiniciará o aplicativo, mas não desligará e desligará a energia.

Para obter mais informações sobre como implementar o Android™ Player, consulte [**Implementação do Android™ Player**](implementing-android-player.md).

### &#x200B;5. Quais ferramentas (software) remotas de monitoramento e alerta de terceiros a Adobe/AMS recomenda para monitorar cada dispositivo? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependendo do que você desejar do monitoramento e dos alertas, um novo recurso do serviço de Notificações da AEM Screens notifica se um dispositivo não executou ping por algum tempo. As ferramentas de terceiros dependem do sistema operacional (SO), dos recursos e das necessidades específicas do cliente.

Para obter mais informações sobre onde é possível monitorar a atividade do dispositivo, consulte [**Serviço de Notificações do AEM Screens**](screens-notifications-service.md).

## Player do AEM Screens

### &#x200B;1. Como instalar o ChromeOS player como plug-in do navegador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

O ChromeOS player pode ser instalado como um plug-in do navegador Chrome no modo de desenvolvedor, sem exigir um dispositivo Chrome Player real. Para instalação, siga as etapas abaixo:

1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
1. Descompacte-o e salve-o no disco.
1. Abra o navegador Chrome e clique em **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
1. Ative o **Modo de desenvolvedor** no canto superior direito.
1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
1. Se estiver disponível na lista de extensões, verifique o plug-in **AEM Screens Chrome Player**.
1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
1. Clique no Plug-in **AEM Screens**. Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **Esc** para sair do modo de tela cheia.

### &#x200B;2. Como solucionar problemas se o Screens player não puder se autenticar por meio da instância de publicação com um manipulador de erros personalizado?

Quando o AEM Screens Player é iniciado, ele faz uma solicitação para ***/content/screens/svc.ping.json***, quando o player recebe um erro 404. O reprodutor inicia uma solicitação de autenticação para autenticar na instância de publicação. Se houver um manipulador de erros personalizado na instância de publicação, retorne o código de status 404 para um usuário anônimo em ***/content/screens/svc.ping.json***.

### &#x200B;3. Como definir a tela do dispositivo para permanecer ativado em um Android™ Player? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga as etapas abaixo para ativar a opção Permanecer acordado em qualquer Android™ player:

1. Navegue até Configurações do Android™ player > **Sobre**.
1. Toque sete vezes no número da compilação para habilitar as **Opções do Desenvolvedor** em **Configurações**.
1. Navegue até **Opções do desenvolvedor**.
1. Habilite **Permanecer Acordado**.

### &#x200B;4. Como ativar o modo de janela para o Windows Player?{#enable-player}

Não há modo de janela no Windows Player. Está sempre no modo de tela cheia.

### &#x200B;5. Como solucionar problemas se um AEM Screens Player envia solicitações de logon continuamente?

Siga as etapas abaixo para solucionar problemas com um AEM Screens Player que envia continuamente solicitações para `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. Quando o AEM Screens Player é iniciado, ele solicita `/content/screens/svc.json`. Quando o reprodutor recebe um código de status 404 na resposta, ele inicia uma solicitação de autenticação usando `/libs/granite/core/content/login.validate/j_security_check` na instância *publish*. Se houver um manipulador de erros personalizado na instância de *publicação*, retorne o código de status 404 para o usuário anônimo em `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Verifique se a configuração do Dispatcher permite essas solicitações no `/filters`.

   Consulte [Configurando Filtros do Screens](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) para obter mais detalhes.

1. Verifique se as regras de regravação do Dispatcher estão regravando qualquer um dos caminhos da tela em um caminho diferente.

1. Verifique se você tem `/etc/map` regras na instância de *autor* ou *publicação* e se os caminhos de telas correspondem a `sling:match` e são redirecionados internamente para um caminho diferente. Resolver a url exata em `/system/console/jcrresolver` ajuda a identificar se a instância *publish* está regravando essas URLs para qualquer outro caminho.

1. Verifique se a configuração de fábrica do Apache Sling Resource Resolver está causando regravações internas.

### &#x200B;6. Como obter os detalhes da exibição e do dispositivo da API do player?

Você pode obter os detalhes da exibição e do dispositivo por meio de:

* **uma API JS interna**
* **um armazenamento do ContextHub**: três armazenamentos do ContextHub são definidos em `/libs/screens/clientlibs/contexthub` para expor canais, dispositivos e informações.

  Siga as etapas abaixo para usar esses valores de armazenamento do ContentHub:

   * Edite as propriedades do canal e defina o caminho do ContextHub na guia de personalização para o valor (como mencionado acima)
   * No JS do canal, é possível usar:

     ```shell
        ContextHub.getStore('screens-device');
        ContextHub.getStore('screens-display');
        ContextHub.getStore('screens-channels');
     ```

## Dicas gerais de solução de problemas {#general-troubleshooting-tips}

### &#x200B;1. Como desativar o Livefyre para evitar um erro de Screens A/P?

Desative o Livefyre para evitar erros de registro ao fazer o seguinte.

1. ***Desabilitar conjunto do Livefyre:***

   * Vá até `https://<host>:<port>/system/console/bundles`.
   * Procure o pacote AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`.
   * Clique em **Parar**.

1. ***Desabilitar o Poller do Livefyre:***

   * No CRXDE Lite, navegue até `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Adicione uma propriedade *enabled* tipo *Boolean*.
   * Defina a propriedade **Enabled** como **false**.

### &#x200B;2. Como adicionar informações de índice do Oak? {#add-oak-index-info}

O AEM Screens cria definições de índice para as consultas usadas pelo produto.Se houver *AVISOS de Travessia de Consulta* em `error.log`, crie um índice personalizado para sua consulta. Consulte [Configurando os Índices](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) para obter mais detalhes.

Você também pode ver um recurso adicional em [Documentação do Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### &#x200B;3. O que é necessário para configurar os Manifestos v3? {#configure-v3}

Para ativar o Manifesto v3, faça o seguinte:

* Atualize o Dispatcher.Consulte [Configuração do Dispatcher para a Versão de Manifesto v3](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) para obter mais detalhes.

* Atualizar componente personalizado.Consulte [Modelo para manipuladores personalizados](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) para obter mais detalhes.

* Desabilitar ContentSync em `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Habilitar SmartSync em `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Editar `channel/experience fragment/page components`.

* Navegue até a guia **Configuração Offline**.

* Insira `clientlibs ` e pastas para arquivos estáticos que devem ser adicionados ao manifesto.

### &#x200B;4. O que você deve fazer se, após o pacote screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 e os pacotes principais do screens estiverem instalados, mas não ativos?

Instale uma versão mínima do AEM 6.5 Feature Pack 8 para que o conector AMS funcione. Consulte [Disponibilidade](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) para obter a versão mínima do Pacote de Recursos do AEM Screens.

### &#x200B;5. Como configurar o serviço CQ Link Externalizer no Screens?

O serviço é usado para definir o nome de host público para as instâncias de autor e publicação, e os valores são usados para atualizar os URLs do servidor do dispositivo e também para o direcionamento do ContextHub.

O serviço Externalizador de links CQ no Screens pode ser configurado da seguinte maneira:

1. Navegue até `http://localhost:4502/system/console/configMgr`
1. Day CQ Link Externalizer
1. Altere o nome do host para as `author/publish` entradas conforme necessário
