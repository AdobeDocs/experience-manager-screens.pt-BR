---
title: Duração da reprodução de imagem em massa no nível do canal
seo-title: Duração da reprodução de imagem em massa no nível do canal
description: Esta página descreve como você pode editar a duração da reprodução de um componente de imagem específico.
seo-description: Esta página descreve como você pode editar a duração da reprodução de um componente de imagem específico.
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 3%

---


# Duração da reprodução de imagem em massa no nível do canal {#channel-level-bulk-image-playback-duration}

## Visão geral {#overview}

Assim que você criar um canal de sequência e adicionar imagens a ele, por padrão, todas as imagens assumirão a duração da reprodução definida na configuração no nível do Canal. Qualquer imagem individual ainda pode substituir o padrão e ter uma duração de reprodução diferente, isso é feito editando a duração de reprodução do componente de imagem específico.

### Pré-requisitos {#prerequisites}

Antes de implementar essa funcionalidade no start, certifique-se de configurar um projeto como pré-requisito para o start implementar essa funcionalidade. Por exemplo,

1. Crie um exemplo de projeto da AEM Screens, **ChannelLevelPlayback**.

1. Crie um canal de sequência como **PlaybackChannel** na pasta **Canais**.

1. Adicione conteúdo a **PlaybackChannel**.

## Edição da Atribuição de Duração da Reprodução de Imagem no Nível do Canal {#editing-channel-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um canal AEM Screens.

### Atualização da duração da reprodução de imagens em um Canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga as etapas abaixo para saber como atualizar a Atribuição de duração de reprodução de imagem no nível do Canal:

1. Navegue até o canal de sequência **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Adicione duas ou mais imagens no editor de canais, conforme mostrado na figura abaixo.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selecione todas as imagens no canal e clique no ícone da chave de fenda na parte superior esquerda (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar no nível do Canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **A caixa** Pagedialog é aberta.

   >[!NOTE]
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite **Duration** de 8000 (ms) para 3000 (ms), ou seja, 3 segundos. Clique na marca de seleção na parte superior direita da caixa de diálogo **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualizando o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), você observará que as imagens serão reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![canal_pré-visualização](assets/channel_preview.gif)

