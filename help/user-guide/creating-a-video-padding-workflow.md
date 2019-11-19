---
title: Criando um fluxo de trabalho de preenchimento de vídeo
seo-title: Criando um fluxo de trabalho de preenchimento de vídeo
description: Siga esta página para saber mais sobre como criar um preenchimento de vídeo no fluxo de trabalho para seus ativos.
seo-description: Siga esta página para saber mais sobre como criar um preenchimento de vídeo no fluxo de trabalho para seus ativos.
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Criando um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow}

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Pré-requisitos**
* **Criando um fluxo de trabalho de preenchimento de vídeo**
   * **Criação de um fluxo de trabalho**
   * **Usar o fluxo de trabalho no projeto do AEM Screens**

* **Validando a saída para o fluxo de trabalho**

## Visão geral {#overview}

O caso de uso a seguir envolve a inserção de um vídeo (por exemplo: 1280 x 720) em um canal em que a tela é 1920 x 1080 e o vídeo é colocado em 0x0 (canto superior esquerdo). O vídeo não deve ser esticado ou modificado de nenhuma maneira e não usa a **capa** no componente de vídeo.

O vídeo será exibido como um objeto de pixel 1 a pixel 1280 em todo o pixel 1 a pixel 720 para baixo e o restante do canal será a cor padrão.

## Pré-requisitos {#prerequisites}

Antes de criar um fluxo de trabalho para vídeo, conclua os seguintes pré-requisitos:

1. Carregar um vídeo na pasta **Ativos** na sua instância do AEM
1. Crie um projeto do AEM Screens (por exemplo, **TestVideoRendition**) e um canal chamado (**VideoRendering**), conforme mostrado na figura abaixo:

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## Criando um fluxo de trabalho de preenchimento de vídeo {#creating-a-video-padding-workflow-1}

Para criar um fluxo de trabalho de preenchimento de vídeo, você deve criar um fluxo de trabalho para seu vídeo e usar o mesmo no canal do projeto do AEM Screens.

Siga as etapas abaixo para criar e usar o fluxo de trabalho:

1. Criação de um fluxo de trabalho
1. Usar o fluxo de trabalho em um projeto do AEM Screens

### Criação de um fluxo de trabalho {#creating-a-workflow}

Siga as etapas abaixo para criar um fluxo de trabalho para seu vídeo:

1. Navegue até a instância do AEM e clique em ferramentas no painel lateral. Selecione **Fluxo de trabalho** —&gt; **Modelos** para criar um novo modelo.

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. Clique em **Modelos** —&gt; **Criar** —&gt; **Criar modelo**. Insira o **Título** (como **VideoRendition**) e o **Nome** no Modelo **de** Adicionar Fluxo de Trabalho. Clique em **Concluído** para adicionar o modelo de fluxo de trabalho.

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. Depois de criar o modelo de fluxo de trabalho, selecione o modelo (**VideoRendition**) e clique em **Editar** na barra de ações.

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. Arraste e solte o componente **Linha de comando **no seu fluxo de trabalho.

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. Selecione o componente Linha **de** comando e abra a caixa de diálogo de propriedades.

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. Selecione a guia **Argumentos** para inserir os campos na caixa de diálogo Linha de **comando - Propriedades** da etapa.

   Digite o formato nos Tipos **de** MIME (como ***video/mp4***) e o comando como (***/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd - hp.mp4***) para iniciar o fluxo de trabalho no campo **Comandos** .

   Consulte os detalhes sobre tipos **e** comandos **MIME** na nota abaixo.

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. Selecione o fluxo de trabalho (**VideoRenditions**) e clique em **Iniciar fluxo de trabalho** na barra de ações para abrir a caixa de diálogo **Executar fluxo de trabalho** .

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. Selecione o caminho de seu ativo na **Carga** (como ***/content/dam/huseinpeyda-crossroad01_512kb 2.mp4***) e digite o **Título ** (como ***RunVideo***) e clique em **Executar**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### Usar o fluxo de trabalho em um projeto do AEM Screens {#using-the-workflow-in-an-aem-screens-project}

Siga as etapas abaixo para usar o fluxo de trabalho em seu projeto do AEM Screens:

1. Navegue até um projeto do AEM Screens (**TestVideoRendition** —&gt; **Canais** —&gt;**VideoRendition**).

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. Arraste e solte o vídeo que você carregou inicialmente para o **Assets**.

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. Depois de fazer upload do vídeo, clique em **Visualizar** para exibir a saída.

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## Validando a saída para o fluxo de trabalho {#validating-the-output-for-the-workflow}

Você pode validar sua saída:

* Verifique a visualização do vídeo no canal
* Navegue até ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** no CRXDE Lite, como mostrado na figura abaixo:

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

