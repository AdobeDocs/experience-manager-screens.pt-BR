---
title: Replicar acionadores de dados para os servidores de publicação
description: Saiba como replicar acionadores de dados no servidor de publicação do AEM Screens.
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---

# Replicação dos acionadores de dados para os servidores de publicação {#replicating-data-triggers}

Ao usar o ContextHub e o mecanismo de direcionamento AEM para personalizar o conteúdo com base em acionadores de dados em uma configuração de criação/publicação, todas as configurações relacionadas ao ContextHub e à Personalização não são replicadas automaticamente com os canais quando são publicadas.

Esta página ajuda você a saber as etapas manuais necessárias para publicar essas configurações separadamente.

Isso se resume basicamente à publicação manual:

1. Configurações dos módulos de armazenamento e interface do ContextHub
1. Personalização de públicos-alvo
1. Atividades de personalização

## Etapas para replicar acionadores de dados para o servidor de publicação {#replicating-data-triggers-publish}

Siga as etapas abaixo para replicar os acionadores de dados para o servidor de publicação.

### Etapa 1: Replicar configurações do ContextHub {#replicating-contexthub-configurations}

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Agente de publicação** e selecione o agente de publicação para poder definir suas configurações.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >Como alternativa, você pode usar o `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para navegar diretamente para a tela e configurar a conexão.

1. Selecionar **Testar conexão** na barra de ação para que você possa validar a comunicação do Autor com a instância de Publicação, conforme mostrado a seguir:

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >Se o teste falhar, corrija a configuração do agente de replicação entre a instância do Autor e de Publicação. Consulte [Solução de problemas da conexão de teste](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) para obter mais detalhes.

1. Selecionar **Adicionar** do **Agente de distribuição** árvore de tela e selecione o caminho de configuração para seu projeto, por exemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Selecione **Enviar**.

### Replicação de públicos {#replicating-audiences}

1. Navegue até sua instância do AEM > **Personalização** > **Públicos-alvo** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar diretamente.

1. Detalhe a pasta do projeto, por exemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Selecione todos os públicos-alvo e segmentos na interface.

1. Selecionar **Gerenciar publicação** na barra de ações.

1. Selecionar **Próxima** e **Publish**.

### Replicação de atividades  {#replicating-activities}

1. Navegue até sua instância do AEM > **Personalização** > **Atividades** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar diretamente.

1. Detalhe a pasta do projeto, ou seja, `/content/campaigns/screens/…`.

1. Selecione todas as atividades na interface do usuário.

1. Selecionar **Gerenciar publicação** na barra de ações.

1. Selecionar **Próxima** e **Publish**.

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

1. Navegue até Ferramentas > **Implantação** > **Distribuição** > **Agente de publicação**.

1. Selecionar **Editar** na barra de ações e verifique se o URL do endpoint no **Endpoints do importador** também aponta para o URL do servidor de publicação no Agente de distribuição.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se você não estiver usando as credenciais padrão de administrador, configure o agente de distribuição com um nome de usuário e senha diferentes.

   Siga as etapas abaixo:

   1. Navegue até Ferramentas > **Operações** > **Console da Web** `http://localhost:4502/system/console/configMgr`para que você possa abrir o **Tela Console da Web do Adobe Experience Manager**.
   1. Pesquisar por **Credenciais de transporte de distribuição do Apache Sling - Credenciais do usuário com base em DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Criar uma configuração, preenchendo **Nome**, **Nome do usuário**, e **senha**, por exemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Selecionar **Salvar**
   1. Uso `Cmd +F` para procurar **Apache Sling Distribution Agent - Fábrica de agentes de encaminhamento** para abrir as configurações e pesquisar **Transportar provedor do segredo**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Atualize o `(name=default)` com `(name=slingTransportSecretProvider)`.
   1. Selecionar **Salvar** e execute a conexão de teste novamente a partir do **Agente de distribuição** da instância do AEM novamente.
