---
title: Duração da reprodução de imagem em massa no nível do canal
description: Saiba como editar a duração da reprodução de um componente de imagem específico no AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Duração da reprodução de imagem em massa no nível do canal {#channel-level-bulk-image-playback-duration}

## Visão geral {#overview}

Ao criar um canal de sequência e adicionar imagens a ele, por padrão, todas as imagens assumem a duração da reprodução definida na configuração Nível de canal. Qualquer imagem individual ainda pode substituir o padrão e ter uma duração de reprodução diferente; isso é feito ao editar a duração de reprodução do componente de imagem específico.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você configurou um projeto como pré-requisito para começar a implementá-la. Por exemplo,

1. Criar um exemplo de projeto do AEM Screens, **ChannelLevelPlayback**.

1. Criar um canal de sequência como **PlaybackChannel** em **Canais** pasta.

1. Adicionar conteúdo a **PlaybackChannel**.

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

1. Selecione todas as imagens no canal e selecione o ícone de chave inglesa no canto superior esquerdo (como mostrado na figura abaixo) para que você possa abrir a caixa de diálogo Configurar nível de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. A variável **Página** é aberta.

   >[!NOTE]
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duração** de 8000 (milissegundos) a 3000 (milissegundos), ou seja, 3 segundos. Selecione a marca de seleção na parte superior direita do **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), observe que as imagens agora são reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)
