---
title: Ativação Direcionada de Estoque de Varejo
seo-title: Retail Inventory Targeted Activation
description: Este caso de uso mostra o estoque de inventário de varejo para três camisetas coloridas diferentes. Dependendo do número de camisetas disponíveis em estoque gravadas no Google Sheets, a imagem (camiseta vermelha, verde ou azul) com o número mais alto é exibida na tela.
seo-description: This Use Case showcases the retail inventory stock for three different colored sweatshirts. Depending on the number of sweatshirts available in stock that is recorded in Google Sheets, the image (red, green, or blue sweatshirt) with highest number is displayed on the screen.
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Ativação Direcionada de Estoque de Varejo {#retail-inventory-targeted-activation}

O caso de uso a seguir demonstra três imagens diferentes com base nos valores na sua Planilha do Google.

## Descrição {#description}

Este caso de uso mostra o estoque de inventário de varejo para três camisetas coloridas diferentes. Dependendo do número de camisetas disponíveis em estoque gravadas no Google Sheets, a imagem (camiseta vermelha, verde ou azul) com o número mais alto é exibida na tela.

Neste caso de uso, o suéter vermelho, verde ou azul será exibido em sua tela com base no valor mais alto do número de suéteres disponíveis.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de direcionamento de estoque de varejo, você deve aprender a configurar ***Armazenamento de dados***, ***Segmentação de público*** e ***Ativar o direcionamento para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de Ativação de Inventário de Varejo:

1. **Preencher as planilhas do Google**

   1. Navegue até a Folha de Google ContextHubDemo.
   1. Adicione três colunas (vermelha, verde e azul) com valores correspondentes para três sweatshirts diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configuração dos públicos de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público*** in **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Adicionar três novos segmentos **Para_vermelho**, **For_Green**, e **For_Blue**.

   1. Selecionar **Para_vermelho** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação : Propriedade - Propriedade** ao editor e clique no ícone configurar para editar as propriedades.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da primeira propriedade**

   1. Selecione o **Operador** as **maior que** no menu suspenso

   1. Selecionar **Tipo de dados** as **número**

   1. Selecionar **googlesheets/value/1/1** no menu suspenso em **Nome da segunda propriedade**.

   1. Arrastar e soltar **outra Comparação : Propriedade - Propriedade** ao editor e clique no ícone configurar para editar as propriedades.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da primeira propriedade**.

   1. Selecione o **Operador** as **maior que** no menu suspenso

   1. Selecionar **Tipo de dados** as **número**

   1. Selecionar **googlesheets/value/1/0** no menu suspenso em **Nome da segunda propriedade**

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação a **For_Blue** conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Da mesma forma, edite e adicione as regras de propriedade de comparação a** For_Green **segment conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Você observará que, para segmentos **For_Green** e **For_Green**, os dados não podem ser resolvidos no editor, pois somente a primeira comparação é válida a partir de agora, de acordo com os valores na Planilha do Google.

1. Navegue e selecione o **DataDrivenRetail** canal (um canal do sequenciador) e clique em **Editar** na barra de ações.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Você deveria ter configurado seu **ContextHub** **Configurações** uso do canal **Propriedades** —> **Personalização** guia.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Você deve selecionar os dois **Marca** e a variável **Área** para que as atividades sejam listadas corretamente ao iniciar o processo de direcionamento.

1. **Adição de uma imagem padrão**

   1. Adicione uma imagem padrão ao canal e clique em **Direcionamento**.
   1. Selecionar **Marca** e a variável **Atividade** no menu suspenso e clique em **Iniciar o direcionamento**.

   1. Clique em **Iniciar o direcionamento**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Antes de começar o direcionamento, é necessário adicionar os segmentos (**For_Green**, **Para_vermelho**, e **For_Blue**) clicando em **+ Adicionar direcionamento de experiência** do painel lateral como mostrado na figura abaixo.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Adicione as imagens a todos os três cenários diferentes, conforme mostrado abaixo.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Verificação da visualização**

   1. Clique em **Visualizar.** Além disso, abra a Planilha do Google e atualize o valor.
   1. Altere o valor de todas as três colunas diferentes e você observará as atualizações da imagem de exibição de acordo com o valor mais alto no inventário.
   ![retail_result](assets/retail_result.gif)
