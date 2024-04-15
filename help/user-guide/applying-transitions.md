---
title: Aplicar transições
description: Saiba como aplicar transições a seus projetos do AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Aplicar transições {#applying-transitions}

Esta seção descreve como você pode aplicar a variável **Transição** componente intermediário entre diferentes ativos (imagens e vídeos) e sequências incorporadas em um canal.

>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades da **Transição** componente, consulte [Transições](adding-components-to-a-channel.md#transition).

## Adicionar componente de transição aos ativos em um canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
>
>Criar um projeto do AEM Screens **TestProject** com um canal **TransiçãoDeTeste**. Além disso, configure um local e uma exibição para visualizar a saída.

1. Navegue até o canal **TransiçãoDeTeste** e selecione **Editar** na barra de ações.

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
   >Por padrão, as propriedades do componente de transição, como **Tipo** está definida como **Desaparecer** e a variável **Duração** está definida como *1600 milissegundos*. Além disso, não é aconselhável definir um tempo de duração de transição mais longo que o ativo ao qual está sendo aplicado.

1. Além disso, se você adicionar um **Sequência incorporada** (que inclui um canal de sequência) a esse editor de canal, é possível adicionar um componente de transição no final. Isso garante que o conteúdo seja reproduzido na ordem correta, conforme ilustrado na imagem a seguir:

   ![image3](assets/transitions5.png)
