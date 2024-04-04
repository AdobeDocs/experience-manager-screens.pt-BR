---
title: Configuração do fluxo de trabalho de posicionamento direto
seo-title: Direct Placement Workflow Configuration
description: Esta página destaca a Configuração do fluxo de trabalho de posicionamento direto.
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 1%

---


# Configuração do fluxo de trabalho de posicionamento direto {#direct-placement-workflow}

Siga esta página para saber mais sobre como configurar um fluxo de trabalho de ativo que permite inserir programaticamente um ativo em um canal predefinido do AEM Screens.

Esta seção abrange os seguintes tópicos:

* Visão geral
* Configuração do fluxo de trabalho de posicionamento direto

## Visão geral {#overview}

A Configuração do fluxo de trabalho de posicionamento direto mapeia um canal de projeto do AEM Screens para uma pasta específica em ativos e permite o posicionamento de qualquer ativo nessa pasta. É recomendável acionar a atualização offline em massa para concluir a publicação.

Como alternativa, como autor de conteúdo, você pode clicar manualmente em **Atualizar conteúdo offline**.

>[!NOTE]
>
>Para saber como usar a atualização offline em massa, consulte [Atualização de Conteúdo como um Serviço](/help/user-guide/content-update-as-a-service.md).

## Configuração do fluxo de trabalho de posicionamento direto {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de iniciar a configuração, você deve instalar o [Pacote de demonstração](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip). Depois de instalar o pacote, você poderá visualizá-lo e acessá-lo a partir da instância do AEM > Ferramentas (ícone) > **Fluxo de trabalho** > **Modelos de fluxo de trabalho**.

Siga as etapas abaixo para configurar o fluxo de trabalho de posicionamento direto:

1. Navegue até o AEM Screens a partir da sua instância AEM e crie um projeto do Screens intitulado como **Fluxo de trabalho do ativo**.

1. Crie um canal chamado como **Fluxo de trabalho - Ativos** em **Canais** pasta.

