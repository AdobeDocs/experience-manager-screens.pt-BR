---
title: Relatório de atribuição de conteúdo
description: Esta página descreve o download e o uso do Relatório de atribuição de conteúdo.
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 2%

---


# Relatório de atribuição de conteúdo {#content-assignment-report}

O recurso Relatório de atribuição de conteúdo permite que um administrador ou autor da AEM Screens exporte um *Relatório de atribuição de conteúdo* em um formato de planilha.

## Usando o Relatório de Atribuição de Conteúdo {#using-content-assignment-report}

O Relatório de atribuição de conteúdo permite que um autor ou administrador da AEM Screens baixe o relatório que contém todos os ativos, como imagens, vídeos em todos os Canais criados em um projeto da AEM Screens. Além disso, inclui as informações de todos os canais atribuídos a todos os monitores designados e, a partir de então, todos os dispositivos atribuídos aos respectivos monitores designados.

O Relatório de atribuição de conteúdo não apenas permite uma pré-visualização de todos os Canais, Ativos, Exibições e Dispositivos no projeto AEM Screens selecionado, mas também fornece uma estrutura de alto nível do seu projeto.

### Usando o Relatório de Atribuição de Conteúdo {#downloading-content-assignment-report-fp}

#### Configuração do projeto {#setting-up-project}

Siga as etapas abaixo para baixar o Relatório de atribuição de conteúdo de um projeto da AEM Screens:

1. Crie um AEM Screens chamado **DemoScreens**.

   ![imagem](/help/user-guide/assets/content-assignment-report/car-1.png)

1. Crie dois canais de sequência em **DemoScreens** como **ChannelOne** e **ChannelTwo**.

   ![imagem](/help/user-guide/assets/content-assignment-report/car-2.png)

1. Selecione **ChannelOne** e clique em **Editar** na barra de ações. Adicione alguns ativos (imagens/vídeos) a este canal. Da mesma forma, adicione ativos a **ChannelTwo**.

1. Navegue até a pasta Locais de **DemoScreens** —> **Locais** e crie três locais diferentes intitulados como **SanJose**, **Dublin** e **SãoFrancisco**.

   ![imagem](/help/user-guide/assets/content-assignment-report/car-3.png)

1. Navegue até cada um dos locais e crie uma exibição para cada local, como **SanJoseMain** em **SanJose**, **DublinMain** em **Dublin**, e **SanFranciscoMain** em **Localização de São Francisco**.

1. Atribua um dispositivo a cada exibição.

   >[!NOTE]
   >Para saber mais sobre como atribuir um canal a uma tela, consulte [Atribuição de Canal](/help/user-guide/channel-assignment.md).

#### Download do relatório de atribuição de conteúdo {#downloading-content-assignment-report}

Depois de configurar seu projeto AEM Screens e atribuir exibições a cada um dos locais, conforme mostrado nas etapas anteriores, você estará pronto para baixar o Relatório de atribuição de conteúdo.

>[!NOTE]
>O recurso Relatório de atribuição de conteúdo só pode ser acessado no nível do projeto.

Siga as instruções abaixo para baixar o Relatório de atribuição de conteúdo:

1. Navegue até o projeto do AEM Screens e selecione o projeto **DemoScreens**.

1. Clique em **Relatório de atribuição de conteúdo** na barra de ações. Uma planilha do Excel deve ser baixada para a máquina local.

   ![imagem](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >A planilha baixada consiste em quatro colunas, como **Canais**, **Ativos**, **Mostra** e **Dispositivos**, que podem ser usadas para investigar essas quatro entidades pertencentes ao seu projeto AEM Screens.





