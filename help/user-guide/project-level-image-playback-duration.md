---
title: Duração da reprodução da imagem no nível do projeto
description: Saiba como definir a duração da reprodução de imagem no nível do projeto.
contentOwner: jsyal
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 1%

---


# Duração da reprodução da imagem no nível do projeto {#project-level-image-playback}

## Visão geral {#overview}

Esse recurso permite definir a duração da reprodução da imagem no nível do projeto. Todas as imagens herdam essa duração de reprodução por padrão. Se nenhuma duração for definida no nível do projeto, a reprodução padrão de 8 segundos continuará.

### Pré-requisitos {#prerequisites}

Antes de usar esse recurso, configure um projeto como pré-requisito para começar a implementar essa funcionalidade. Por exemplo,

1. Criar um projeto do AEM Screens (neste exemplo, **ReproduçãoEmNívelDeProjeto**).
1. Criar um canal de sequência como **PlayBackChannel** em **Canais** pasta.
1. Adicionar conteúdo a **PlayBackChannel**.

   ![ativos](assets/image_playback1.png)

   Por exemplo, a imagem a seguir mostra as imagens adicionadas à variável **PlayBackChannel** editor:

   ![ativos](assets/image_playback2.png)

## Editar atribuição de duração da reprodução da imagem no nível do projeto {#editing-project-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um projeto do AEM Screens.

### Atualização da duração da reprodução de imagens no nível do projeto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Se quiser atualizar a duração da reprodução de uma imagem ou de um canal, consulte [Duração da reprodução da imagem no nível do canal](channel-level-image-playback.md).

Siga as etapas abaixo para saber como atualizar a Duração da reprodução da imagem no nível do projeto:

1. Navegar até o projeto **ReproduçãoEmNívelDeProjeto** e clique em **Propriedades** na barra de ações.
   ![ativos](assets/image_playback3.png)

1. Clique em todas as imagens no canal e clique no ícone da chave inglesa no canto superior esquerdo (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar nível de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. A variável **Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos e os vídeos são reproduzidos com a duração padrão.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duração** de 8000 (milissegundos) a 3000 (milissegundos), ou seja, 3 segundos. Selecione a marca de seleção no canto superior direito da **Página** para que suas alterações sejam salvas.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), observe que as imagens agora são reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

