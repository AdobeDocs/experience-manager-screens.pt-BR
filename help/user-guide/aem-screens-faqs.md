---
title: Perguntas frequentes sobre o AEM Screens
description: Leia respostas das perguntas frequentes relacionadas a um projeto do AEM Screens.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 0%

---

# Perguntas frequentes sobre o AEM Screens {#aem-screens-faqs}

Este tópico fornece respostas para as perguntas frequentes relacionadas a um projeto do AEM Screens.

## Problema de tela em branco {#blank-screen}

>[!NOTE]
>As verificações obrigatórias listadas que o suporte principal ou o suporte do cliente deve tentar antes de levantar um problema.

### 1. Quais devem ser as etapas da solução de problemas de primeiros socorros para qualquer cliente que esteja diante de uma tela preta ou sem reprodução? {#troubleshooting-blank-screen}

* Verifique se a visualização do canal está funcionando.
* Verificar se a visualização está funcionando
* Tente registrar o reprodutor como uma extensão de navegador no sistema para a mesma exibição e verifique se ele está funcionando.
* Com o reprodutor em execução no sistema, navegue até `http://localhost:24502`. Verifique se todo o conteúdo foi baixado corretamente.
* Verifique os ativos para garantir que as representações apropriadas sejam criadas e que a representação correta esteja sendo reproduzida.
* Verifique se há conteúdo agendado e se os horários estão corretos. Verifique se a hora configurada no reprodutor está correta.
* O Inspect registra o console do reprodutor e verifica se há erros. Clique com o botão direito do mouse e inspecione para ver os logs do console. Se estiver usando o Windows Player, pressione `CTRL + ALT +I` para exibir o dev console e ver os logs.

### 2. Como resolver problemas de tela cinza no AEM Screens ao criar um canal ou agendamento padrão?

Para evitar as telas em branco ou cinza no campo, crie um canal global ou agendamento padrão, atribuído a cada exibição com menos prioridade 1. Caso algo dê errado com as atualizações de conteúdo porque os reprodutores já têm esse conteúdo em cache no disco. Ele deve ser reproduzido perfeitamente e evitar as telas cinzas.

Todo o restante do conteúdo, como canais ou agendamentos, tem prioridade maior que 1, de modo que o outro conteúdo tem prioridade e o conteúdo global do canal ou agendamento (com prioridade 1) é reproduzido apenas como uma opção de fallback.

## Gerenciamento de canal {#channel-management}

### 1. Qual é a diferença entre um canal online e um offline? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Um ***Canal online*** mostra o conteúdo atualizado no ambiente em tempo real, enquanto uma ***Canal offline*** mostra o conteúdo em cache.

### 2. Como faço para criar um canal online? {#how-do-i-make-a-channel-online}

Clique no canal e navegue até as propriedades do canal na barra de ações. Marcar **Modo de desenvolvedor (forçar canal a ficar online)** em **Canal** para tornar o canal online.

### 3. Qual é o uso do campo Função do canal? {#what-is-the-use-of-the-channel-role-field}

A Função do canal é a abstração do canal real que é executada para que o autor possa se concentrar diretamente na experiência genérica. Pense nele como um tipo de tag que identifica exclusivamente o canal em seu contexto (exibição ou programação).

### 4. Como ocorre a resolução real do canal? {#how-does-actual-channel-resolution-happen}

Para *referências estáticas*, a resolução apenas segue o caminho especificado.

Para *referências dinâmicas*, a resolução ocorre quando o canal é atribuído à exibição (não ao agendamento). O caminho de exibição se torna o contexto do canal e a resolução ocorre da seguinte maneira (prioridade mais alta a mais baixa):

1. A exibição tem um nó filho que corresponde ao nome do canal referenciado
1. A exibição tem um nó irmão que corresponde ao nome do canal referenciado
1. O local principal da exibição tem um nó secundário que corresponde ao nome do canal referenciado
1. O local de exibição principal tem um nó secundário que corresponde ao nome do canal referenciado

