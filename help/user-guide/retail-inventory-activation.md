---
title: Ativação Direcionada de Estoque de Varejo
description: Saiba mais sobre este caso de uso do AEM Screens que mostra o estoque de estoque de varejo para três camisetas coloridas diferentes.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Ativação Direcionada de Estoque de Varejo {#retail-inventory-targeted-activation}

O caso de uso a seguir demonstra três imagens diferentes com base nos valores na sua Planilha do Google.

## Descrição {#description}

Este caso de uso mostra o estoque de estoque de estoque de varejo para três camisetas coloridas diferentes. Dependendo do número de camisetas disponíveis em estoque gravadas no Google Sheets, a imagem (camiseta vermelha, verde ou azul) com o número mais alto será exibida.

O suéter Vermelho, Verde ou Azul é exibido com base no valor mais alto do número de suéteres disponíveis.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de direcionamento de estoque de varejo, saiba como configurar o ***Armazenamento de dados***, a ***Segmentação de público*** e a ***Habilitar o direcionamento para Canais*** em um projeto do AEM Screens.

Consulte [Configurando o ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de Ativação de Inventário de Varejo:

1. **Preenchendo as Planilhas Google**

   1. Navegue até a Folha de Google ContextHubDemo.
   1. Adicione três colunas (vermelha, verde e azul) com valores correspondentes para três sweatshirts diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurando os Públicos de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público-alvo*** na página **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Adicione três novos segmentos **Para_Vermelho**, **Para_Verde** e **Para_Azul**.

   1. Clique em **For_Red** e em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - Propriedade** no editor.
   1. Clique no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da Primeira Propriedade**.
   1. Clique no **Operador** e como **maior que** no menu suspenso.
   1. Clique em **Tipo de Dados** e como **número**.
   1. Clique em **googlesheets/value/1/1** na lista suspensa em **Nome da segunda propriedade**.
   1. Arraste e solte **outra Comparação: Propriedade - Propriedade** no editor e clique no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da Primeira Propriedade**.
   1. Clique no **Operador** e como **maior que** no menu suspenso.
   1. Clique em **Tipo de Dados** e como **número**.
   1. Clique em **googlesheets/value/1/0** na lista suspensa em **Nome da segunda propriedade**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Blue**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Green**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Observe que para os segmentos **For_Green** e **For_Green**, os dados não podem ser resolvidos no editor, pois somente a primeira comparação é válida a partir de agora, de acordo com os valores na Planilha do Google.

1. Navegue e clique no canal **DataDrivenRetail** (um canal de sequência).
1. Clique em **Editar** na barra de ações.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Você já deve ter configurado suas **Configurações do** ContextHub **** usando a guia **Propriedades** > **Personalization** do canal.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Clique na **Marca** e na **Área** para que as atividades sejam listadas corretamente quando você iniciar o processo de Direcionamento.

1. **Adicionando uma imagem padrão**

   1. Adicione uma imagem padrão ao canal e clique em **Direcionamento**.
   1. Clique em **Marca** e na **Atividade** no menu suspenso e clique em **Iniciar o Direcionamento**.
   1. Clique em **Iniciar o direcionamento**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Antes de começar o direcionamento, adicione os segmentos (**For_Green**, **For_Red** e **For_Blue**) selecionando **+ Adicionar direcionamento de experiência** no painel lateral, como mostrado na figura abaixo.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Adicione as imagens a todos os três cenários diferentes, conforme mostrado abaixo.

   ![direcionamento_de_varejo](assets/retail_targeting.gif)

1. **Verificando a Visualização**

   1. Clique em **Visualizar.** Além disso, abra sua Planilha do Google e atualize seu valor.
   1. Altere o valor de todas as três colunas diferentes. Observe as atualizações de imagem de exibição de acordo com o valor mais alto no inventário.

   ![resultado_varejo](assets/retail_result.gif)
