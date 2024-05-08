---
title: Configuração do fluxo de trabalho de posicionamento direto
description: Esta página destaca a Configuração do fluxo de trabalho de posicionamento direto.
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# Configuração do fluxo de trabalho de posicionamento direto {#direct-placement-workflow}

Siga esta página para aprender a configurar um fluxo de trabalho de ativo que permite inserir programaticamente um ativo em um canal predefinido do AEM Screens.

Esta seção abrange os seguintes tópicos:

* Visão geral
* Configuração do fluxo de trabalho de posicionamento direto

## Visão geral {#overview}

A Configuração do fluxo de trabalho de posicionamento direto mapeia um canal de projeto do AEM Screens para uma pasta específica em ativos e permite o posicionamento de qualquer ativo nessa pasta. A Adobe recomenda acionar uma atualização offline em massa para concluir a publicação.

Como alternativa, como um Autor de conteúdo, você pode clicar manualmente em **Atualizar conteúdo offline**.

>[!NOTE]
>
>Para saber como usar a atualização offline em massa, consulte [Atualização de Conteúdo como um Serviço](/help/user-guide/content-update-as-a-service.md).

## Configuração do fluxo de trabalho de posicionamento direto {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de iniciar a configuração, instale o `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. Depois de instalar o pacote, você poderá visualizá-lo e acessá-lo a partir da instância do AEM > Ferramentas (ícone) > **Fluxo de trabalho** > **Modelos de fluxo de trabalho**.

Siga as etapas abaixo para configurar o fluxo de trabalho de posicionamento direto:

1. Navegue até o AEM Screens a partir da sua instância AEM e crie um projeto do Screens intitulado como **Fluxo de trabalho do ativo**.

1. Crie um canal chamado como **Fluxo de trabalho - Ativos** em **Canais** pasta.

