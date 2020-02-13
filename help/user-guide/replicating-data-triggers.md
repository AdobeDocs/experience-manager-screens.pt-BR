---
title: Replicar acionadores de dados para publicar servidores
seo-title: Replicar acionadores de dados para publicar o servidor
description: Replicar acionadores de dados para publicar o servidor.
seo-description: Replicar acionadores de dados para publicar o servidor.
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

---


# Replicação de acionadores de dados para o servidor de publicação {#replicating-data-triggers}

Ao usar o ContextHub e o AEM Targeting Engine para personalizar o conteúdo com base em acionadores de dados em uma configuração de autor/publicação, todas as configurações relacionadas ao ContextHub e Personalização não são replicadas automaticamente com os canais quando são publicadas.

Siga esta página para saber mais sobre as etapas manuais necessárias para publicar essas configurações separadamente.

Isso se resume basicamente à publicação manual:

1. Configurações dos módulos de armazenamento e interface do usuário do ContextHub
1. Públicos-alvo de personalização
1. Atividades de personalização

## Etapas para replicar acionadores de dados para publicar o servidor {#replicating-data-triggers-publish}

Siga as etapas abaixo para replicar os acionadores de dados para publicar o servidor:

### Replicação de configurações do ContextHub {#replicating-contexthub-configurations}

1. Navegue até **Ferramentas** > **Implantação** > **Distribuição** > **Publicar agente** http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish
1. Clique no botão Testar conexão para validar se o autor pode se comunicar corretamente com a instância de publicação
1. Se o teste falhar, será necessário corrigir a configuração do agente de replicação entre o autor e a publicação
1. Verifique se o URL do ponto de extremidade também está apontando para o URL do servidor de publicação no Distribution Agent
1. Editar > Pontos de extremidade do importador
1. Clique na guia Distribuir
1. Botão de opção Selecionar Adicionar árvore
1. No navegador de caminho, selecione o caminho de configuração do seu projeto (ou seja, /conf/screens/settings/cloudsettings/configuration)
1. Clique em Enviar

### Replicação dos públicos-alvo {#replicating-audiences}

1. Navegue até Ferramentas > Personalização > Públicoshttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html
1. Fazer o detalhamento na pasta do projeto (ou seja, /conf/screens/)
1. Selecionar todos os públicos-alvo/segmentos na interface do usuário
1. Clique em Gerenciar publicação
1. Clique emAvançar
1. Clique em Publicar

### Replicação das atividades {#replicating-activities}

1. Navegue até Ferramentas > Personalização > Atividadeshttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html
1. Fazer o detalhamento na pasta do projeto (ou seja, /content/campaign/screens/...)
1. Selecionar todas as atividades na interface do usuário
1. Clique em Gerenciar publicação
1. Clique emAvançar
1. Clique em Publicar

> [!Nnota]
>A replicação de configurações e públicos-alvo do ContextHub é feita durante a configuração do projeto, enquanto as atividades de replicação e serão necessárias sempre que a definição de metas for alterada dentro de um canal.

#### Resultado {#result}

Se a replicação for bem-sucedida, você deverá exibir a seguinte estrutura na instância de publicação (ou semelhante para o seu projeto):

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`