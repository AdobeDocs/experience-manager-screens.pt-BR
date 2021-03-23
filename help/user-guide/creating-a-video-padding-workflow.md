---
title: Criação de um fluxo de trabalho de preenchimento de vídeo
seo-title: Criação de um fluxo de trabalho de preenchimento de vídeo
description: Siga esta página para saber mais sobre como criar um preenchimento de vídeo no fluxo de trabalho dos seus ativos.
seo-description: Siga esta página para saber mais sobre como criar um preenchimento de vídeo no fluxo de trabalho dos seus ativos.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
feature: Telas de criação
role: Administrador, Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# Criação de um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow}

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Pré-requisitos**
* **Criação de um fluxo de trabalho de preenchimento de vídeo**
   * **Criação de um workflow**
   * **Uso do fluxo de trabalho no projeto AEM Screens**

* **Validar a saída do fluxo de trabalho**

## Visão geral {#overview}

O seguinte caso de uso envolve a inserção de um vídeo (por exemplo: 1280 x 720) em um canal em que a exibição é 1920 x 1080 e o vídeo pode ser colocado em 0x0 (canto superior esquerdo). O vídeo não deve ser esticado ou modificado de forma alguma e não usa **Cover** no componente de vídeo.

O vídeo será exibido como um objeto de pixel 1 a pixel 1280 com e de pixel 1 a pixel 720 abaixo, e o restante do canal será a cor padrão.

## Pré-requisitos {#prerequisites}

Antes de criar um fluxo de trabalho para vídeo, preencha os seguintes pré-requisitos:

1. Faça upload de um vídeo na pasta **Assets** em sua instância do AEM
1. Crie um projeto do AEM Screens (por exemplo, **TestVideoRendition**) e um canal chamado (**VideoRendering**), conforme mostrado na figura abaixo:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Criação de um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow-1}

Para criar um fluxo de trabalho de preenchimento de vídeo, você deve criar um fluxo de trabalho para o vídeo e, em seguida, usá-lo no canal do projeto AEM Screens.

Siga as etapas abaixo para criar e usar o workflow:

1. Criação de um workflow
1. Uso do fluxo de trabalho em um projeto do AEM Screens

### Criação de um workflow {#creating-a-workflow}

Siga as etapas abaixo para criar um fluxo de trabalho para o seu vídeo:

1. Navegue até a instância do AEM e clique em ferramentas no painel lateral. Selecione **Workflow** —> **Modelos** para criar um novo modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Clique em **Modelos** —> **Criar** —> **Criar Modelo**. Insira o **Title** (como **VideoRendition**) e **Name** no **Adicionar Modelo de Fluxo de Trabalho**. Clique em **Concluído** para adicionar o modelo de fluxo de trabalho.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Depois de criar o modelo de fluxo de trabalho, selecione o modelo (**VideoRepresentation**) e clique em **Editar** na barra de ações.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arraste e solte o componente **Linha de comando** no seu fluxo de trabalho.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Selecione o componente **Linha de Comando** e abra a caixa de diálogo de propriedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Selecione a guia **Argumentos** para inserir os campos na caixa de diálogo **Linha de comando - Propriedades da etapa**.

   Insira o formato no **Mime Types** (como ***video/mp4***) e o comando como (**/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=color=black&quot; cq5dam.video.fullhd-hp.mp4**) para iniciar o workflow no campo **Commands**.

   Consulte os detalhes sobre **Tipos Mime** e **Comandos** na nota abaixo.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Selecione o workflow (**VideoRepresenttions**) e clique em **Iniciar Fluxo de Trabalho** na barra de ações para abrir a caixa de diálogo **Executar Fluxo de Trabalho**.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Selecione o caminho do seu ativo no **Carga** (como ***/content/dam/huseinpeyda-cross01_512kb 2.mp4***) e insira o **Título** como ***RunVideo*** e clique em **Executar a9/>.**

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Uso do fluxo de trabalho em um projeto do AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga as etapas abaixo para usar o fluxo de trabalho no seu projeto do AEM Screens:

1. Navegue até um projeto do AEM Screens (**TestVideoRendition** —> **Canais** —>**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Clique em **Editar** na barra de ações. Arraste e solte o vídeo que você carregou inicialmente no **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Depois de fazer upload do vídeo, clique em **Preview** para exibir a saída.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validando a saída do workflow {#validating-the-output-for-the-workflow}

Você pode validar sua saída ao:

* Verificar a visualização do vídeo no canal
* Navegue até ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** no CRXDE Lite, conforme mostrado na figura abaixo:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

