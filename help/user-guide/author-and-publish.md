---
title: Configuração de instâncias de Autor e Publish no AEM Screens
description: Saiba como configurar uma instância do Autor e uma instância do Publish para o AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# Configuração de instâncias de Autor e Publish no AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página destaca os seguintes tópicos:

* **Configurando instâncias do Autor e do Publish**
* **Configurando a Topologia do Publish**
* **Gerenciando Publicação: Entregando Atualizações de Conteúdo do Autor para o Publish para o Dispositivo**

## Pré-requisitos {#prerequisites}

Antes de começar a usar servidores do Author e do Publish, você deve ter conhecimento prévio sobre:

* **Topologia do AEM**
* **Criando e gerenciando o projeto do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.4 Screens Feature Pack 2. Para obter acesso a este Feature Pack, entre em contato com o Suporte da Adobe e solicite acesso. Depois de obter permissão, você pode baixá-lo do Compartilhamento de pacotes.

>[!IMPORTANT]
>
>Se quiser usar mais de uma instância do Publish com o Dispatcher, atualize o Dispatcher. Consulte [Habilitando Sessões Fixas](dispatcher-configurations-aem-screens.md#enable-sticky-session).

## Configuração de instâncias de Autor e Publish {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para saber mais sobre a visão geral da arquitetura do Autor e do Publish e como o conteúdo é criado em uma instância do Autor AEM e depois replicado para várias instâncias do Publish, consulte [Visão geral da arquitetura do Autor e do Publish](author-publish-architecture-overview.md).

A seção a seguir explica como configurar agentes de replicação na topologia Author e Publish.

Você pode configurar um exemplo simples, em que você hospeda um Autor e duas instâncias do Publish:

* Autor > localhost:4502
* Publish 1 (pub1) > localhost:4503
* Publish 2 (pub2) > localhost:4504

## Configuração dos agentes de replicação no autor {#setting-replication-agents}

Para criar agentes de replicação, saiba como criar um agente de replicação padrão.

Há três agentes de replicação necessários para o Screens:

1. **Agente de Replicação Padrão &#x200B;***(especificado como&#x200B;*** Agente de Replicação Padrão**)
1. **Agente de replicação da Screens**
1. **Agente de Replicação Reversa**

### Etapa 1: Criação de um Agente de Replicação Default {#step-creating-a-default-replication-agent}

Siga as etapas abaixo para criar um agente de replicação padrão:

1. Navegue até sua instância do AEM > ícone de martelo > **Operações** > **Configuração**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Clique em **Replicação** na árvore de navegação esquerda.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Clique nos **Agentes no Autor** da pasta **Replicação** e clique em **Novo** para criar um novo agente de replicação padrão.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Insira o **Título** e o **Nome** para criar o agente de replicação e clique em **Criar**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Clique com o botão direito do mouse no agente de replicação e clique em **Abrir** para editar as configurações.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Clique em **Editar**.

1. Na caixa de diálogo **Configurações do Agente**, insira os detalhes.

   >[!NOTE]
   >
   >O usuário deve marcar **Habilitado** para habilitar o agente de replicação. Marque esta opção nos agentes padrão, Screens e de replicação reversa.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navegue até a guia **Transporte** e insira o **URI**, **Usuário** e **Senha**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Você também pode copiar e renomear um agente de replicação padrão existente.


#### Criação de agentes de replicação padrão {#creating-standard-replication-agents}

1. Crie um agente de replicação padrão para pub1 (um agente padrão pronto para uso já deve estar configurado). Por exemplo, *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Crie um agente de replicação padrão para pub2. Você pode copiar o agente de replicação para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte. Por exemplo, *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Criação de agentes de replicação do Screens {#creating-screens-replication-agents}

1. Crie um agente de replicação AEM Screens para pub1. Pronto para uso, há um agente de replicação Screens nomeado que aponta para a porta 4503. Ative-o.
1. Crie um agente de replicação AEM Screens para pub2. Copie o agente de replicação do Screens para pub1 e altere a porta para apontar para 4504 para pub2.

   >[!NOTE]
   >Para saber como configurar agentes de replicação Screens, consulte [Configurando o Agente de Replicação Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Criação de agentes de replicação reversa do Screens {#creating-screens-reverse-replication-agents}

1. Crie um agente de replicação reversa para pub1.
1. Crie um agente de replicação reversa para pub2. Você pode copiar o agente de replicação reversa para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte.

## Configuração da topologia do Publish {#setting-up-publish-topology}

### Etapa 1: Configurar A Descoberta Baseada No Apache Sling Oak {#step-configure-apache-sling-oak-based-discovery}

Configurar a descoberta baseada no Apache Sling Oak para todas as instâncias do Publish na topologia

Para cada instância do Publish:

1. Navegue até `https://<host>:<port>/system/console/configMgr`
1. Clique na Configuração do **Apache Sling Oak-Based Discovery Service**.
1. Atualizar URLs do conector de topologia: adicione URLs de todas as instâncias do Publish participantes que sejam:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Lista** do conector de topologia `Whitelist`: Adaptar-se a IPs ou sub-redes que abrangem todas as instâncias do Publish. Certifique-se de `whitelist` o IP/nome do host de todas as instâncias do Publish sem o número da porta.

1. Habilitar **Loops Locais de Interrupção Automática**

A configuração deve ser idêntica para cada instância do Publish e o loop local de interrupção automática impede um loop infinito.

#### Etapa 2: verificar a topologia do Publish {#step-verify-publish-topology}

Para qualquer uma das instâncias do Publish, navegue até `https://:/system/console/topology`. Você deve ver cada instância do Publish representada na topologia em **Conectores de topologia de saída**.

#### Etapa 3: Configurar Cluster Artemis do AtiveMQ {#step-setup-activemq-artemis-cluster}

Essa etapa permite criar uma senha criptografada para o cluster AtiveMQ Artemis.
O usuário do cluster e a senha de todas as instâncias do Publish na topologia devem ser idênticos. A senha da configuração do AtiveMQ Artemis deve ser criptografada. Como cada instância tem sua própria chave de criptografia, é necessário usar o Suporte de criptografia para criar uma cadeia de caracteres de senha criptografada. Em seguida, a senha criptografada pode ser usada na configuração OSGi para AtiveMQ.

Em cada instância do Publish:

1. No Console OSGi, navegue até **PRINCIPAL** > **Suporte de criptografia** (`https://<host>:<port>/system/console/crypto`).
1. Digite a senha de texto sem formatação desejada (a mesma para todas as instâncias) em **Texto sem formatação**
1. Clique em **Protect**.
1. Copie o valor **Texto protegido** para um bloco de notas ou editor de texto. Esse valor pode ser usado na configuração do OSGi para AtiveMQ.

Como cada instância do Publish, por padrão, tem chaves de criptografia exclusivas, execute essa etapa em cada instância do pub e salve a chave exclusiva para a próxima configuração.

>[!NOTE]
>
>A senha deve começar e terminar com chaves. Por exemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Etapa 4: Ativar Cluster Artemis AtiveMQ {#step-activate-activemq-artemis-cluster}

Em cada instância de publicação:

1. Navegue até o gerenciador de configurações OSGi `https://<host>:<port>/system/console/configMgr`
1. Clique na Configuração do **Apache AtiveMQ Artemis JMS Provider**
1. Atualize o seguinte:

   * ***Senha do Cluster***: usar o valor criptografado da etapa anterior por respectiva instância
   * ***Tópicos***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verificar Cluster Artemis do AtiveMQ {#verify-activemq-artemis-cluster}

Siga as etapas abaixo em cada instância do Publish:

1. Navegue até o Console OSGi > Principal > AtiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verifique e marque para exibir as portas de outras instâncias em Informações de Cluster > Topologia > nós=2, membros=2.
1. Enviar uma Mensagem de Teste (parte superior da tela em Informações do Agente)
1. Informe as seguintes alterações nos campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Olá, Mundo
   1. Exiba o `error.log` de cada instância para que você possa ver se a mensagem foi enviada e recebida no cluster.

>[!NOTE]
>
>A navegação para o Console OSGi pode levar alguns segundos após salvar a configuração na etapa anterior. Você também pode verificar o error.log para obter mais detalhes.

Como exemplo, a imagem a seguir é exibida na configuração bem-sucedida do Servidor AtiveMQ Artemis.

Se você não vir a seguinte configuração de */system/console/mq*, navegue até */system/console/mq* e clique em **Reiniciar** para reiniciar o agente.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Remover requisito de cabeçalho do referenciador {#remove-referrer-header-requirement}

Siga as etapas em cada instância do Publish:

1. Navegue até o **Console OSGi** > **Gerenciador de Configurações**
1. Clique em **Filtro de referenciador Apache Sling**
1. Atualizar configuração e **marcar Permitir Vazio**

### Configuração do autor e da instância do Publish {#configuring-author-and-publish-instance}

Depois de configurar a topologia de publicação, configure as instâncias do Autor e do Publish para exibir os resultados práticos da implementação:

>[!NOTE]
>
>**Pré-requisitos**
>
>Para começar a usar este exemplo, crie um projeto do AEM Screens e, em seguida, crie um local, exibição e canal em seu projeto. Adicione conteúdo ao canal e atribua o canal a uma exibição.

#### Etapa 1: iniciar um AEM Screens Player (dispositivo)

1. Inicie uma janela separada do navegador.
1. Vá para o Screens player usando o *navegador da Web*, ou seja,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` ou inicie o aplicativo AEM Screens. Ao abrir o dispositivo, observe o estado do dispositivo como não registrado.

>[!NOTE]
>
>É possível abrir um AEM Screens Player usando o aplicativo AEM Screens baixado ou o navegador da Web.

#### Etapa 2: Registrar um dispositivo no autor {#step-registering-a-device-on-author}

1. Vá para `https://localhost:4502/screens.html/content/screens/we-retail` ou clique no projeto e navegue até Dispositivos > Gerenciador de dispositivos.
1. Clique em **Registrar Dispositivo**.
1. Clique em **Device Registration**.
1. Clique no dispositivo que você deseja registrar e em **Registrar dispositivo**.
1. Verifique o código de registro e clique em **Validar**.
1. Insira um título para o dispositivo e clique em **Registrar**.

#### Etapa 3: atribuição do dispositivo a ser exibido {#step-assigning-the-device-to-display}

1. Clique em **Atribuir exibição** na caixa de diálogo da etapa anterior.
1. Clique no caminho de exibição do seu canal na pasta **Locais**.
1. Clique em **Atribuir**.
1. Clique em **Concluir** para concluir o processo e agora o dispositivo foi atribuído.

Verifique o reprodutor e observe o conteúdo que você adicionou ao canal.

#### Etapa 4: publicação da configuração do dispositivo nas instâncias do Publish {#step-publishing-device-configuration-to-publish-instances}

**Verificando o Dispositivo**

Siga as etapas abaixo para replicar o usuário do dispositivo:

1. Navegue até a página de administrador do usuário. Por exemplo, `https://localhost:4502/useradmin`.
1. Procure o grupo **`screens-devices-master`**.
1. Clique com o botão direito no grupo e clique em **Ativar**.

>[!CAUTION]
>
>Não ative o author-publish-screens-service, pois ele é um usuário do sistema usado pela Tarefa do Autor.

Você também pode ativar o dispositivo no Console de Gerenciamento de Dispositivos. Siga as etapas abaixo:

1. Navegue até seu projeto do Screens > **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Clique no dispositivo e clique em **Ativar** na barra de ações, conforme mostrado na figura abaixo.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, após ativar o dispositivo, você também pode editar ou atualizar o URL do servidor. Na barra de ações, clique em **Editar URL do servidor**, conforme mostrado na figura abaixo. Suas alterações se propagam para o AEM Screens Player.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de verificação de publicação {#publishing-check-list}

Os pontos a seguir resumem a Lista de verificação de publicação:

* *Usuário de Dispositivo do Screens* - Estas informações são armazenadas como um usuário AEM e podem ser ativadas em **Ferramentas** > **Segurança** > **Usuários**. O usuário recebe o prefixo &quot;screens&quot; com uma longa sequência serializada.

* *Projeto* - O projeto do AEM Screens.
* *Local* - Local ao qual o dispositivo está conectado.
* *Canais* - Um ou mais canais que estão sendo exibidos no local.
* *Agendar* - Se estiver usando um agendamento, verifique se ele foi publicado.
* *Local, Agendamentos e Pasta de Canal* - Se os recursos correspondentes estiverem dentro de uma pasta.

Siga as etapas abaixo para verificar o comportamento de criação e publicação:

1. Atualize parte do conteúdo do canal na instância do Autor.
1. Execute **Gerenciar Publicação** para publicar novas alterações em todas as instâncias do Publish.
1. Pressione **Ativar** para ativar o dispositivo no **Gerenciador de Dispositivos**.
1. Selecione **Editar URL** da URL da instância do autor para uma das URL das instâncias de publicação.
1. Verifique se o conteúdo do canal atualizado é exibido no AEM Screens Player.
1. Repita essas etapas usando uma instância diferente do Publish.


#### Etapa 5: apontar o dispositivo para a instância do Publish no painel de administração {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Exiba a interface do administrador no Screens Player e pressione o canto superior esquerdo para abrir o menu Administrador no AEM Screens Player habilitado para toque ou usando o mouse.
1. Clique na opção **Configuração** no painel lateral.
1. Altere a instância do Autor para a instância do Publish no **Servidor**.

Visualizar as alterações no AEM Screens Player.

Como alternativa, você também pode atualizar/editar o URL do servidor no console de gerenciamento de dispositivos usando as seguintes etapas:

1. Navegue até o projeto do AEM Screens e clique na pasta **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Clique no dispositivo e, na barra de ações, clique em **Editar URL do servidor**, conforme mostrado na figura abaixo. Suas alterações se propagam para o AEM Screens Player.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

O recurso **Gerenciar Publicação** permite que você forneça atualizações de conteúdo do Autor para o Publish no dispositivo. Você pode publicar/desfazer a publicação de conteúdo para todo o projeto do AEM Screens ou apenas para um de seus canais, locais, dispositivos, aplicativos ou um agendamento. Para saber mais sobre este recurso, consulte [Atualização de conteúdo sob demanda](on-demand-content.md).

## Dicas de solução de problemas {#troubleshoot-tips}

Siga a seção abaixo para obter respostas a perguntas frequentes relacionadas à configuração do Author/Publish.

### Como adicionar um redirecionamento de https para http após o registro e a atribuição iniciais? {#add-redirect}

**Solução**
Habilitar `Proxy/Load Balancer Connection in the Jetty configuration` para `true`.

### Como atualizar conteúdo offline e problemas de download do player com ativos fora do `/content/dam/projects/<project>`? {#update-offline-content}

**Solução**
Conceda permissões de leitura ao usuário bulk-offline-update-screens-service e ao grupo `screens-devices-master` para todos os `/content/dam` ou ativos específicos que deseja usar, caso deseje ser mais restritivo.

### Como resolver erros do Screens Replication Agent? {#replication-agent}

**Solução**
Verifique se você não marcou a opção Use for reverse replication (Usar para replicação reversa) na configuração do agente. O agente de replicação Screens não pode ser usado como um agente de replicação reversa e o escopo desse recurso é encaminhar comandos do dispositivo do autor para o Publish.