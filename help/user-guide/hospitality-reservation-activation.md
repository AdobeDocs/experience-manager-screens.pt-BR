---
title: Ativação de Reserva de Hospitalidade
seo-title: Ativação de Reserva de Hospitalidade
description: O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.
seo-description: O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Ativação de Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.

## Descrição {#description}

Para este caso de uso, a Folha do Google é preenchida com porcentagem de reserva em dois restaurantes **Restaurant1** e **Restaurant2**. Uma fórmula é aplicada com base em valores de Restaurant1 e Restaurant2 e, com base na fórmula, o valor 1 ou 2 é atribuído à coluna **AdTarget**.

Se o valor de **Restaurant1** > **Restaurant2**, então **AdTarget** recebe o valor **1** caso contrário **AdTarget** recebe o valor **2&lt;a11/ .** O valor 1 gera a opção *Steak food* e o Valor 2 resulta na exibição da opção *Thai food* na tela de exibição.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de reserva, você deve aprender a configurar ***Data Store***, ***Segmentação de público-alvo*** e ***Ativar a segmentação para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. **Preencher as planilhas do Google e adicionar a fórmula.**

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, conforme mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configuração dos segmentos em Públicos-alvo de acordo com os requisitos**

   1. Navegue até os segmentos em seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público-alvo*** em **[Configuração do ContextHub na página AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Selecione as **Planilhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone configurar para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione **Operator** como **equal** no menu suspenso

   1. Insira o **Value** como **1**

   1. Da mesma forma, selecione as **Sheets A1 2** e clique em **Edit**.

   1. Selecione a propriedade de comparação e clique no ícone configurar para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione o **Operador** como **2**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Você deve ter configurado seu **ContextHub** **Configurações** usando a guia **Propriedades** —> **Personalização** do canal.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecione **Direcionamento** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Iniciar Direcionamento**.
1. **Verificar a visualização**

   1. Clique em **Visualizar.** Além disso, abra suas planilhas do Google e atualize seu valor.
   1. Atualize o valor nas colunas **Restaurant1** e **Restaurant2**. Se **Restaurant1** > **Restaurant2,** você poderá visualizar uma imagem de *Steak* alimento, *Thai* a imagem da comida será exibida na sua tela.

   ![resultado5](assets/result5.gif)

