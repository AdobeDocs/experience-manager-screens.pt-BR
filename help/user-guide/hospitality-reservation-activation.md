---
title: Ativação da Reserva de Hospitalidade
seo-title: Ativação da Reserva de Hospitalidade
description: O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.
seo-description: O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Ativação da Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reservas de hospital com base nos valores preenchidos nas planilhas do Google.

## Descrição {#description}

Para este caso de uso, o Google Sheet é preenchido com a porcentagem de reserva em dois restaurantes **Restaurant1** e **Restaurant2**. Uma fórmula é aplicada com base nos valores de Restaurant1 e Restaurant2 e, com base na fórmula, o valor 1 ou 2 é atribuído à Coluna **AdTarget** .

Se o valor de **Restaurant1** &gt; **Restaurant2**, então o **AdTarget** recebe o valor** 1 **caso contrário, o **AdTarget** recebe o valor **2**. O Valor 1 gera a opção *Abate* e o Valor 2 resulta na exibição da opção *Tailandês Food* na tela.

## Condições prévias {#preconditions}

Antes de começar a implementar a ativação da reserva, você deve aprender a configurar o ***Data Store***, a Segmentação ***do*** público-alvo e a ***Ativar a definição de metas para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. **Preenchendo as planilhas do Google e adicionando a fórmula.**

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, como mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurar os segmentos em Públicos conforme os requisitos**

   1. Navegue até os segmentos em seu público-alvo (Consulte a ***Etapa 2: Configuração da segmentação*** de público-alvo em ** [Configuração do ContextHub na página do AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Selecione as **planilhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **igual **no menu suspenso

   1. Insira o **Valor** como **1**

   1. Da mesma forma, selecione as** Sheets A1 2 **e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso no nome **da propriedade**

   1. Selecione o **operador** como **2**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub nas telas](configuring-context-hub.md)do AEM.

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Você deve ter configurado suas **Configurações** do **ContextHub** usando a guia **Propriedades** do canal —&gt; **Personalização** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecione **Definição de metas** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Iniciar definição de metas**.
1. **Verificando a visualização**

   1. Clique em **Visualizar.** Além disso, abra suas planilhas do Google e atualize seu valor.
   1. Atualize o valor nas colunas **Restaurant1** e **Restaurant2** . Se **Restaurante1** &gt; **Restaurante2,** você poderá visualizar uma imagem de alimento *bife* , caso contrário, a imagem de comida *tailandesa* será exibida na sua tela.
   ![result5](assets/result5.gif)

