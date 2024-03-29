---
title: Duração da reprodução da imagem
seo-title: Image Playback Duration
description: Siga esta página para saber mais sobre a duração da reprodução da imagem.
seo-description: Follow this page to learn about image playback duration.
contentOwner: jsyal
source-git-commit: 69a40e437fa9b19e283bcf1a1322d18e17990a49
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# Duração da reprodução da imagem {#image-playback-duration}

## Visão geral {#overview}

Depois de criar um canal de sequência e adicionar imagens a ele, por padrão, todas as imagens assumirão a duração da reprodução definida na configuração Nível de canal. Qualquer imagem individual ainda pode substituir o padrão e ter uma duração de reprodução diferente; isso é feito ao editar a duração de reprodução do componente de imagem específico.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, configure um projeto como pré-requisito para começar a implementá-la. Por exemplo,

1. Criar um projeto do AEM Screens (neste exemplo, **ChannelLevelPlayback**)

1. Criar um canal de sequência como **PlaybackChannel** em **Canais** pasta

1. Adicionar conteúdo a **PlaybackChannel**

## Edição de atribuição da duração da reprodução da imagem no nível do canal {#editing-channel-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um canal AEM Screens.

### Atualização da duração da reprodução de imagens em um canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga as etapas abaixo para saber como atualizar a Atribuição de duração da reprodução da imagem no nível do canal:

1. Navegar até o canal de sequência **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Adicione duas ou mais imagens no editor de canal, como mostrado na figura abaixo.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selecione todas as imagens no canal e clique no ícone da chave inglesa na parte superior esquerda (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar nível de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duração** de 8000 (ms) a 3000 (ms), ou seja, 3 segundos. Clique na marca de seleção na parte superior direita do **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), você notará que as imagens serão reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

