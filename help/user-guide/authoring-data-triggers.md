---
title: Criação com acionadores de dados
seo-title: Criação com acionadores de dados
description: Siga esta página para saber como criar com acionadores de dados.
translation-type: tm+mt
source-git-commit: 24fda825220c6c2863fd76098a2f06209d9e0190

---


# Criação com acionadores de dados {#authoring-with-data-triggers}

Esta seção destaca como ativar a definição de metas em seus canais.

## Pré-requisitos {#prereqs}

Antes de seguir as etapas abaixo para ativar a definição de metas nos canais, você deve saber os seguintes tópicos:

1. Termos chave na configuração no AEM Screens
1. Configurar o Data Store
1. Configurar a segmentação do público-alvo

Depois de concluir as etapas anteriores, você pode estar pronto para ativar a definição de metas em seus canais.

## Visão geral da criação com acionadores de dados {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Ativar a definição de metas em um canal do AEM Screens {#enabling-targeting}

Siga as etapas abaixo para ativar a definição de metas em seus canais.

1. Navegue até um dos canais do AEM Screens. As etapas a seguir demonstram como habilitar a definição de metas usando **DataDrivenRetail** criado em um Canal do AEM Screens.

1. Selecione o canal **DataDrivenRetail** e clique em **Propriedades** na barra de ações.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub.

   1. Selecione o Caminho **do** ContextHub como **libs** > **configurações** > **configurações** de nuvem > **padrão** **** ****> Configurações doContextHube clique em Selecionar.

   1. Selecione o Caminho **dos** segmentos como **conf** > **We.Retail** > **configurações** > **wcm** **** ****>segmentos e clique emSelect.

   1. Clique em **Salvar e fechar**.
   >[!NOTE]
   Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue e selecione **DataDrivenRetail** em **DataDrivenAssets** > **Canais** e clique em **Editar** na barra de ações.

   >[!NOTE]
   Se você configurou tudo corretamente, verá a opção **Definição de metas** na lista suspensa do editor, como mostra a figura abaixo.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Depois de configurar as configurações do ContextHub para o seu canal, siga as etapas anteriores de 1 a 4, para os outros três canais de sequência também se desejar seguir todos os casos de uso abaixo.

### Saiba mais: Casos de uso de exemplo {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação Direcionada para Inventário de Varejo](retail-inventory-activation.md)**
1. **[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação da Reserva de Hospitalidade](hospitality-reservation-activation.md)**

