---
title: Replicar acionadores de dados para publicar servidores
seo-title: Replicar acionadores de dados para publicar o servidor
description: Siga esta página para saber como replicar acionadores de dados para publicar o servidor.
seo-description: Replicar os acionadores de dados para publicar o servidor.
feature: Administração de telas, acionador de dados
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 2%

---


# Replicação de acionadores de dados para servidores de publicação {#replicating-data-triggers}

Ao usar o ContextHub e o Mecanismo de Direcionamento de AEM para personalizar o conteúdo com base em acionadores de dados em uma configuração de criação/publicação, todas as configurações relacionadas ao ContextHub e à Personalização não são replicadas automaticamente com os canais quando são publicadas.

Siga esta página para saber mais sobre as etapas manuais necessárias para publicar essas configurações separadamente.

Basicamente, isso se resume à publicação manual:

1. Configurações do armazenamento e da interface do usuário do ContextHub
1. Públicos-alvo de personalização
1. Atividades de personalização

## Etapas para replicar acionadores de dados para publicar no servidor {#replicating-data-triggers-publish}

Siga as etapas abaixo para replicar os acionadores de dados para publicar o servidor.

### Etapa 1: Replicação das configurações do ContextHub {#replicating-contexthub-configurations}

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Publicar Agente** e clique no agente de publicação para definir suas configurações.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Como alternativa, você pode usar o `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para navegar para a tela diretamente para configurar e testar a conexão.

1. Clique em **Testar conexão** na barra de ações para validar a comunicação do autor com a instância de publicação, conforme mostrado na figura abaixo.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se o teste falhar, será necessário corrigir a configuração do agente de replicação entre a instância de autor e publicação. Consulte [Resolução de problemas do teste de conexão](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obter mais detalhes.

1. Selecione **Add** na árvore de tela **Distribution Agent** e selecione o caminho de configuração do seu projeto, por exemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Clique em **Enviar**.

### Replicação dos públicos-alvo {#replicating-audiences}

1. Navegue até a instância do AEM > **Personalization** > **Audiences** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar diretamente.

1. Detalhe na pasta do projeto, por exemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Selecione todos os públicos-alvo e segmentos na interface do usuário.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Next** e **Publish**.

### Replicação das atividades {#replicating-activities}

1. Navegue até a instância de AEM > **Personalization** > **Activities** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar diretamente.

1. Faça o detalhamento na pasta do projeto, ou seja, `/content/campaigns/screens/…`.

1. Selecione todas as atividades na interface do usuário.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Next** e **Publish**.

>[!IMPORTANT]
>
>A replicação de configurações e públicos do ContextHub é feita durante a configuração do projeto, enquanto a replicação de atividades e serão necessárias sempre que o direcionamento for alterado dentro de um canal.

#### Resultado {#result}

Se a replicação for bem-sucedida, você deverá exibir a seguinte estrutura na instância de publicação (ou semelhante para o seu projeto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Solução de problemas de conexão de teste {#troubleshoot-test}

Se a conexão de teste falhar durante a replicação das configurações do ContextHub, siga a seção abaixo para solucionar o problema:

1. Navegue até Ferramentas > **Implantação** > **Distribuição** > **Publicar Agente**.

1. Clique em **Edit** na barra de ações e verifique se o URL do ponto de extremidade no campo **Importer Endpoints** também aponta para o URL do servidor de publicação no Distribution Agent.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se você não estiver usando as credenciais de administrador padrão, precisará configurar o agente de distribuição com um nome de usuário e senha diferentes.

   Siga as etapas abaixo:

   1. Navegue até Ferramentas > **Operações** > **Console da Web** `http://localhost:4502/system/console/configMgr`para abrir a **tela do Console da Web do Adobe Experience Manager**.
   1. Procure por **Credenciais de Transporte de Distribuição do Apache Sling - Baseadas em Credenciais do Usuário DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Crie uma configuração, preenchendo **Name**, **User name** e **password**, por exemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Clique em **Salvar**
   1. Use `Cmd +F` para procurar **Apache Sling Distribution Agent - Forward Agents Fatory** para abrir as configurações e procurar **Transport Secret Provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Atualize o `(name=default)` com `(name=slingTransportSecretProvider)`.
   1. Clique em **Save** e execute a conexão de teste novamente a partir da tela **Distribution Agent** da instância de AEM novamente.