E assim por diante, até chegar à pasta de locais. Pare aí no momento (para que você não possa referenciar um canal que estaria na pasta de canais por exemplo, somente canais na subárvore de local).

### 5. Como definir a configuração personalizada clientlib offline no canal do AEM Screens?

Ao usar um código personalizado criado no lado do cliente `clientlib` em um canal do AEM Screens, as seguintes etapas são necessárias. As etapas garantem que a variável `clientlib` os arquivos foram carregados com sucesso no canal (`manifest.json`) e contém o caminho do `clientlib`.

Siga as etapas abaixo no editor de canal:

1. Clique em um canal e em **Editar** na barra de ações.
1. Clique no componente ao qual deseja adicionar o personalizado `clientlib`.
1. Clique no botão de configuração (a chave inglesa ).
1. Navegue até a **Configuração offline** e adicione o caminho à clientlib personalizada em **Bibliotecas do cliente**.

## Registro do dispositivo {#device-registration}

### 1. Se eu descobrir endpoints como solicitações de integração e registro de dispositivos, poderei criar scripts para vários dispositivos e registrá-los. Além de bloqueá-lo em uma ramificação Wi-Fi, é possível proteger essas solicitações? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Atualmente, o registro só é possível na instância do autor. Embora o serviço de registro não seja autenticado, ele cria apenas um dispositivo pendente no AEM e não registra o dispositivo nem atribui nenhuma exibição.

Para registrar um dispositivo (criando um usuário para o dispositivo no AEM), autentique no AEM e siga manualmente o assistente de registro para concluir o registro. Teoricamente, um usuário mal-intencionado pode criar vários dispositivos pendentes, mas não pode registrar nenhum se não tiver um logon AEM.

### 2. Há alguma maneira de transformar solicitações HTTP GET em HTTP POST com alguma forma de autenticação? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

A solicitação de registro é uma solicitação POST.

É recomendável obter a ID do dispositivo da sessão em vez de ser passada como parâmetro. Isso limparia os logs do servidor, o cache do navegador e assim por diante. Não é um problema de segurança. Semanticamente. O GET é usado quando não há alteração de estado no servidor e o POST é usado quando há uma alteração de estado.

### 3. Há alguma maneira de recusar uma solicitação de registro de dispositivo? {#is-there-a-way-to-decline-a-device-registration-request}

Você não pode recusar as solicitações de registro. Em vez disso, as solicitações de registro devem expirar após um tempo limite configurado no `Adobe Experience Manager Web Console`. Por padrão, esse valor é definido como um dia e armazenado em um cache de memória.

## Relatórios de Integridade e Monitoramento de Dispositivos {#device-monitoring-and-health-reports}

### 1. Como solucionar problemas se o AEM Screens Player mostrar uma tela em branco?

Verifique as seguintes possibilidades para solucionar o problema de tela em branco:

* O AEM não consegue enviar o conteúdo off-line
* O canal não tem conteúdo
* Nenhum dos ativos está agendado para exibição no momento atual

### 2. O que devo fazer se o AEM Screens Player não puder se registrar e seu estado for exibido como Failure?

Ative a permissão Vazia de filtro de referência do Apache Sling. Necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor do AEM Screens.

1. Navegue até **Configuração do console da Web do Adobe Experience Manager**
1. Verifique a **allow.empty** opção.
1. Clique em **Salvar**.

### 3. Como solucionar problemas se, ao registrar um AEM Screens Player, o dispositivo mostrar FAILURE e os registros do console exibirem um erro ENAME_NOT_FOUND?

Esse problema pode ocorrer se o reprodutor não conseguir encontrar o DNS do servidor do AEM Screens. Tente usar o endereço IP para se conectar. Para obter o IP do servidor, use: *arp &lt;server_dns_name>*.

