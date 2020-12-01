---
title: Criação com acionadores de dados
seo-title: Criação com acionadores de dados
description: Siga esta página para saber como criar com acionadores de dados.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# Criação com acionadores de dados {#authoring-with-data-triggers}

Esta seção destaca como ativar a definição de metas em seus canais.

>[!IMPORTANT]
>
>A versão mínima que suporta acionadores de dados em um canal AEM Screens é AEM 6.5.3 Feature Pack 3.

## Pré-requisitos {#prereqs}

Antes de seguir as etapas abaixo para ativar a definição de metas em canais, você deve aprender os [Termos chave em Configuração no AEM Screens](configuring-context-hub.md) necessários para entender o ContextHub e a Definição de metas no AEM Screens.

>[!IMPORTANT]
>
>É recomendável que você entenda e configure as configurações do ContextHub antes de ativar a definição de metas em um canal AEM Screens.

Siga os links abaixo para obter mais informações:

1. **[Configuração do armazenamento de dados](configuring-context-hub.md)**
1. **[Configuração da segmentação da Audiência](configuring-context-hub.md)**

Após concluir as etapas anteriores, você estará pronto para ativar a definição de metas em seus canais.

## Visão geral da criação com acionadores de dados {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## Habilitar a definição de metas em um Canal AEM Screens {#enabling-targeting}

Siga as etapas abaixo para ativar a definição de metas em seus canais.

1. Navegue até um dos canais AEM Screens. As etapas a seguir demonstram como habilitar a definição de metas usando **DataDrivenRetail** *(canal de sequência)* criado em um Canal AEM Screens.

1. Selecione o canal **DataDrivenRetail** e clique em **Propriedades** na barra de ações.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub e selecione o ContextHub e o caminho de Segmentos.

   1. Selecione **Caminho do ContextHub** como **libs** > **definições** > **definições de nuvem** > **predefinição** > **Definições do ContextHub** e clique em &lt;a1 2/>Selecione **.**

   1. Selecione **Caminho dos segmentos** como **conf** > **We.Retail** > **definições** > **wcm** > **segmentos** e clique em **Selecionar&lt;a 13/>.**

   1. Clique em **Salvar e fechar**.
   >[!NOTE]
   >
   >Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue e selecione **DataDrivenRetail** de **DataDrivenAssets** > **Canais** e clique em **Editar** na barra de ações. Arraste e solte os ativos no editor de canais.

   >[!NOTE]
   >
   >Se você configurou tudo corretamente, verá a opção **Definição de metas** no menu suspenso do editor, como mostra a figura abaixo.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. Clique em **Definição de metas**.

1. Selecione **Marca** e **Atividade** no menu suspenso e clique em **Direcionamento de Start**.

### Saiba mais: Exemplo de casos de uso {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação direcionada para inventário de varejo](retail-inventory-activation.md)**
1. **[Ativação de temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de reserva de hospitalidade](hospitality-reservation-activation.md)**
