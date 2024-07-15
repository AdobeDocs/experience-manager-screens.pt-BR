---
title: Duração da reprodução da imagem no nível do projeto
description: Saiba como definir a duração da reprodução de imagem no nível do projeto.
contentOwner: jsyal
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---


# Duração da reprodução da imagem no nível do projeto {#project-level-image-playback}

## Visão geral {#overview}

Esse recurso permite definir a duração da reprodução da imagem no nível do projeto. Todas as imagens herdam essa duração de reprodução por padrão. Se nenhuma duração for definida no nível do projeto, a reprodução padrão de 8 segundos continuará.

### Pré-requisitos {#prerequisites}

Antes de usar esse recurso, configure um projeto como pré-requisito para começar a implementar essa funcionalidade. Por exemplo,

1. Crie um projeto do AEM Screens (neste exemplo, **ProjectLevelPlayback**).
1. Crie um canal de sequência como **PlayBackChannel** na pasta **Channels**.
1. Adicionar conteúdo a **PlayBackChannel**.

   ![ativos](assets/image_playback1.png)

   Por exemplo, a imagem a seguir mostra as imagens adicionadas ao editor **PlayBackChannel**:

   ![ativos](assets/image_playback2.png)

## Editar atribuição de duração da reprodução da imagem no nível do projeto {#editing-project-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um projeto do AEM Screens.

### Atualização da duração da reprodução de imagens no nível do projeto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Se quiser atualizar a duração da reprodução de uma imagem ou de um nível de canal, consulte [Duração da reprodução da imagem no nível de canal](channel-level-image-playback.md).

Siga as etapas abaixo para saber como atualizar a Duração da reprodução da imagem no nível do projeto:

1. Navegue até o projeto **ProjectLevelPlayback** e clique em **Propriedades** na barra de ações.
   ![ativos](assets/image_playback3.png)

1. Clique em todas as imagens no canal e clique no ícone da chave inglesa no canto superior esquerdo (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar nível de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. A caixa de diálogo **Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos e os vídeos são reproduzidos com a duração padrão.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite a **Duração** de 8000 (milissegundos) para 3000 (milissegundos), ou seja, 3 segundos. Marque a marca de seleção no canto superior direito da caixa de diálogo **Página** para salvar suas alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), observe que as imagens agora são reproduzidas por 3 segundos em vez de 8 segundos (o valor padrão).

![visualização_do_canal](assets/channel_preview.gif)

