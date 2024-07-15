---
title: Criação de um fluxo de trabalho de preenchimento de vídeo
description: Saiba mais sobre como criar um preenchimento de vídeo no fluxo de trabalho para seus ativos.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Criação de um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow}

Esta seção abrange os seguintes tópicos:

* **Visão geral**
* **Pré-requisitos**
* **Criando um Fluxo de Trabalho de Preenchimento de Vídeo**
   * **Criando um Fluxo de Trabalho**
   * **Usando o Fluxo de Trabalho no Projeto do AEM Screens**

* **Validando a Saída do Fluxo de Trabalho**

## Visão geral {#overview}

O caso de uso a seguir envolve a colocação de um vídeo (por exemplo: 1280 x 720) em um canal no qual a exibição é 1920 x 1080 e o vídeo deve ser colocado em 0x0 (canto superior esquerdo). O vídeo não deve ser ampliado ou modificado de forma alguma e não use a **Capa** no componente de vídeo.

O vídeo é exibido como um objeto do pixel 1 ao pixel 1280 e do pixel 1 ao pixel 720 para baixo. O restante do canal é a cor padrão.

## Pré-requisitos {#prerequisites}

Antes de criar um fluxo de trabalho para vídeo, conclua os seguintes pré-requisitos:

1. Carregue um vídeo na pasta **Assets** da instância do AEM
1. Crie um projeto do AEM Screens (por exemplo, **TestVideoRendering**) e um canal chamado (**VideoRendering**), conforme mostrado na figura abaixo:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Criação de um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow-1}

Para criar um fluxo de trabalho de preenchimento de vídeo, crie um fluxo de trabalho para o vídeo e use o mesmo no canal de projeto do AEM Screens.

Siga as etapas abaixo para criar e usar o workflow:

1. Criação de um fluxo de trabalho
1. Usar o fluxo de trabalho em um projeto do AEM Screens

### Criação de um fluxo de trabalho {#creating-a-workflow}

Siga as etapas abaixo para criar um fluxo de trabalho para seu vídeo:

1. Navegue até a instância do AEM.
1. Clique nas ferramentas no painel lateral.
1. Clique em **Fluxo de trabalho** > **Modelos** para criar um modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Clique em **Modelos** > **Criar** > **Criar Modelo**. Insira o **Título** (como **VideoRendition**) e **Nome** em **Adicionar Modelo de Fluxo de Trabalho**. Clique em **Concluído** para adicionar o modelo de fluxo de trabalho.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Depois de criar o modelo de fluxo de trabalho, clique no modelo (**VideoRendition**) e clique em **Editar** na barra de ações.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arraste e solte o componente **`Command Line`** no seu fluxo de trabalho.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Clique no componente **`Command Line`** e abra a caixa de diálogo de propriedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Clique na guia **Argumentos**.
1. Na caixa de diálogo **Linha de Comando - Propriedades da Etapa**, insira o formato nos **Tipos MIME** (como ***video/mp4***) e o comando como (***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4**). Este comando inicia o fluxo de trabalho no campo **Comandos**.

   Consulte os detalhes em **Tipos MIME** e **Comandos** na observação abaixo.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Clique no fluxo de trabalho (**VideoRenditions**).
1. Clique em **Iniciar Fluxo de Trabalho** na barra de ações.

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Na caixa de diálogo **Executar Fluxo de Trabalho**, clique no caminho do seu ativo na **Carga** (como ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***) e insira o **Título** como ***RunVideo*** e clique em **Executar**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Usar o fluxo de trabalho em um projeto do AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga as etapas abaixo para usar o fluxo de trabalho em seu projeto do AEM Screens:

1. Navegue até um projeto do AEM Screens (**TestVideoRendition** > **Channels** >**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Clique em **Editar** na barra de ações. Arraste e solte o vídeo que você carregou inicialmente no **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Depois de carregar o vídeo, clique em **Visualizar** para exibir a saída.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validando a Saída do Workflow {#validating-the-output-for-the-workflow}

Você pode validar sua saída ao:

* Verificar pré-visualização do vídeo no canal
* Navegue até ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** em CRXDE Lite, conforme mostrado na figura abaixo:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
