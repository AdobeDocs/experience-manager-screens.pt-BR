---
title: Aplicar transições
seo-title: Aplicar transições
description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
seo-description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Telas de criação
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---

# Aplicar transições {#applying-transitions}

Esta seção descreve como você pode aplicar o componente **Transition** entre diferentes ativos (imagens e vídeos) e sequências incorporadas em um canal.


>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades do componente **Transition**, consulte [Transições](adding-components-to-a-channel.md#transition).

## Adição do componente de transição aos ativos em um canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
>
>Crie um projeto do AEM Screens **TestProject** com um canal **TestTransition**. Além disso, configure um local e uma exibição para exibir a saída.

1. Navegue até o Canal **TestTransition** e clique em **Editar** na barra de ações.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >O canal **TestTransition** já tem poucos ativos (imagens e vídeos) nele. Por exemplo, o canal **TestTransition** inclui três imagens e dois vídeos, conforme mostrado abaixo:

   ![image2](assets/transitions2.png)


1. Arraste e solte o componente **Transition** no editor.
   >[!CAUTION]
   >
   >Antes de adicionar a transição aos ativos no canal, certifique-se de não adicionar a transição antes do primeiro ativo no canal sequencial. O primeiro item em seu canal deve ser um ativo e não uma transição.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Por padrão, as propriedades do componente de transição, como **Type**, são definidas como **Fade** e **Duration** são definidas como *1600 ms*.  Além disso, não é aconselhável definir um período de transição mais longo do que o ativo ao qual está sendo aplicado.

1. Além disso, se você adicionar um componente **Embedded Sequence** (que inclui um canal de sequência) a esse editor de canal, poderá adicionar um componente de transição no final, para que o conteúdo seja reproduzido em ordem, conforme demonstrado na figura abaixo:

   ![image3](assets/transitions5.png)
