---
title: Aplicação de Transições
seo-title: Aplicação de Transições
description: Siga esta página para saber como aplicar transições a seus projetos do Screens.
seo-description: Siga esta página para saber como aplicar transições a seus projetos do Screens.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 8492bdd071ae029a68ec4a4983c79ce326cac38b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---


# Aplicação de Transições {#applying-transitions}

Esta seção descreve como você pode aplicar o componente de **Transição** entre diferentes ativos (imagens e vídeos) e sequências incorporadas em um canal.


>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades do componente de **Transição** , consulte [Transição](adding-components-to-a-channel.md#transition).

## Adicionar componente de Transição aos ativos em um Canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto de AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
>
> Crie um projeto do AEM Screens **TestProject** com um canal **TestTransition**. Além disso, configure um local e uma tela para visualização da saída.

1. Navegue até o Canal **TestTransition** e clique em **Editar** na barra de ações.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >O canal **TestTransition** já tem poucos ativos (imagens e vídeos) nele. Por exemplo, o canal **TestTransition** inclui três imagens e dois vídeos, como mostrado abaixo:

   ![image2](assets/transitions2.png)


1. Arraste e solte o componente de **Transição** no editor.
   >[!CAUTION]
   >
   >Antes de adicionar a transição aos ativos no canal, certifique-se de não adicionar a transição antes do primeiro ativo no canal sequencial. O primeiro item em seu canal deve ser um ativo e não uma transição.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Por padrão, as propriedades do componente de transição, como **Tipo** , estão definidas como **Desvanecer** e a **Duração** está definida como *1600 ms*.  Além disso, não é aconselhável definir um tempo de duração de transição maior do que o ativo ao qual está sendo aplicado.

1. Além disso, se você adicionar um componente de Sequência **** Incorporada (que inclui um canal de sequência) a esse editor de canais, poderá adicionar um componente de transição no final, para que o conteúdo seja reproduzido em ordem, conforme demonstrado na figura abaixo:

   ![image3](assets/transitions5.png)

