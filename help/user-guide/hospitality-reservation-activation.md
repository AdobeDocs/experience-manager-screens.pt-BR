---
title: Ativação de Reserva de Hospitalidade
seo-title: Hospitality Reservation Activation
description: O caso de uso a seguir demonstra o uso da ativação de reservas hospitalares com base nos valores preenchidos nas Planilhas Google.
seo-description: The following use case demonstrates the usage of hospital reservation activation based on the values populated in Google Sheets.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Ativação de Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reservas hospitalares com base nos valores preenchidos nas Planilhas Google.

## Descrição {#description}

Para este caso de uso, a folha do Google é preenchida com a porcentagem de reserva em dois restaurantes **Restaurante1** e **Restaurante2**. Uma fórmula é aplicada com base nos valores de Restaurant1 e Restaurant2 e com base na fórmula, o valor 1 ou 2 é atribuído ao **AdTarget** Coluna.

Se o valor de **Restaurante1** > **Restaurante2**, depois **AdTarget** é valor atribuído **1** caso contrário **AdTarget** é valor atribuído **2**. O valor 1 gera *Comida de bife* opção e Valor 2 resultam na exibição de *Comida tailandesa* na tela.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de reserva, você deve aprender a configurar ***Armazenamento de dados***, ***Segmentação de público*** e ***Ativar o direcionamento para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. **Preencher as Google Sheets e adicionar a fórmula.**

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, conforme mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuração dos segmentos em Públicos-alvo de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público*** in **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Selecione o **Folhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione o **Operador** as **igual** no menu suspenso

   1. Insira o **Valor** as **1**

   1. Da mesma forma, selecione o **Folhas A1 2** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecionar **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione o **Operador** as **2**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Você deveria ter configurado seu **ContextHub** **Configurações** uso do canal **Propriedades** —> **Personalização** guia.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecionar **Direcionamento** no editor e selecione **Marca** e a variável **Atividade** no menu suspenso e clique em **Iniciar o direcionamento**.
1. **Verificação da visualização**

   1. Clique em **Visualizar.** Além disso, abra as Google Sheets e atualize o valor.
   1. Atualizar o valor em **Restaurante1** e **Restaurante2** colunas. Se **Restaurante1** > **Restaurante2,** você deve conseguir visualizar uma imagem de *Bife* alimentos de outro modo, *Tailandês* a imagem dos alimentos é exibida no seu ecrã.
   ![result5](assets/result5.gif)
