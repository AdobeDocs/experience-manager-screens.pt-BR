---
title: Aplicar transições
seo-title: Aplicar transições
description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
seo-description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 2708464222321fd138c986f19d8572c71f1dae75

---


# Aplicar transições {#applying-transitions}

Esta seção descreve como um componente de **Transição** permite que você adicione uma transição ao seu projeto do Screens.


>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades do componente Transição, consulte [Transições](adding-components-to-a-channel.md#transition)

## Adicionar componente de transição aos ativos em um canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
> Crie um projeto do AEM Screens **TestProject** com um canal **TestTransition**. Além disso, configure um local e uma tela para exibir a saída.

1. Navegue até Channel **TestTransition** e clique em **Edit (Editar** ) na barra de ações.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >O canal **TestTransition** já tem poucos ativos (imagens e vídeos) nele. Por exemplo, o canal **TestTransition** inclui três imagens e dois vídeos, como mostrado abaixo:

   ![image2](assets/transitions2.png)


1. Arraste e solte o componente **Transição** no editor.
   >[!CAUTION]
   >
   >Antes de adicionar a transição aos seus ativos no canal, verifique se:
Você não adiciona transição antes do primeiro ativo no canal sequencial. O primeiro item em seu canal deve ser um ativo e não uma transição.

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >Por padrão, o componente de transição é definido como Tipo como **Normal** com **Duração** definida como *600 ms*.  Além disso, não é aconselhável definir um tempo de duração de transição maior do que o ativo ao qual está sendo aplicado.


## Adicionar componente de transição a vídeos em um canal {#adding-transition-videos}

Ao aplicar o componente de transição entre vídeos, sempre defina o **Tipo** como **Desvanecer** e a Duração **** da sequência como **1600 ms**.

![image3](assets/transitions4.png)