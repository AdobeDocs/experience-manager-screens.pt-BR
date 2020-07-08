---
title: 'Configuração do fluxo de trabalho de disposição direta '
seo-title: Configuração do fluxo de trabalho de disposição direta
description: Esta página destaca a Configuração do Fluxo de Trabalho de Disposição Direta.
seo-description: Esta página destaca a Configuração do Fluxo de Trabalho de Disposição Direta.
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# Configuração do fluxo de trabalho de disposição direta {#direct-placement-workflow}

Siga esta página para saber mais sobre como configurar um fluxo de trabalho de ativos que permite inserir programaticamente um ativo em um canal de AEM Screens predefinido.

Esta seção aborda os seguintes tópicos:

* Visão geral
* Configuração do fluxo de trabalho de disposição direta

## Visão geral {#overview}

A Configuração do fluxo de trabalho de disposição direta mapeia um canal de projeto AEM Screens para uma pasta específica em ativos e permite o posicionamento de qualquer ativo nessa pasta. É recomendável acionar a atualização offline em massa para concluir a publicação.

Como alternativa, como autor de conteúdo, você pode clicar manualmente em **Atualizar conteúdo** offline.

>[!NOTE]
>
>Para saber como usar a atualização offline em massa, consulte Atualização de [conteúdo como um serviço](/help/user-guide/content-update-as-a-service.md).

## Configuração do fluxo de trabalho de disposição direta {#configuring-workflow}

>[!IMPORTANT]
>
>Antes de start da configuração, você deve instalar o Pacote [de](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)demonstração. Depois de instalar o pacote, você deve ser capaz de visualização e acessá-lo da sua instância do AEM —> Ferramentas (ícone) —> **Fluxo de trabalho** —> Modelos **de** fluxo de trabalho.

Siga as etapas abaixo para configurar o fluxo de trabalho de disposição direta:

1. Navegue até AEM Screens de sua instância do AEM e crie um projeto do Screens intitulado como Fluxo de trabalho **do** ativo.

1. Crie um canal chamado **Workflow-Assets** na pasta **Canais** .

1. 
