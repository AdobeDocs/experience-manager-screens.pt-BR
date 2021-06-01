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
feature: Telas de criação
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 4%

---


# Duração da reprodução de imagem em massa no nível do canal {#channel-level-bulk-image-playback-duration}

## Visão geral {#overview}

Depois de criar um canal de sequência e adicionar imagens a ele, por padrão, todas as imagens presumirão a duração da reprodução definida na configuração do nível Canal. Qualquer imagem individual ainda pode substituir o padrão e ter uma duração de reprodução diferente. Isso é feito ao editar a duração da reprodução do componente de imagem específico.

### Pré-requisitos {#prerequisites}

Antes de implementar essa funcionalidade, certifique-se de configurar um projeto como pré-requisito para começar a implementar essa funcionalidade. Por exemplo,

1. Crie um exemplo de projeto do AEM Screens, **ChannelLevelPlayback**.

1. Crie um canal de sequência como **PlaybackChannel** na pasta **Channels**.

1. Adicione conteúdo a **PlaybackChannel**.

## Editar Atribuição de Duração da Reprodução de Imagem no Nível do Canal {#editing-channel-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um canal do AEM Screens.

### Atualizar a duração da reprodução das imagens em um canal {#updating-the-playback-duration-for-images-in-a-channel}

Siga as etapas abaixo para saber como atualizar a Atribuição de duração da reprodução de imagem no nível do canal:

1. Navegue até o canal de sequência **PlaybackChannel**.

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. Clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. Adicione duas ou mais imagens no editor de canais, conforme mostrado na figura abaixo.

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. Selecione todas as imagens no canal e clique na chave inglesa no canto superior esquerdo (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar no nível do canal .

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **** A caixa de diálogo Pagedialog é aberta.

   >[!NOTE]
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duration** de 8000 (ms) para 3000 (ms), ou seja, 3 segundos. Clique na marca de seleção na parte superior direita da caixa de diálogo **Page** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Visualização do resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), você observará que as imagens agora serão reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

