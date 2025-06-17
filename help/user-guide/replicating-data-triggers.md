---
title: Replicar acionadores de dados para os servidores de publicação
description: Saiba como replicar acionadores de dados no servidor de publicação do AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Replicação dos acionadores de dados para os servidores de publicação {#replicating-data-triggers}

Ao usar o ContextHub e o mecanismo de direcionamento do AEM para personalizar o conteúdo com base em acionadores de dados em uma configuração de criação/publicação, todas as configurações relacionadas ao ContextHub e ao Personalization não são replicadas automaticamente com os canais quando publicadas.

Esta página ajuda você a saber as etapas manuais necessárias para publicar essas configurações separadamente.

Esse processo se resume basicamente à publicação manual do seguinte:

1. Configurações dos módulos de armazenamento e interface do ContextHub
1. Públicos da Personalization
1. Atividades do Personalization

## Etapas para replicar acionadores de dados para o servidor de publicação {#replicating-data-triggers-publish}

Siga as etapas abaixo para replicar os acionadores de dados para o servidor de publicação.

### Etapa 1: Replicar configurações do ContextHub {#replicating-contexthub-configurations}

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Agente de Publicação** e clique no agente de publicação para definir suas configurações.

   ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Como alternativa, você pode usar o `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para navegar diretamente para a tela a fim de configurar e testar a conexão.

1. Clique em **Testar conexão** na barra de ações para que você possa validar a comunicação do Autor com a instância de Publicação, conforme mostrado a seguir:

   ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se o teste falhar, corrija a configuração do agente de replicação entre a instância do Autor e de Publicação. Consulte [Solução de problemas de conexão de teste](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obter mais detalhes.

1. Clique em **Adicionar** da árvore de tela do **Agente de Distribuição** e clique no caminho de configuração do seu projeto, por exemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Clique em **Enviar**.

### Replicação de públicos {#replicating-audiences}

1. Navegue até sua instância do AEM > **Personalization** > **Públicos-alvo** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar diretamente.

1. Detalhe sua pasta de projeto, por exemplo, `/conf/screens/`.

   ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Clique em todos os públicos-alvo e segmentos na interface do usuário do.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Avançar** e **Publicar**.

### Replicação de atividades {#replicating-activities}

1. Navegue até sua instância do AEM > **Personalization** > **Atividades** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar diretamente.

1. Detalhe a pasta do projeto, ou seja, `/content/campaigns/screens/…`.

1. Clique em todas as atividades na interface do usuário.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Avançar** e **Publicar**.

>[!IMPORTANT]
>
>A replicação de configurações e públicos do ContextHub é feita durante a configuração do projeto, enquanto as atividades de replicação são replicadas e são necessárias sempre que o direcionamento é alterado em um canal.

#### Resultado {#result}

Se a replicação for bem-sucedida, você deverá exibir a seguinte estrutura na instância de publicação (ou semelhante para o seu projeto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Solução de problemas da conexão de teste {#troubleshoot-test}

Se a conexão de teste falhar ao replicar as configurações do ContextHub, siga a seção abaixo para solucionar o problema:

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Agente de Publicação**.

1. Clique em **Editar** na barra de ações e verifique se a URL do ponto de extremidade no campo **Pontos de Extremidade do Importador** também aponta para a URL do servidor de publicação no Agente de Distribuição.
   ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se você não estiver usando as credenciais padrão de administrador, configure o Agente de Distribuição com um nome de usuário e senha diferentes.

   Siga as etapas abaixo:

   1. Navegue até Ferramentas > **Operações** > **Console da Web** `http://localhost:4502/system/console/configMgr`para poder abrir a **tela Console da Web do Adobe Experience Manager**.
   1. Pesquisar por **`Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider`**

      ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Crie uma configuração preenchendo **Name**, **User name** e **password**, por exemplo, *slingTransportSecretProvider*.

      ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Clique em **Salvar**
   1. Use `Cmd +F` para pesquisar o **Apache Sling Distribution Agent - Fatory de Agentes de Encaminhamento** para abrir as configurações e pesquisar o **Provedor do Segredo de Transporte**.

      ![imagem1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Atualize o `(name=default)` com `(name=slingTransportSecretProvider)`.
   1. Clique em **Salvar** e execute a conexão de teste novamente a partir da tela do **Agente de Distribuição** a partir da sua instância AEM novamente.
