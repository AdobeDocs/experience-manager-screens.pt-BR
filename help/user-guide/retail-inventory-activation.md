---
title: Ativação direcionada para inventário de varejo
seo-title: Ativação direcionada para inventário de varejo
description: Este caso de uso mostra o estoque de estoque de varejo para três camisas coloridas diferentes. Dependendo do número de camisas disponíveis em estoque que são gravadas nas planilhas do Google, a imagem (camiseta vermelha, verde ou azul) com o maior número é exibida na tela.
seo-description: Este caso de uso mostra o estoque de estoque de varejo para três camisas coloridas diferentes. Dependendo do número de camisas disponíveis em estoque que são gravadas nas planilhas do Google, a imagem (camiseta vermelha, verde ou azul) com o maior número é exibida na tela.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: a7d3ec582dde83ed6efb08a6c3c6a75cc0820970
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---


# Ativação direcionada para inventário de varejo {#retail-inventory-targeted-activation}

O caso de uso a seguir demonstra três imagens diferentes com base nos valores em sua planilha do Google.

## Descrição {#description}

Este caso de uso mostra o estoque de estoque de varejo para três camisas coloridas diferentes. Dependendo do número de camisas disponíveis em estoque que são gravadas nas planilhas do Google, a imagem (camiseta vermelha, verde ou azul) com o maior número é exibida na tela.

Neste caso de uso, o suéter vermelho, verde ou azul será exibido na tela com base no valor mais alto do número de suéteres disponíveis.

## Pré-condições {#preconditions}

Antes de implementar a ativação de direcionamento de inventário de varejo, você deve saber como configurar ***Armazenamento de dados***, ***Segmentação de Audiência*** e ***Ativar direcionamento para Canais*** em um Projeto AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso da Ativação de Inventário de varejo:

1. **Preenchendo as planilhas do Google**

   1. Navegue até a página do Google ContextHubDemo.
   1. Adicione três colunas (Vermelho, Verde e Azul) com valores correspondentes para três camisas diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurar as Audiências de acordo com os requisitos**

   1. Navegue até os segmentos na sua audiência (Consulte ***Etapa 2: Configuração da segmentação de Audiência*** na **[Configuração do ContextHub na página AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Adicione três novos segmentos **For_Red**, **For_Green** e **For_Blue**.

   1. Selecione **For_Red** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação : Propriedade - Propriedade** para o editor e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da primeira propriedade**

   1. Selecione **Operador** como **maior-que** no menu suspenso

   1. Selecione **Tipo de Dados** como **número**

   1. Selecione **googlesheets/value/1/1** no menu suspenso em **Second Property name**.

   1. Arraste e solte **outra comparação: Propriedade - Propriedade** para o editor e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da primeira propriedade**.

   1. Selecione **Operador** como **maior-que** no menu suspenso

   1. Selecione **Tipo de Dados** como **número**

   1. Selecione **googlesheets/value/1/0** no menu suspenso em **Second Property name**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Blue**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento ** For_Green **conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Você observará que para os segmentos **For_Green** e **For_Green**, os dados não podem ser resolvidos no editor, pois apenas a primeira comparação é válida de agora em diante, de acordo com os valores na planilha do Google.

1. Navegue e selecione seu canal **DataDrivenRetail** (um canal sequenciável) e clique em **Editar** na barra de ações.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Você deve ter configurado o **ContextHub** **Configurações** usando a guia canal **Propriedades** —> **Personalização**.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Você deve selecionar **Marca** e **Área** para que as atividades sejam listadas corretamente ao start do processo de definição de metas.

1. **Adicionar uma imagem padrão**

   1. Adicione uma imagem padrão ao seu canal e clique em **Definição de metas**.
   1. Selecione **Marca** e **Atividade** no menu suspenso e clique em **Direcionamento de Start**.

   1. Clique em **Iniciar o direcionamento**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Antes da definição de metas do start, você deve adicionar os segmentos (**For_Green**, **For_Red** e **For_Blue**) clicando em **+ Adicionar definição de metas de experiência** no painel lateral, conforme mostrado na figura abaixo.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Adicione as imagens a todos os três cenários diferentes, conforme mostrado abaixo.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Verificando a Pré-visualização**

   1. Clique em **Pré-visualização.** Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o valor de todas as três colunas diferentes e você observará as atualizações de imagem de exibição de acordo com o valor mais alto no inventário.

   ![varejo_resultado](assets/retail_result.gif)

