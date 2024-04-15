---
title: Duração da reprodução da imagem
description: Saiba mais sobre a duração da reprodução de imagem no AEM Screens.
contentOwner: jsyal
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# Duração da reprodução da imagem {#image-playback-duration}

## Visão geral {#overview}

Após criar um canal de sequência e adicionar imagens a ele, por padrão, todas as imagens assumem a duração da reprodução definida na configuração Nível de canal. Qualquer imagem individual ainda pode substituir o padrão e ter uma duração de reprodução diferente; isso é feito ao editar a duração de reprodução do componente de imagem específico.

### Pré-requisitos {#prerequisites}

Antes de implementar essa funcionalidade, configure um projeto como pré-requisito para começar a implementá-la. Por exemplo,

1. Criar um projeto do AEM Screens (neste exemplo, **ChannelLevelPlayback**)
1. Criar um canal de sequência como **PlaybackChannel** em **Canais** pasta
1. Adicionar conteúdo a **PlaybackChannel**

## Edição de atribuição da duração da reprodução da imagem no nível do canal {#editing-channel-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um canal AEM Screens.

### Atualização da duração da reprodução de imagens em um canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga as etapas abaixo para saber como atualizar a Atribuição de duração da reprodução da imagem no nível do canal:

1. Navegar até o canal de sequência **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Selecionar **Editar** na barra de ações.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Adicione duas ou mais imagens no editor de canal, como mostrado na figura abaixo.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selecione todas as imagens no canal e selecione o ícone da chave inglesa no canto superior esquerdo (como mostrado na figura abaixo). A caixa de diálogo Configurar nível de canal é aberta.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duração** de 8000 (milissegundos) a 3000 (milissegundos), ou seja, 3 segundos. Selecione a marca de seleção no canto superior direito da **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Ao atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), observe que as imagens agora são reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