### 4. O AMS recomenda implementar um Watchdog Android™ em todos os dispositivos? O plug-in Watchdog (Cordova) está incluído como parte do APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Um cão de guarda do Android™ em várias plataformas usando APIs puras do Android™ já faz parte do aplicativo. Nenhum software adicional é necessário. No entanto, dependendo do dispositivo usado, você pode renunciar ao apk para obter privilégios de sistema para um ciclo de alimentação completo (`Powermanager` api), se necessário. Se ele não for reenviado usando as chaves do fabricante, ele encerrará e reiniciará o aplicativo, mas não desligará e desligará a energia.

Para obter mais informações sobre como implementar o Android™ Player, consulte [**Implementação do Android™ Player**](implementing-android-player.md).

### 5. Quais ferramentas (software) de monitoramento e alerta remotos de terceiros o Adobe/AMS recomenda para monitorar cada dispositivo? {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Dependendo do que você desejar do monitoramento e dos alertas, um novo recurso do serviço de Notificações da AEM Screens notifica se um dispositivo não executou ping por algum tempo. As ferramentas de terceiros dependem do sistema operacional (SO), dos recursos e das necessidades específicas do cliente.

Para obter mais informações sobre onde é possível monitorar a atividade do dispositivo, consulte [**Serviço de notificações AEM Scree ns**](screens-notifications-service.md).

## Player do AEM Screens

### 1. Como instalar o ChromeOS player como plug-in do navegador Chrome? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

O ChromeOS player pode ser instalado como um plug-in do navegador Chrome no modo de desenvolvedor, sem exigir um dispositivo Chrome Player real. Para instalação, siga as etapas abaixo:

