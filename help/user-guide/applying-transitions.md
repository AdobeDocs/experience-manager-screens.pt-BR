---
title: Aplicar transições
seo-title: Applying Transitions
description: Siga esta página para saber como aplicar transições aos seus projetos do Screens.
seo-description: Follow this page to learn how to apply transitions to your Screens projects.
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# Aplicar transições {#applying-transitions}

Esta seção descreve como você pode aplicar a variável **Transição** componente intermediário entre diferentes ativos (imagens e vídeos) e sequências incorporadas em um canal.


>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades da **Transição** , consulte [Transições](adding-components-to-a-channel.md#transition).

## Adicionar componente de transição aos ativos em um canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
>
>Criar um projeto do AEM Screens **TestProject** com um canal **TransiçãoDeTeste**. Além disso, configure um local e uma exibição para visualizar a saída.

1. Navegue até o canal **TransiçãoDeTeste** e clique em **Editar** na barra de ações.

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >A variável **TransiçãoDeTeste** o canal já tem alguns ativos (imagens e vídeos). Por exemplo, a variável **TransiçãoDeTeste** o canal inclui três imagens e dois vídeos, conforme mostrado abaixo:

   ![image2](assets/transitions2.png)


1. Arraste e solte a **Transição** componente ao seu editor.
   >[!CAUTION]
   >
   >Antes de adicionar a transição aos seus ativos no canal, certifique-se de não adicionar a transição antes do primeiro ativo no canal sequencial. O primeiro item no canal deve ser um ativo e não uma transição.

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >Por padrão, as propriedades do componente de transição, como **Tipo** está definida como **Desaparecer** e a variável **Duração** está definida como *1600 ms*.  Além disso, não é aconselhável definir um tempo de duração de transição mais longo que o ativo ao qual está sendo aplicado.

1. Além disso, se você adicionar um **Sequência incorporada** (que inclui um canal de sequência) a esse editor de canal, é possível adicionar um componente de transição no final, para que o conteúdo seja reproduzido em ordem, conforme demonstrado na figura abaixo:

   ![image3](assets/transitions5.png)
