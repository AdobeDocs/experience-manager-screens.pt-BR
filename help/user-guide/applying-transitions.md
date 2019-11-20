---
title: Aplicar transições
seo-title: Aplicar transições
description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
seo-description: Siga esta página para saber como aplicar transições em seus projetos do Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 02acf7ffc447c92efb75d756071d2cd5f4aaf104

---


# Aplicar transições {#applying-transitions}

Esta seção descreve como um componente de **Transição** permite que você adicione uma transição ao seu projeto do Screens.


>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades do componente Transição, consulte [Transições](adding-components-to-a-channel.md#transition)

## Adicionar um componente de transição {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
> Crie um projeto do AEM Screens **TestProject** com um canal **TestTransition**. Além disso, configure um local e uma tela para exibir a saída.

1. Navegue até Channel **TestTransition** e clique em **Edit (Editar** ) na barra de ações.



   >[!NOTE]
   >
   >O canal **TestTransition** já tem poucos ativos (imagens e vídeos) nele. Por exemplo, o canal **TestTransition** inclui cinco imagens e um vídeo, como mostrado abaixo:



1. Arraste e solte o componente **Transição** no editor.

   > [!NOTE]
   >
   >Por padrão, o componente de transição é definido como Tipo como **Normal** com **Duração** definida como *600 ms*.


   >[!CAUTION]
   >
   >Antes de adicionar a transição aos seus ativos no canal, verifique se:
Você não adiciona transição antes do primeiro ativo no canal sequencial. O primeiro item em seu canal deve ser um ativo e não uma transição.
