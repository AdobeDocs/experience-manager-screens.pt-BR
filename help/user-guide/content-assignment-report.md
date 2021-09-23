---
title: Relatório de atribuição de conteúdo
description: Esta página descreve o download e o uso do Relatório de atribuição de conteúdo.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 6%

---

# Relatório de atribuição de conteúdo {#content-assignment-report}

O recurso Relatório de atribuição de conteúdo permite que um administrador ou autor do AEM Screens exporte um *Relatório de atribuição de conteúdo* em um formato de planilha.

## Uso do relatório de atribuição de conteúdo {#using-content-assignment-report}

O Relatório de atribuição de conteúdo permite que um autor do AEM Screens ou um administrador baixe o relatório que contém todos os ativos, como imagens, vídeos em todos os canais criados em um projeto do AEM Screens. Além disso, inclui as informações de todos os canais atribuídos a todas as exibições designadas e, a partir de então, todos os dispositivos atribuídos às suas exibições designadas.

O Relatório de atribuição de conteúdo não só permite uma pré-visualização de todos os Canais, Ativos, Exibições e Dispositivos no projeto AEM Screens selecionado, como também fornece uma estrutura de alto nível do projeto.


### Pré-requisitos {#pre-reqs}

Antes de baixar o Relatório de atribuição de conteúdo, configure um projeto do AEM Screens com Canais, Locais e Dispositivos.
Consulte os seguintes recursos para obter mais detalhes:

1. [Criação e gerenciamento de projetos](/help/user-guide/creating-a-screens-project.md)
1. [Criação e gerenciamento de canais](/help/user-guide/managing-channels.md)
1. [Criação e gerenciamento de localizações](/help/user-guide/managing-locations.md)
1. [Criação e gerenciamento de exibições](/help/user-guide/managing-displays.md)
1. [Criação de dispositivos](/help/user-guide/managing-devices.md)
1. [Atribuição de canais](/help/user-guide/channel-assignment-latest-fp.md)


## Download do relatório de atribuição de conteúdo {#downloading-content-assignment-report-fp}

Depois de configurar seu projeto do AEM Screens e atribuir exibições para cada um dos locais, conforme mostrado nas etapas anteriores, você estará pronto para baixar o Relatório de atribuição de conteúdo.

>[!NOTE]
>O recurso Relatório de atribuição de conteúdo só pode ser acessado no nível do projeto.

Siga as instruções abaixo para baixar o Relatório de atribuição de conteúdo:

1. Navegue até o projeto do AEM Screens e selecione o projeto **DemoScreens**.

1. Clique em **Relatório de atribuição de conteúdo** na barra de ações.

   ![imagem](/help/user-guide/assets/content-assignment-report/can-download.png)

1. A planilha baixada consiste em duas guias, como **Locations** e **Content**. A guia Local exibe quatro colunas, como **Localizações**, **Exibe**, **Canais** e **Dispositivos**, que podem ser usadas para investigar ainda mais essas quatro entidades pertencentes ao seu projeto do AEM Screens.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Os dados exibidos na planilha são classificados alfabeticamente em um formato de fácil leitura.

1. Você pode clicar em qualquer um dos canais da coluna **Channels** para abrir a guia **Content** que o navegará diretamente para esse canal e também fornecerá informações sobre ativos (imagens e vídeos) associados a esse canal específico, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
