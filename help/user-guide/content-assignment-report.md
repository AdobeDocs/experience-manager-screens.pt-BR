---
title: Relatório de atribuição de conteúdo
description: Esta página descreve o download e o uso do Relatório de atribuição de conteúdo.
translation-type: tm+mt
source-git-commit: b9091708221f92b11e859f0da8a7080b31b0af77
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 1%

---


# Relatório de atribuição de conteúdo {#content-assignment-report}

O recurso Relatório de atribuição de conteúdo permite que um administrador ou autor da AEM Screens exporte um Relatório *de atribuição de* conteúdo que pode estar no formato de planilha.

## Uso do relatório de atribuição de conteúdo {#using-content-assignment-report}

O Relatório de atribuição de conteúdo permite que um autor ou administrador da AEM Screens baixe o relatório que contém todos os ativos, como imagens, vídeos em todos os Canais criados em um projeto da AEM Screens. Além disso, inclui as informações de todos os canais atribuídos a todos os monitores designados e, a partir de então, todos os dispositivos atribuídos aos respectivos monitores designados.

### Uso do recurso Relatório de atribuição de conteúdo{#downloading-content-assignment-report-fp}

#### Configuração do projeto {#setting-up-project}

Siga as etapas abaixo para baixar o Relatório de atribuição de conteúdo de um projeto da AEM Screens:

1. Crie um AEM Screens intitulado como **DemoScreens**.

1. Crie dois canais de sequência em **DemoScreens** , como **ChannelOne** e **ChannelTwo**.

1. Selecione **ChannelOne** e clique em **Editar** na barra de ações. Adicione alguns ativos (imagens/vídeos) a este canal. Da mesma forma, adicione ativos ao **ChannelTwo**.

1. Navegue até a pasta Locais em **DemoScreens** —> **Locais** e crie três locais diferentes chamados de **SanJose**, **Dublin** e **São Francisco**.

1. Navegue até cada um dos locais e crie uma exibição para cada local, como **SanJoseMain** , em **SanJose** , **DublinMain** , em **Dublin** , no local de Dublin **, e** São FranciscoMain **** em SãoFranciscolocation.

1. Atribua um dispositivo a cada exibição.

#### Download do relatório de atribuição de conteúdo {#downloading-content-assignment-report}

Depois de configurar seu projeto AEM Screens e atribuir exibições a cada um dos locais, conforme mostrado nas etapas anteriores.

>[!NOTE]
>O recurso Relatório de atribuição de conteúdo só pode ser acessado no nível do projeto.

Siga as instruções abaixo para baixar o Relatório de atribuição de conteúdo:

1. Navegue até o projeto do AEM Screens e selecione o projeto **DemoScreens**.

1. Clique em Relatório de atribuição de conteúdo na barra de ações. Uma planilha do Excel deve ser baixada para a máquina local.

   >[!NOTE]
   >A planilha do Excel baixada inclui quatro colunas, como **Canais**, **Ativos**, **Exibições** e **Dispositivos** , que podem ser usadas para investigar mais detalhadamente todas essas quatro entidades.




