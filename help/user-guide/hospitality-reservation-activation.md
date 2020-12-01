---
title: Ativação de reserva de hospitalidade
seo-title: Ativação de reserva de hospitalidade
description: O caso de uso a seguir demonstra o uso da ativação de reserva do hospital com base nos valores preenchidos nas planilhas do Google.
seo-description: O caso de uso a seguir demonstra o uso da ativação de reserva do hospital com base nos valores preenchidos nas planilhas do Google.
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# Ativação de Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reserva do hospital com base nos valores preenchidos nas planilhas do Google.

## Descrição {#description}

Neste caso de uso, a Folha do Google é preenchida com a porcentagem de reserva em dois restaurantes **Restaurant1** e **Restaurant2**. Uma fórmula é aplicada com base nos valores de Restaurant1 e Restaurant2 e, com base na fórmula, o valor 1 ou 2 é atribuído à Coluna **AdTarget**.

Se o valor de **Restaurante1** > **Restaurante2**, então **AdTaget** recebe o valor **1** caso contrário **AdTarget** recebe o valor **2&lt;a11/ ...** O valor 1 gera a opção *Steak food* e o valor 2 resulta na exibição da opção *Thai food* na tela de exibição.

## Pré-condições {#preconditions}

Antes de implementar a ativação de reserva, você deve aprender a configurar ***Repositório de dados***, ***Segmentação de Audiência*** e ***Ativar segmentação para Canais*** em um Projeto AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso da ativação de reserva de hospitalidade para seu projeto AEM Screens:

1. **Preenchendo as planilhas do Google e adicionando a fórmula.**

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, conforme mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurar os segmentos no Audiência de acordo com os requisitos**

   1. Navegue até os segmentos na sua audiência (Consulte ***Etapa 2: Configuração da segmentação de Audiência*** na **[Configuração do ContextHub na página AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Selecione as **Folhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione **Operador** como **igual** no menu suspenso

   1. Digite **Value** como **1**

   1. Da mesma forma, selecione as **planilhas A1 2** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione **Operador** como **2**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e as Audiências devem ser pré-configuradas conforme descrito em [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Você deve ter configurado o **ContextHub** **Configurações** usando a guia canal **Propriedades** —> **Personalização**.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecione **Definição de metas** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Definição de metas do Start**.
1. **Verificando a Pré-visualização**

   1. Clique em **Pré-visualização.** Além disso, abra suas planilhas do Google e atualize seu valor.
   1. Atualize o valor nas colunas **Restaurant1** e **Restaurant2**. Se **Restaurante1** > **Restaurante2,** for possível visualização de uma imagem de *inchaço* alimentos, a imagem de alimentação *Tailandês* será exibida na tela.

   ![resultado5](assets/result5.gif)

