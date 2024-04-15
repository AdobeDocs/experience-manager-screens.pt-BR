---
title: Ativação de Reserva de Hospitalidade
description: Saiba como este caso de uso demonstra o uso da ativação de reserva de hospitalidade com base nos valores preenchidos nas Planilhas do Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Ativação de Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reservas hospitalares com base nos valores preenchidos nas Planilhas Google.

## Descrição {#description}

Para este caso de uso, a folha do Google é preenchida com porcentagem de reservas em dois restaurantes **`Restaurant1`** e **`Restaurant2`**. Uma fórmula é aplicada com base em valores de `Restaurant1` e `Restaurant2` e com base na fórmula, o valor 1 ou 2 é atribuído ao **AdTarget** Coluna.

Se o valor de **`Restaurant1`** > **`Restaurant2`**, depois **AdTarget** é valor atribuído **1** caso contrário **AdTarget** é valor atribuído **2**. O valor 1 gera *Comida de bife* opção e o Valor dois resultam na exibição de *Comida tailandesa* na tela.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de reserva, você deve aprender a configurar ***Armazenamento de dados***, ***Segmentação de público*** e ***Ativar o direcionamento para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas do caso de uso abaixo para implementar a ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. **Preencher as Google Sheets e adicionar a fórmula**.

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, conforme mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuração dos segmentos em Públicos-alvo de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público*** in **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).
   1. Selecione o **Folhas A1 1** e clique em **Editar**.
   1. Selecione a propriedade da comparação e clique no link **Configuração** ícone.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**.
   1. Selecione o **Operador** as **igual** no menu suspenso.
   1. Insira o **Valor** as **1**.
   1. Da mesma forma, selecione o **Folhas A1 2** e clique em **Editar**.
   1. Selecione a propriedade da comparação e clique no link **Configuração** ícone.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**.
   1. Selecione o **Operador** as **2**.

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Você deveria ter configurado seu **ContextHub** **Configurações** uso do canal **Propriedades** > **Personalização** guia.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecionar **Direcionamento** no editor e selecione **Marca** e a variável **Atividade** no menu suspenso e clique em **Iniciar o direcionamento**.
1. **Verificação da visualização**

   1. Clique em **Visualizar.** Além disso, abra as Google Sheets e atualize o valor.
   1. Atualizar o valor em **`Restaurant1`** e **`Restaurant2`** colunas. Se **`Restaurant1`** > **`Restaurant2`,** você deve conseguir visualizar uma imagem de *Bife* alimentos de outro modo, *Tailandês* a imagem dos alimentos é exibida no seu ecrã.

   ![resultado5](assets/result5.gif)