1. Clique em [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
1. Descompacte-o e salve-o no disco.
1. Abra o navegador Chrome e clique em **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
1. Ligue o **Modo de desenvolvedor** no canto superior direito.
1. Clique em **Carregar desempacotado** no canto superior esquerdo e carregue o Chrome Player descompactado.
1. Se disponível na lista de extensões, verifique a **AEM Screens Chrome Player** plug-in.
1. Abra uma nova guia e clique no link **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
1. Clique em **AEM Screens** Plug-in. Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **Esc** para sair do modo de tela cheia.

### 2. Como solucionar problemas se o reprodutor do Screens não puder se autenticar por meio da instância de publicação com um manipulador de erros personalizado?

Quando o AEM Screens Player é iniciado, ele faz uma solicitação para ***/content/screens/svc.ping.json***, quando o reprodutor recebe um erro 404. O reprodutor inicia uma solicitação de autenticação para autenticar na instância de publicação. Se houver um manipulador de erros personalizado na instância de publicação, retorne o código de status 404 de um usuário anônimo em ***/content/screens/svc.ping.json***.

### 3. Como definir a tela do dispositivo permanecer em um Android™ Player? {#how-to-set-the-device-screen-stay-on-in-an-android-player}

Siga as etapas abaixo para ativar a função Permanecer acordado em qualquer player Android™:

1. Navegue até Configurações do Android™ Player > **Sobre**.
1. Toque sete vezes no número da build para poder habilitar **Opções do desenvolvedor** in **Configurações**.
1. Navegue até **Opções do desenvolvedor**.
1. Ativar **Fique Acordado**.

### 4. Como ativar o modo de janela para o Windows Player?{#enable-player}

Não há modo de janela no Windows Player. Está sempre no modo de tela cheia.

### 5. Como solucionar problemas se um AEM Screens Player envia solicitações de logon continuamente?

Siga as etapas abaixo para solucionar problemas com um AEM Screens Player que envia solicitações continuamente para o `/content/screens/svc.json` e `/libs/granite/core/content/login.validate/j_security_check`:

1. Quando o AEM Screens Player é iniciado, ele solicita que `/content/screens/svc.json`. Quando o reprodutor recebe um código de status 404 na resposta, ele inicia uma solicitação de autenticação usando `/libs/granite/core/content/login.validate/j_security_check` contra a *publicar* instância. Se houver um manipulador de erros personalizado no *publicar* exemplo, certifique-se de retornar o código de status 404 para usuário anônimo em `/content/screens/svc.json` ou `/content/screens/svc.ping.json`.

1. Verifique se a configuração do Dispatcher permite essas solicitações na variável `/filters`.

   Consulte [Configuração de filtros do Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters) para obter mais detalhes.

1. Verifique se as regras de regravação do Dispatcher estão regravando qualquer um dos caminhos da tela em um caminho diferente.

1. Verifique se você tem `/etc/map` regras sobre o *autor* ou *publicar* os caminhos de instância e telas são combinados com `sling:match` e redirecionado internamente para um caminho diferente. Resolução do url exato em `/system/console/jcrresolver` ajuda a identificar se a variável *publicar* A instância do está reescrevendo esses URLs em qualquer outro caminho.

1. Verifique se a configuração de fábrica do Apache Sling Resource Resolver está causando regravações internas.

### 6. Como obter os detalhes da exibição e do dispositivo da API do player?

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

### 1. Como desativar o Livefyre para evitar o erro do A/P Screens?

Desative o Livefyre para evitar erros de registro ao fazer o seguinte.

1. ***Desative o pacote Livefyre:***

   * Vá até `https://<host>:<port>/system/console/bundles`.
   * Procure o pacote AEM Livefyre: `com.adobe.cq.social.cq-social-livefyre`.
   * Clique em **Parar**.

1. ***Desative o poller do Livefyre:***

   * No CRXDE Lite, navegue até `/etc/importers/polling/livefyre-poller/jcr:content`.
   * Adicionar uma propriedade do *habilitado* type *Booleano*.
   * Definir **Propriedade ativada** para ser **false**.

### 2. Como adicionar informações do índice Oak? {#add-oak-index-info}

O AEM Screens cria definições de índice para as consultas usadas pelo produto.
Se houver *AVISOS de cruzamento de consulta* no `error.log`, crie um índice personalizado para o query. Consulte [Configurar os índices](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes) para obter mais detalhes.

Você também pode ver um recurso adicional em [Documentação do Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).


### 3. O que é necessário para configurar Manifestos v3? {#configure-v3}

Para ativar o Manifesto v3, faça o seguinte:

* Atualize o Dispatcher.
Consulte [Configuração do Dispatcher para Versão de Manifesto v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) para obter mais detalhes.

* Atualizar componente personalizado.
Consulte [Modelo para manipuladores personalizados](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers) para obter mais detalhes.

* Desativar ContentSync em `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

* Ativar SmartSync no `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

* Editar `channel/experience fragment/page components`.

* Navegue até a **Configuração offline** guia.

* Enter `clientlibs `e pastas para arquivos estáticos que devem ser adicionados ao manifesto.

### 4. O que você deve fazer se, após o pacote screens-cloud-ams-pkg-0.0.20, screens-cloud-ams-pkg-0.0.16 e os pacotes principais de telas estiverem instalados, mas não ativos?

Instale uma versão mínima do AEM 6.5 Feature Pack 8 para que o conector AMS funcione. Consulte [Disponibilidade](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) assim, você pode obter a versão mínima do Pacote de recursos do AEM Screens.

### 5. Como configurar o serviço Externalizador de link CQ no Screens?

O serviço é usado para definir o nome de host público para as instâncias de autor e publicação, e os valores são usados para atualizar os URLs do servidor do dispositivo e também para o direcionamento do ContextHub.

O serviço Externalizador de link CQ no Screens pode ser configurado da seguinte maneira:

1. Navegue até `http://localhost:4502/system/console/configMgr`
1. Day CQ Link Externalizer
1. Altere o nome do host para o `author/publish` entradas conforme necessário