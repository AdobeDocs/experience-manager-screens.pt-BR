---
title: Duração da reprodução da imagem no nível do projeto
description: Saiba como definir a duração da reprodução de imagem no nível do projeto.
contentOwner: jsyal
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 1%

---


# Duração da reprodução da imagem no nível do projeto {#project-level-image-playback}

## Visão geral {#overview}

Esse recurso permite definir a duração da reprodução da imagem no nível do projeto. Todas as imagens herdam essa duração de reprodução por padrão. Se nenhuma duração for definida no nível do projeto, a reprodução padrão de 8 segundos continuará.

### Pré-requisitos {#prerequisites}

Antes de usar esse recurso, configure um projeto como pré-requisito para começar a implementar essa funcionalidade. Por exemplo,

1. Criar um projeto do AEM Screens (neste exemplo, **ReproduçãoEmNívelDeProjeto**)

1. Criar um canal de sequência como **PlayBackChannel** em **Canais** pasta

1. Adicionar conteúdo a **PlayBackChannel**

   ![ativos](assets/image_playback1.png)

   Por exemplo, a imagem a seguir mostra as imagens adicionadas à variável **PlayBackChannel** editor:

   ![ativos](assets/image_playback2.png)

## Editar atribuição de duração da reprodução da imagem no nível do projeto {#editing-project-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um projeto do AEM Screens.

### Atualização da duração da reprodução de imagens no nível do projeto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>Para atualizar a duração de uma reprodução em nível de imagem ou canal, consulte [Duração da reprodução da imagem no nível do canal](channel-level-image-playback.md).

Siga as etapas abaixo para saber como atualizar a Duração da reprodução da imagem no nível do projeto:

1. Navegar até o projeto **ReproduçãoEmNívelDeProjeto** e clique em **Propriedades** na barra de ações.
   ![ativos](assets/image_playback3.png)

1. Selecione todas as imagens no canal e clique no ícone da chave inglesa na parte superior esquerda (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar nível de canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos e os vídeos são reproduzidos com a duração padrão.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite o **Duração** de 8000 (ms) a 3000 (ms), ou seja, 3 segundos. Clique na marca de seleção na parte superior direita do **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Exibir o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), você notará que as imagens serão reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

