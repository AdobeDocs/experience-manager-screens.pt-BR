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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Ativação de Reserva de Hospitalidade {#hospitality-reservation-activation}

O caso de uso a seguir demonstra o uso da ativação de reservas hospitalares com base nos valores preenchidos nas Planilhas Google.

## Descrição {#description}

Para este caso de uso, a Planilha do Google é preenchida com porcentagem de reservas em dois restaurantes **`Restaurant1`** e **`Restaurant2`**. Uma fórmula é aplicada com base nos valores de `Restaurant1` e `Restaurant2` e, com base na fórmula, o valor 1 ou 2 é atribuído à Coluna **AdTarget**.

Se o valor de **`Restaurant1`** > **`Restaurant2`**, então **AdTarget** recebe o valor **1**, caso contrário **AdTarget** recebe o valor **2**. O valor 1 gera uma opção *Steak food* e o valor dois resulta em uma exibição da opção *Thai food* na tela de exibição.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de reserva, saiba como configurar o ***Armazenamento de dados***, a ***Segmentação de público-alvo*** e a ***Habilitar o direcionamento para Canais*** em um projeto do AEM Screens.

Consulte [Configurando o ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas do caso de uso abaixo para implementar a ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. **Preenchendo as Planilhas Google e adicionando a fórmula**.

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, conforme mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurando os segmentos em Públicos de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público-alvo*** na página **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).
   1. Clique em **Folhas A1 1** e em **Editar**.
   1. Clique na propriedade de comparação e no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**.
   1. Clique no **Operador** como **igual** no menu suspenso.
   1. Insira o **Valor** como **1**.
   1. Da mesma forma, clique em **Folhas A1 2** e em **Editar**.
   1. Clique na propriedade de comparação e no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**.
   1. Clique no **Operador** como **2**.

1. Navegue e clique no seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configurando o ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >Suas **Configurações do** ContextHub **** usando a guia do canal **Propriedades** > **Personalization** já devem ter sido configuradas neste momento.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Clique em **Direcionamento** no editor e em **Marca** e **Atividade** no menu suspenso e clique em **Iniciar Direcionamento**.
1. **Verificando a Visualização**

   1. Clique em **Visualizar.** Além disso, abra suas Planilhas Google e atualize seu valor.
   1. Atualize o valor em **`Restaurant1`** e **`Restaurant2`** colunas. Se **`Restaurant1`** > **`Restaurant2`,** você poderá ver uma imagem de comida *Bife* do contrário, a imagem de comida *Tailandesa* será exibida em sua tela.

   ![resultado5](assets/result5.gif)
