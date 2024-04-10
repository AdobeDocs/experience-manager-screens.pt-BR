---
title: Relatório de atribuição de conteúdo
description: Esta página descreve o download e o uso do Relatório de atribuição de conteúdo.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Relatório de atribuição de conteúdo {#content-assignment-report}

O recurso Relatório de atribuição de conteúdo permite que um administrador ou autor do AEM Screens exporte uma *Relatório de atribuição de conteúdo* em formato de planilha.

## Uso do relatório de atribuição de conteúdo {#using-content-assignment-report}

O Relatório de atribuição de conteúdo permite que um autor do AEM Screens ou um administrador baixe o relatório que contém todos os ativos, como imagens, vídeos em todos os canais criados em um projeto do AEM Screens. Além disso, inclui as informações de todos os canais atribuídos a todas as exibições designadas e, de agora em diante, todos os dispositivos atribuídos a suas exibições designadas.

O Relatório de atribuição de conteúdo não só permite uma pré-visualização de todos os canais, ativos, exibições e dispositivos no projeto AEM Screens selecionado, como também fornece uma estrutura de alto nível do seu projeto.


### Pré-requisitos {#pre-reqs}

Antes de baixar o Relatório de atribuição de conteúdo, configure um projeto do AEM Screens com canais, locais e dispositivos.
Consulte os seguintes recursos para obter mais detalhes:

1. [Criação e gerenciamento de projetos](/help/user-guide/creating-a-screens-project.md)
1. [Criação e gerenciamento de canais](/help/user-guide/managing-channels.md)
1. [Criação e Gerenciamento de Locais](/help/user-guide/managing-locations.md)
1. [Criando e Gerenciando Exibições](/help/user-guide/managing-displays.md)
1. [Criando dispositivos](/help/user-guide/managing-devices.md)
1. [Atribuição de canais](/help/user-guide/channel-assignment-latest-fp.md)


## Baixar o relatório de atribuição de conteúdo {#downloading-content-assignment-report-fp}

Depois de configurar o projeto do AEM Screens e atribuir exibições a cada um dos locais como mostrado nas etapas anteriores, você estará pronto para baixar o Relatório de atribuição de conteúdo.

>[!NOTE]
>O recurso Relatório de atribuição de conteúdo só pode ser acessado no nível do projeto.

Siga as instruções abaixo para baixar o Relatório de atribuição de conteúdo:

1. Navegue até o projeto do AEM Screens e selecione o projeto **DemoScreens**.

1. Clique em **Relatório de atribuição de conteúdo** na barra de ações.

   ![imagem](/help/user-guide/assets/content-assignment-report/can-download.png)

1. A planilha baixada consiste em duas guias, como **Localizações** e **Conteúdo**. A guia Local exibe quatro colunas, como **Localizações**, **Exibições**, **Canais**, e **Dispositivos** que pode ser usado para investigar mais detalhadamente essas quatro entidades pertencentes ao seu projeto do AEM Screens.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Os dados exibidos na planilha são classificados em ordem alfabética em um formato fácil de ler.

1. Você pode clicar em qualquer um dos canais no **Canais** coluna para abrir a **Conteúdo** guia que direcionará você para esse canal e também fornecerá informações sobre ativos (imagens e vídeos) associados a esse canal específico, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
