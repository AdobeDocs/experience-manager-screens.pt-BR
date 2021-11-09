---
title: Configuração do autor e publicação no AEM Screens
seo-title: Configuring Author and Publish in AEM Screens
description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor de AEM e depois replicado para várias instâncias de publicação. Siga esta página para saber como configurar o autor e a publicação para o AEM Screens.
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn how to configure author and publish for AEM Screens.
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 6f44bc9d28ed7fa3a9c8afef7ab7ecab64d53d36
workflow-type: tm+mt
source-wordcount: '1882'
ht-degree: 3%

---

# Configuração do autor e publicação no AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página destaca os seguintes tópicos:

* **Configuração de instâncias de autor e publicação**
* **Configuração da topologia de publicação**
* **Gerenciar publicação: Fornecer atualizações de conteúdo do autor para publicar no dispositivo**

## Pré-requisitos {#prerequisites}

Antes de começar a usar os servidores de criação e publicação, você deve ter conhecimento prévio de:

* **Topologia de AEM**
* **Criação e gerenciamento de projeto do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4 Screens Feature Pack 2. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

>[!IMPORTANT]
>
>Se quiser usar mais de uma instância de publicação com o dispatcher, atualize o arquivo dispatcher.any no dispatcher. Consulte [Ativar sessões adesivas](dispatcher-configurations-aem-screens.md#enable-sticky-session) para obter mais detalhes.

## Configuração de instâncias de autor e publicação {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para saber mais sobre a visão geral de criação e publicação da arquitetura e como o conteúdo é criado em uma instância de autor de AEM e depois replicado para várias instâncias de publicação, consulte [Visão geral da arquitetura de criação e publicação](author-publish-architecture-overview.md).

A seção a seguir explica como configurar agentes de replicação na topologia de criação e publicação.

Você pode configurar um exemplo simples, em que hospeda um autor e duas instâncias de publicação:

* Autor —> localhost:4502
* Publicar 1 (pub1) —> localhost:4503
* Publicar 2 (pub2) —> localhost:4504

## Configurando agentes de replicação no autor {#setting-replication-agents}

Para criar agentes de replicação, você deve aprender a criar um agente de replicação padrão.

Há 3 agentes de replicação necessários para o Screens:

1. **Agente de replicação padrão ***(especificado como*** Agente de replicação padrão**)
1. **Agente de replicação do Screens**
1. **Reverter agente de replicação**

### Etapa 1: Criando um Agente de Replicação Padrão {#step-creating-a-default-replication-agent}

Siga as etapas abaixo para criar um agente de replicação padrão:

1. Navegue até a instância do AEM —> ícone de martelo —> **Operações** —> **Configuração**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Selecione o **Replicação** na árvore de navegação esquerda.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Selecione o **Agentes do autor** do **Replicação** e clique em **Novo** para criar um novo agente de replicação padrão.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Insira o **Título** e **Nome** para criar o agente de replicação e clique em **Criar**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Clique com o botão direito do mouse no agente de replicação e clique em **Abrir** para editar as configurações.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Clique em **Editar** para abrir o **Configurações do agente** para inserir os detalhes.

   >[!NOTE]
   >
   >O usuário precisa verificar **Ativado** para ativar o agente de replicação. Você deve marcar essa opção em Default, Screens e Reverse Replication Agents.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navegue até o **Transportes** e insira a **URI**, **Usuário** e **Senha**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Também é possível copiar e renomear um agente de replicação padrão existente.


#### Criação de agentes de replicação padrão  {#creating-standard-replication-agents}

1. Criar agente de replicação padrão para pub1 (o agente padrão pronto para uso já deve estar configurado) (por exemplo, *https://&lt;hostname>:4503/bin/receive?sling:authRequestLogin=1*)
1. Crie um agente de replicação padrão para pub2. Você pode copiar o agente de representante para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte. (por exemplo, *https://&lt;hostname>:4504/bin/receive?sling:authRequestLogin=1*)

#### Criação de agentes de replicação do Screens {#creating-screens-replication-agents}

1. Crie o agente de replicação do AEM Screens para pub1. Pronto para uso, há um chamado Screens Replication Agent que aponta para a porta 4503. Isso precisa ser ativado.
1. Crie o agente de replicação do AEM Screens para pub2. Copie o agente de replicação do Screens para pub1 e altere a porta para 4504 para pub2.

   >[!NOTE]
   >Para saber como configurar os agentes de replicação do Screens, consulte [Configurando o agente de replicação do Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/configure-screens-replication.html?lang=en).

#### Criando agentes de replicação inversa do Screens {#creating-screens-reverse-replication-agents}

1. Criar agente de replicação inversa padrão para pub1.
1. Criar agente de replicação inversa padrão para pub2. Você pode copiar o agente de representante reverso para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte.

## Configuração da topologia de publicação {#setting-up-publish-topology}

### Etapa 1: Configurar a descoberta baseada no Apache Sling Oak {#step-configure-apache-sling-oak-based-discovery}

Configurar a Descoberta Baseada no Apache Sling Oak para todas as instâncias de Publicação na topologia

Para cada instância de publicação:

1. Vá até `https://<host>:<port>/system/console/configMgr`
1. Selecionar **Serviço de Descoberta Baseado em Oak do Apache Sling** Configuração.
1. Atualizar URLs do conector de Topologia: adicione URLs de todas as instâncias de publicação de participação que sejam:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Lista de permissões do conector de topologia**: adaptar a IPs ou sub-redes que abrangem instâncias de publicação de participação
1. Habilitar **Interromper automaticamente loops locais**

A configuração deve ser idêntica para cada instância de publicação e o loop Local de interrupção automática impede um loop infinito.

#### Etapa 2: Verificar topologia de publicação {#step-verify-publish-topology}

Para qualquer uma das instâncias de publicação, navegue até `https://:/system/console/topology`. Você deve ver cada instância de publicação representada na topologia em **Conectores de topologia de saída**.

#### Etapa 3: Configurar Cluster do AtiveMQ Artemis {#step-setup-activemq-artemis-cluster}

Esta etapa permite criar uma senha criptografada para o cluster AtiveMQ Artemis.
O usuário do cluster e a senha de todas as instâncias de publicação na topologia precisam ser idênticos. A senha da configuração do AtiveMQ Artemis precisa ser criptografada. Como cada instância tem sua própria chave de criptografia, é necessário usar o Suporte de criptografia para criar uma cadeia de caracteres de senha criptografada. A senha criptografada será usada na configuração OSGi para AtiveMQ.

Em cada instância de publicação:

1. No console OSGi, navegue até **PRINCIPAL** —> **Suporte de criptografia** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Digite a senha de texto simples desejada (mesma para todas as instâncias) em **Texto sem formatação**
1. Clique em **Protect**.
1. Copie o valor **Texto protegido** para o bloco de notas ou editor de texto. Esse valor será usado na configuração OSGi para AtiveMQ.

Como cada instância de publicação por padrão tem chaves de criptografia exclusivas, é necessário executar essa etapa em cada instância do pub e salvar a chave exclusiva para a próxima configuração.

>[!NOTE]
>
>A senha deve começar e terminar com chaves. Por exemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Etapa 4: Ativar Cluster de Artemis AtiveMQ {#step-activate-activemq-artemis-cluster}

Em cada instância de publicação:

1. Navegue até o Gerenciador de configuração do OSGi `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Selecionar **Provedor JMS do Apache AtiveMQ Artemis** Configuração
1. Atualize o seguinte:

   * ***Senha do Cluster***: usar valor criptografado da etapa anterior por instância respectiva
   * ***Tópicos***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verificar Cluster de Artemis do AtiveMQ {#verify-activemq-artemis-cluster}

Siga as etapas abaixo em cada instância de publicação:

1. Navegue até Console OSGi -> Principal > Áreas AtiveMQ `https://localhost:4505/system/console/mq`.
1. Verifique e marque para exibir as portas de outras instâncias em Informações do Cluster > Topologia > nós=2, membros=2.
1. Enviar uma mensagem de teste (parte superior da tela, em Informações do agente)
1. Insira as seguintes alterações nos campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Hello World
   1. Visualize o error.log de cada instância para ver se a mensagem foi enviada e recebida no cluster

>[!NOTE]
>
>Navegar até o console OSGi pode levar alguns segundos após salvar a configuração na etapa anterior. Você também pode verificar o error.log para obter mais detalhes.

Como exemplo, a imagem a seguir é exibida na configuração bem-sucedida do AtiveMQ Artemis Server.

Se você não vir a seguinte configuração de */system/console/mq*, em seguida, navegue até */system/console/mq* e clique em **Reiniciar** para reiniciar o corretor.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Remover requisito de cabeçalho do referenciador {#remove-referrer-header-requirement}

Siga as etapas em cada Instância de publicação:

1. Navegue até o **Console OSGi** > **Gerenciador de configuração**
1. Selecionar **Filtro de referenciador do Apache Sling**
1. Atualizar a configuração e **marcar Permitir vazio**

### Configuração da instância de autor e publicação {#configuring-author-and-publish-instance}

Depois de configurar a topologia de publicação, é necessário configurar as instâncias de autor e publicação para exibir os resultados práticos da implementação:

>[!NOTE]
>
>**Pré-requisitos**
>
>Para começar a usar este exemplo, crie um novo projeto do AEM Screens seguido de criar um local, exibição e canal no seu projeto. Adicione conteúdo ao canal e atribua o canal a uma exibição.

#### Etapa 1: Iniciar um reprodutor do AEM Screens (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Inicialize uma janela de navegador separada.
1. Ir para o player do Screens usando o *navegador da web*, ou seja,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` ou inicie o aplicativo AEM Screens. Ao abrir o dispositivo, você perceberá o estado do dispositivo como não registrado.

>[!NOTE]
>
>Você pode abrir um reprodutor do AEM Screens usando o aplicativo AEM Screens baixado ou usando o navegador da Web.

#### Etapa 2: Registrando um dispositivo no autor {#step-registering-a-device-on-author}

1. Ir para `https://localhost:4502/screens.html/content/screens/we-retail` ou selecione o projeto e navegue até Dispositivos > Gerenciador de dispositivos.
1. Selecionar **Registrar dispositivo**.
1. Clique em **Registro do dispositivo** para exibir o dispositivo.
1. Selecione o dispositivo que deseja registrar e clique em **Registrar dispositivo**.
1. Verifique o código de registro e clique em **Validar**.
1. Insira um título para o seu dispositivo e clique em **Registrar**.

#### Etapa 3: Atribuição do dispositivo à exibição {#step-assigning-the-device-to-display}

1. Clique em **Atribuir exibição** na caixa de diálogo da etapa anterior.
1. Selecione o caminho de exibição do seu canal na **Localizações** pasta.
1. Clique em **Atribuir**.
1. Clique em **Concluir** para concluir o processo e agora o dispositivo é atribuído.

Verifique o player e você verá o conteúdo adicionado no canal.

#### Etapa 4: Publicação da configuração do dispositivo para publicar instâncias {#step-publishing-device-configuration-to-publish-instances}

**Verificando o dispositivo**

Antes, execute as etapas abaixo para verificar a ID do dispositivo. Para verificar, procure a ID do dispositivo no CRXDE Lite, com o caminho como */home/users/screens/we-retail/devices*.

Siga as etapas abaixo para replicar o usuário do dispositivo:

1. Navegue até a página de administração do usuário (por exemplo: `https://localhost:4502/useradmin`
1. Procure a variável **screens-devices-principal** grupo
1. Clique com o botão direito no grupo e clique em **Ativar**

>[!CAUTION]
>
>Não ative o author-publish-screens-service, pois ele é um usuário do sistema, usado pelo Trabalho de Autor.

Você também pode ativar o dispositivo no Console de gerenciamento de dispositivos. Siga as etapas abaixo:

1. Navegue até o projeto do Screens —> **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e clique em **Ativar** na barra de ação, como mostrado na figura abaixo.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, depois de ativar o dispositivo, você também pode editar ou atualizar o URL do servidor clicando em **Editar URL do servidor** na barra de ações, como mostrado na figura abaixo, e suas alterações serão propagadas para o player do AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de verificação de publicação {#publishing-check-list}

Os pontos a seguir resumem a lista Verificação de publicação :

* *Usuário do dispositivo do Screens* - Isso é armazenado como um usuário AEM e pode ser ativado de **Ferramentas** > **Segurança** > **Usuários**. O usuário terá o prefixo &quot;telas&quot; com uma sequência de caracteres serializada longa.

* *Projeto* - O projeto AEM Screens.
* *Localização* - Local ao qual o dispositivo está conectado.
* *Canal(s)* - um ou mais canais exibidos no local
* *Agendar* - se estiver usando um agendamento, certifique-se de que isso seja publicado
* *Localização, agendamentos e pasta de canal* - se os recursos correspondentes estiverem dentro de uma pasta.

Siga as etapas abaixo para verificar o comportamento de criação/publicação:

1. Atualizar algum conteúdo de canal na instância do autor
1. Executar **Gerenciar publicação** para publicar novas alterações em todas as instâncias de publicação
1. Press **Ativar** para ativar o dispositivo de **Gerenciador de dispositivos**
1. **Editar URL** do URL da instância do autor para um dos URL de instâncias de publicação
1. Verifique se o conteúdo atualizado do canal é exibido no reprodutor do AEM Screens
1. Repita essas etapas usando uma instância de publicação diferente


#### Etapa 5: Apontar o dispositivo para publicar a instância no painel de administração {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visualize a interface do usuário do administrador no player do Screens, pressione e segure no canto superior esquerdo para abrir o menu Admin, no player do AEM Screens habilitado para toque ou usando um mouse.
1. Clique no botão **Configuração** no painel lateral.
1. Altere a instância do autor para publicar em **Servidor**.

Exiba as alterações no seu reprodutor AEM Screens.

Como alternativa, você também pode atualizar/editar o URL do servidor no console de gerenciamento de dispositivos usando as seguintes etapas:

1. Navegue até o projeto do AEM Screens e selecione o **Dispositivos** pasta.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e clique em **Editar URL do servidor** na barra de ações, como mostrado na figura abaixo, e suas alterações serão propagadas para o player do AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

O **Gerenciar publicação** permite que você forneça atualizações de conteúdo do autor para publicar no dispositivo. Você pode publicar/cancelar a publicação de conteúdo para todo o projeto do AEM Screens ou somente para um de seus canais, locais, dispositivos, aplicativos ou agendamentos. Para saber mais sobre esse recurso, consulte [Atualização de conteúdo sob demanda](on-demand-content.md).
