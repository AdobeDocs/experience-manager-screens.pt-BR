---
title: Replicar acionadores de dados para publicar servidores
seo-title: Replicar acionadores de dados para publicar o servidor
description: Replicar acionadores de dados para publicar o servidor.
seo-description: Replicar acionadores de dados para publicar o servidor.
translation-type: tm+mt
source-git-commit: 4e86ed7c3050209b3baa67087fc149afae8340b6

---


# Replicação de acionadores de dados para servidores de publicação {#replicating-data-triggers}

Ao usar o ContextHub e o AEM Targeting Engine para personalizar o conteúdo com base em acionadores de dados em uma configuração de autor/publicação, todas as configurações relacionadas ao ContextHub e Personalização não são replicadas automaticamente com os canais quando são publicadas.

Siga esta página para saber mais sobre as etapas manuais necessárias para publicar essas configurações separadamente.

Isso se resume basicamente à publicação manual:

1. Configurações dos módulos de armazenamento e interface do usuário do ContextHub
1. Públicos-alvo de personalização
1. Atividades de personalização

## Etapas para replicar acionadores de dados para publicar o servidor {#replicating-data-triggers-publish}

Siga as etapas abaixo para replicar os acionadores de dados para publicar o servidor.

### Etapa 1:Replicação de configurações do ContextHub {#replicating-contexthub-configurations}

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Publicar agente** e clique no agente de publicação para definir suas configurações.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!Nnota]
   >Como alternativa, você pode usar o para navegar `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` para a tela diretamente para configurar e testar a conexão.

1. Clique em **Testar conexão** na barra de ação para validar a comunicação do autor com a instância de publicação, como mostrado na figura abaixo.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!Nnota]
   >Se o teste falhar, será necessário corrigir a configuração do agente de replicação entre a instância de autor e publicação. Consulte [Solução de problemas de conexão](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) de teste para obter mais detalhes.

1. Selecione **Adicionar** na árvore de tela Agente **de** distribuição e selecione o caminho de configuração para o seu projeto, por exemplo, `/conf/screens/settings/cloudsettings/configuration`.

1. Clique em **Enviar**

### Replicação dos públicos-alvo {#replicating-audiences}

1. Navegue até sua instância do AEM > **Personalização** > **Públicos** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` para navegar diretamente.

1. Detalhe na pasta do projeto, por exemplo, `/conf/screens/`.

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. Selecione todos os públicos-alvo e segmentos na interface do usuário.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Avançar** e **Publicar**.

### Replicação das atividades {#replicating-activities}

1. Navegue até sua instância do AEM > **Personalização** > **Atividades** ou use `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` para navegar diretamente.

1. Faça uma busca detalhada na pasta do projeto, ou seja, `/content/campaigns/screens/…`.

1. Selecione todas as atividades na interface do usuário.

1. Clique em **Gerenciar publicação** na barra de ações.

1. Clique em **Avançar** e **Publicar**.

> [!Nnota]
> **Importante **:>A replicação de configurações e públicos-alvo do ContextHub é feita durante a configuração do projeto, enquanto as atividades de replicação e serão necessárias sempre que a definição de metas for alterada dentro de um canal.

#### Resultado {#result}

Se a replicação for bem-sucedida, você deverá exibir a seguinte estrutura na instância de publicação (ou semelhante para o seu projeto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## Solução de problemas de conexão de teste {#troubleshoot-test}

Se a conexão de teste falhar durante a replicação das configurações do ContextHub, siga a seção abaixo para solucionar o problema:

1. Navegue até Ferramentas > **Implantação** > **Distribuição** > **Publicar agente**.

1. Clique em **Editar** na barra de ações e verifique se o URL do ponto final no campo Pontos finais **do** importador também aponta para o URL do servidor de publicação no Distribution Agent.
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. Se você não estiver usando as credenciais de administrador padrão, será necessário configurar o agente de distribuição com um nome de usuário e senha diferentes.
Siga as etapas abaixo:

   1. Navegue até Ferramentas > **Operações** > Console **da** Web `http://localhost:4502/system/console/configMgr`para abrir a tela **do console da Web do** Adobe Experience Manager.

   1. Procurar credenciais de transporte de distribuição do **Apache Sling - baseadas em credenciais do usuário DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. Crie uma configuração, preenchendo **Nome**, Nome **de** usuário e **senha**, por exemplo, *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. Clique em **Salvar**

   1. Use `Cmd +F` para procurar o **Apache Sling Distribution Agent - Fábrica** de Agentes Encaminhados para abrir as configurações e procurar o **Transport Secret Provider**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. Atualize o `(name=default)` com `(name=slingTransportSecretProvider)`.

   1. Clique em **Salvar** e execute a conexão de teste novamente na tela **Distribution Agent** da sua instância do AEM.
