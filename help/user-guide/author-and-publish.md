---
title: Configuração do autor e publicação no AEM Screens
seo-title: Configuração do autor e publicação no AEM Screens
description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação. Siga esta página para saber como configurar o autor e publicar para AEM Screens.
seo-description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação. Siga esta página para saber como configurar o autor e publicar para AEM Screens.
translation-type: tm+mt
source-git-commit: 235aa979543455882c72fa262cf7320c4298de5e
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 2%

---


# Configuração do autor e publicação no AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página destaca os seguintes tópicos:

* **Configuração de instâncias de autor e publicação**
* **Configuração da topologia de publicação**
* **Gerenciando a publicação: Fornecer atualizações de conteúdo do autor para o dispositivo**

## Pré-requisitos {#prerequisites}

Antes de começar a usar os servidores de autor e publicação, você deve ter conhecimento prévio de:

* **Topologia AEM**
* **Criação e gerenciamento do AEM Screens Project**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4 Screens Pack 2. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

>[!IMPORTANT]
>
>Se quiser usar mais de uma instância de publicação com o dispatcher, atualize o dispatcher.any arquivo no seu dispatcher. Consulte [Ativando Sessões Aderentes](dispatcher-configurations-aem-screens.md#enable-sticky-session) para obter mais detalhes.

## Configurando instâncias de autor e publicação {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para saber mais sobre o autor e publicar a visão geral da arquitetura e como o conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação, consulte [Visão geral da arquitetura do autor e publicação](author-publish-architecture-overview.md).

A seção a seguir explica como configurar agentes de replicação na topologia de criação e publicação.

Você pode configurar um exemplo simples, no qual você hospeda um autor e duas instâncias de publicação:

* Autor —> localhost:4502
* Publicar 1 (pub1) —> localhost:4503
* Publicar 2 (pub2) —> localhost:4504

## Configuração de agentes de replicação no autor {#setting-replication-agents}

Para criar agentes de replicação, você deve aprender a criar um agente de replicação padrão.

Há três agentes de replicação necessários para o Screens:

1. **Agente de Replicação Padrão  ***(especificado*** como Agente** de Replicação Padrão)
1. **Screens Replication Agent**
1. **Reverter agente de replicação**

### Etapa 1: Criando um Agente de Replicação Padrão {#step-creating-a-default-replication-agent}

Siga as etapas abaixo para criar um agente de replicação padrão:

1. Navegue até a instância AEM —> ícone de martelo —> **Operações** —> **Configuração**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Selecione **Replicação** na árvore de navegação esquerda.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Selecione **Agentes no autor** na pasta **Replicação** e clique em **Novo** para criar um novo agente de replicação padrão.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Insira **Title** e **Nome** para criar o agente de replicação e clique em **Criar**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Clique com o botão direito do mouse no agente de replicação e clique em **Abrir** para editar as configurações.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Clique em **Editar** para abrir a caixa de diálogo **Configurações do Agente** para inserir os detalhes.

   >[!NOTE]
   >
   >O usuário precisa marcar **Enabled** para habilitar o agente de replicação. Você deve marcar essa opção em Default, Screens e Reverse Replication Agents.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navegue até a guia **Transporte** e digite **URI**, **Usuário** e **Senha**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Também é possível copiar e renomear um agente de replicação padrão existente.


#### Criando Agentes de Replicação Padrão {#creating-standard-replication-agents}

1. Criar agente de replicação padrão para pub1 (o agente padrão predefinido já deve estar configurado) (por exemplo, *https://&lt;nome do host>:4503/bin/receive?sling:authRequestLogin=1*)
1. Criar agente de replicação padrão para pub2. Você pode copiar o agente rep para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte. (por exemplo, *https://&lt;nome do host>:4504/bin/receive?sling:authRequestLogin=1*)

#### Criando Agentes de Replicação de Telas {#creating-screens-replication-agents}

1. Criar agente de replicação AEM Screens para pub1. Completo, há um chamado Screens Replication Agent que aponta para a porta 4503. Isso precisa ser habilitado.
1. Criar agente de replicação AEM Screens para pub2. Copie o agente de replicação Screens para pub1 e altere a porta para 4504 para pub2.

#### Criando Agentes de Replicação Inversa de Telas {#creating-screens-reverse-replication-agents}

1. Criar agente de replicação reversa padrão para pub1.
1. Criar agente de replicação reversa padrão para pub2. Você pode copiar o agente de representante reverso para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte.

## Configuração da Topologia de Publicação {#setting-up-publish-topology}

### Etapa 1: Configurar Descoberta Baseada em Oak do Apache Sling {#step-configure-apache-sling-oak-based-discovery}

Configurar a descoberta baseada no Apache Sling Oak para todas as instâncias de publicação na topologia

Para cada instância de publicação:

1. Vá até `https://<host>:<port>/system/console/configMgr`
1. Selecione Configuração **Apache Sling Oak-Based Discovery Service**.
1. Atualizar URLs do conector de topologia: adicionar URLs de todas as instâncias de publicação de participação que sejam:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Lista** da lista de permissões do conector de topologia: adaptar a IPs ou sub-redes que abrangem instâncias de publicação de participação
1. Habilitar **Parar automaticamente loops locais**

A configuração deve ser idêntica para cada instância de publicação e o loop Local de interrupção automática impede um loop infinito.

#### Etapa 2: Verificar Topologia de Publicação {#step-verify-publish-topology}

Para qualquer uma das instâncias de publicação, navegue até `https://:/system/console/topology`. Você deve ver cada instância de publicação representada na topologia em **Conectores de topologia de saída**.

#### Etapa 3: Configurar Cluster de Artemis do AtiveMQ {#step-setup-activemq-artemis-cluster}

Esta etapa permite que você crie uma senha criptografada para o cluster AtiveMQ Artemis.
O usuário do cluster e a senha de todas as instâncias de publicação na topologia precisam ser idênticos. A senha da configuração do AtiveMQ Artemis precisa ser criptografada. Como cada instância tem sua própria chave de criptografia, é necessário usar o Suporte de criptografia para criar uma string de senha criptografada. Em seguida, a senha criptografada será usada na configuração OSGi para AtiveMQ.

Em cada instância de publicação:

1. No console OSGi, navegue até **MAIN** —> **Suporte de criptografia** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Digite a senha de texto sem formatação desejada (a mesma para todas as instâncias) em **Texto sem formatação**
1. Clique em **Protect**.
1. Copie o valor **Texto protegido** para o bloco de notas ou editor de texto. Esse valor será usado na configuração OSGi para AtiveMQ.

Como cada instância de publicação por padrão tem chaves de criptografia exclusivas, é necessário executar essa etapa em cada instância de pub e salvar a chave exclusiva para a próxima configuração.

>[!NOTE]
>
>A senha deve ser start e terminar com chaves. Por exemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Etapa 4: Ativar o Cluster AtiveMQ Artemis {#step-activate-activemq-artemis-cluster}

Em cada instância de publicação:

1. Navegue até o gerenciador de configuração OSGi `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Selecione **Configuração do Apache AtiveMQ Artemis Provedor JMS**
1. Atualize o seguinte:

   * ***Senha*** do cluster: (use valor criptografado de etapa anterior por instância respectiva)
   * ***Tópicos***: {nome: &#39;command&#39;, endereço: &#39;com.adobe.cq.screens.command&#39;, maxConsumers: 50}

#### Verifique o cluster AtiveMQ Artemis {#verify-activemq-artemis-cluster}

Siga as etapas abaixo em cada instância de publicação:

1. Navegue até Console OSGi -> Principal > Áreas AtiveMQ `https://localhost:4505/system/console/mq`.
1. Verifique e visualização as portas de outras instâncias em Informações do cluster > Topologia > nós=2, membros=2.
1. Enviar uma mensagem de teste (parte superior da tela em Informações do agente)
1. Digite as seguintes alterações nos campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Hello World
   1. Visualização o error.log de cada instância para ver se a mensagem foi enviada e recebida no cluster

>[!NOTE]
>
>Navegar no console OSGi pode levar alguns segundos depois de salvar a configuração na etapa anterior. Você também pode verificar error.log para obter mais detalhes.

Como exemplo, a imagem a seguir é exibida na configuração bem-sucedida do AtiveMQ Artemis Server.

Se você não vir a seguinte configuração de */system/console/mq*, navegue até */system/console/mq* e clique em **Reiniciar** para reiniciar o broker.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Remover requisito de cabeçalho de quem indicou {#remove-referrer-header-requirement}

Siga as etapas em cada instância de Publicação:

1. Navegue até **Console OSGi** > **Configuration Manager**
1. Selecione **Filtro de Quem indicou Apache Sling**
1. Atualizar configuração e **marcar Permitir vazio**

### Configurando a instância de autor e publicação {#configuring-author-and-publish-instance}

Depois de configurar a topologia de publicação, é necessário configurar as instâncias de autor e publicação para visualização dos resultados práticos da implementação:

>[!NOTE]
>
>**Pré-requisitos**
>
>Para começar a usar este exemplo, crie um novo projeto do AEM Screens seguido de criação de um local, exibição e canal no seu projeto. Adicione conteúdo ao seu canal e atribua o canal a uma exibição.

#### Etapa 1: Iniciar um AEM Screens Player (dispositivo) {#step-starting-an-aem-screens-player-device}

1. Inicialize uma janela de navegador separada.
1. Vá para o player do Screens usando o *navegador da Web*, ou seja,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` ou inicie o aplicativo AEM Screens. Ao abrir o dispositivo, você perceberá o estado do dispositivo como não registrado.

>[!NOTE]
>
>Você pode abrir um AEM Screens player usando o aplicativo AEM Screens baixado ou usando o navegador da Web.

#### Etapa 2: Registrando um dispositivo no autor {#step-registering-a-device-on-author}

1. Vá para `https://localhost:4502/screens.html/content/screens/we-retail` ou selecione seu projeto e navegue até Dispositivos > Gerenciador de dispositivos.
1. Selecione **Registrar dispositivo**.
1. Clique em **Device Registration** para visualização o dispositivo.
1. Selecione o dispositivo que deseja registrar e clique em **Registrar dispositivo**.
1. Verifique o código de registro e clique em **Validar**.
1. Insira um título para seu dispositivo e clique em **Register**.

#### Etapa 3: Atribuindo o dispositivo à exibição {#step-assigning-the-device-to-display}

1. Clique em **Atribuir exibição** na caixa de diálogo da etapa anterior.
1. Selecione o caminho de exibição para seu canal na pasta **Locations**.
1. Clique em **Atribuir**.
1. Clique em **Concluir** para concluir o processo e agora o dispositivo é atribuído.

Verifique seu player e você verá o conteúdo que você adicionou ao seu canal.

#### Etapa 4: Configuração do dispositivo de publicação para publicar instâncias {#step-publishing-device-configuration-to-publish-instances}

**Verificação do dispositivo**

Antes, execute as etapas abaixo para verificar a ID do dispositivo. Para verificar, procure a ID do dispositivo no CRXDE Lite, com o caminho como */home/users/screens/we-retail/devices*.

Siga as etapas abaixo para replicar o usuário do dispositivo:

1. Navegue até a página de administração do usuário (por exemplo: `https://localhost:4502/useradmin`
1. Procure pelo grupo **screens-devices-principal**
1. Clique com o botão direito do mouse no grupo e clique em **Ativar**

>[!CAUTION]
>
>Não ative author-publish-screens-service, pois ele é um usuário do sistema, usado pelo trabalho do autor.

Você também pode ativar o dispositivo a partir do Console de Gerenciamento de Dispositivos. Siga as etapas abaixo:

1. Navegue até o projeto do Screens —> **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e clique em **Ativar** na barra de ação, conforme mostrado na figura abaixo.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, depois de ativar o dispositivo, você também pode editar ou atualizar o URL do servidor clicando em **Editar URL do servidor** na barra de ação, como mostrado na figura abaixo, e suas alterações serão propagadas para o player do AEM Screens.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de verificação de publicação {#publishing-check-list}

Os pontos a seguir resumem a lista de verificação de publicação:

* *Screens Device User*  - é armazenado como um usuário AEM e deve ser ativado em  **Ferramentas** >  **Segurança** >  **Usuários**. O usuário receberá o prefixo &quot;telas&quot; com uma string serializada longa.

* *Projeto*  - O projeto da AEM Screens.
* *Local*  - Local ao qual o dispositivo está conectado.
* *Canais*  - um ou mais canais que estão sendo exibidos no local
* *Agendamento*  - se estiver usando um agendamento, verifique se isso foi publicado
* *Localização, Agendamentos e Pasta*  de Canais - se os recursos correspondentes estiverem dentro de uma pasta.

Siga as etapas abaixo para verificar o comportamento de autor/publicação:

1. Atualizar algum conteúdo de canal na instância do autor
1. Execute **Gerenciar publicação** para publicar novas alterações em todas as instâncias de publicação
1. Pressione **Ativar** para ativar o dispositivo a partir de **Gerenciador de dispositivos**
1. **Editar o** URL do URL da instância do autor para um dos URL de instâncias de publicação
1. Verifique se o conteúdo atualizado do canal é exibido no AEM Screens player
1. Repita essas etapas usando uma instância de publicação diferente


#### Etapa 5: Apontando o dispositivo para publicar a instância no painel de administração {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visualização a interface do usuário do administrador no player do Screens, mantenha pressionada a tecla no canto superior esquerdo para abrir o menu Admin, no AEM Screens player habilitado para toque ou usando um mouse.
1. Clique na opção **Configuração** no painel lateral.
1. Altere a instância do autor para publicar a instância em **Server**.

Visualização as alterações no AEM Screens player.

Como alternativa, você também pode atualizar/editar o URL do servidor no console de gerenciamento de dispositivos usando as seguintes etapas:

1. Navegue até o projeto do AEM Screens e selecione a pasta **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e clique em **Editar URL do servidor** na barra de ação, conforme mostrado na figura abaixo, e suas alterações serão propagadas para o AEM Screens player.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

O recurso **Gerenciar publicação** permite que você forneça atualizações de conteúdo do autor para publicar no dispositivo. Você pode publicar/desfazer a publicação de conteúdo para todo o seu projeto AEM Screens ou somente para um de seus canais, local, dispositivo, aplicativo ou agendamento. Para saber mais sobre esse recurso, consulte [Atualização de conteúdo sob demanda](on-demand-content.md).


