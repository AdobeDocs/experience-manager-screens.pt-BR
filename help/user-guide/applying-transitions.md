---
title: Aplicar transições
description: Saiba como aplicar transições a seus projetos do AEM Screens.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7e
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 276
ht-degree: 0%

---

# Aplicar transições {#applying-transitions}

Esta seção descreve como você pode aplicar o componente **Transição** entre diferentes ativos (imagens e vídeos) e sequências inseridas em um canal.

>[!CAUTION]
>
>Para saber mais detalhes sobre as propriedades do componente **Transição**, consulte [Transições](adding-components-to-a-channel.md#transition).

## Adicionar componente de transição ao Assets em um canal {#adding-transition}

Siga as etapas abaixo para adicionar um componente de transição ao seu projeto do AEM Screens:

>[!NOTE]
>
>**Pré-requisitos**
>
>Crie um projeto do AEM Screens **TestProject** com um canal **TestTransition**. Além disso, configure um local e uma exibição para visualizar a saída.

1. Navegue até o Canal **TestTransition** e clique em **Editar** na barra de ações.

   ![imagem1](assets/transitions1.png)

   >[!NOTE]
   >
   >O canal **TestTransition** já contém alguns ativos (imagens e vídeos). Por exemplo, o canal **TestTransition** inclui três imagens e dois vídeos, conforme mostrado abaixo:

   ![imagem2](assets/transitions2.png)


1. Arraste e solte o componente **Transição** no editor.

   >[!CAUTION]
   >
   >Antes de adicionar a transição aos seus ativos no canal, certifique-se de não adicionar a transição antes do primeiro ativo no canal sequencial. O primeiro item no canal deve ser um ativo e não uma transição.

   ![imagem3](assets/transitions3.png)

   >[!NOTE]
   >
   >Por padrão, as propriedades do componente de transição, como **Type**, estão definidas como **Fade** e a **Duration** está definida como *1600 milissegundos*. Além disso, não é aconselhável definir um tempo de duração de transição mais longo que o ativo ao qual está sendo aplicado.

1. Além disso, se você adicionar um componente de **Sequência inserida** (que inclui um canal de sequência) a esse editor de canal, será possível adicionar um componente de transição ao final. Isso garante que o conteúdo seja reproduzido na ordem correta, conforme ilustrado na imagem a seguir:

   ![imagem3](assets/transitions5.png)
