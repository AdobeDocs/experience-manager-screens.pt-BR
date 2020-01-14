---
title: Duração da reprodução de imagem no nível do projeto
seo-title: Duração da reprodução de imagem no nível do projeto
description: 'Essa funcionalidade permite definir a duração da reprodução da imagem no nível do projeto. '
seo-description: 'Essa funcionalidade permite definir a duração da reprodução da imagem no nível do projeto. '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: ae1f7cab650f811ae03f0a2f3dfa49ec855997ee

---


# Duração da reprodução de imagem no nível do projeto {#project-level-image-playback}

## Visão geral {#overview}

Esse recurso permite definir a duração da reprodução da imagem no nível do projeto. Todas as imagens herdam a duração desta reprodução por padrão. Se nenhuma duração for definida no nível do projeto, a reprodução padrão de 8 segundos continuará.

### Pré-requisitos {#prerequisites}

Antes de usar esse recurso, certifique-se de configurar um projeto como pré-requisito para iniciar a implementação dessa funcionalidade. Por exemplo,

1. Criar um projeto do AEM Screens (neste exemplo, **ProjectLevelPlayback**)

1. Criar um canal de sequência como **PlayBackChannel** na pasta **Canais**

1. Adicionar conteúdo ao **PlayBackChannel**

   ![ativos](assets/image_playback1.png)

   Por exemplo, a imagem a seguir mostra as imagens adicionadas ao editor **PlayBackChannel** :

   ![ativos](assets/image_playback2.png)

## Edição da Atribuição de Duração da Reprodução de Imagem no Nível do Projeto {#editing-project-level-image-playback-duration-assignment}

A seção abaixo explica como editar a duração da reprodução do conteúdo em um projeto do AEM Screens.

### Atualizando a duração da reprodução de imagens no nível do projeto {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>Se quiser atualizar a duração da reprodução em nível de imagem ou canal, consulte a Duração [da reprodução de imagem em nível de](channel-level-image-playback.md)canal.

Siga as etapas abaixo para saber como atualizar a Duração da reprodução de imagem no nível do projeto:

1. Navigate to your project **ProjectLevelPlayback** and click **Properties** from the action bar.
   ![ativos](assets/image_playback3.png)

1. Selecione todas as imagens no canal e clique no ícone de chave inglesa no canto superior esquerdo (como mostrado na figura abaixo) para abrir a caixa de diálogo Configurar no nível do canal.

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **A caixa de diálogo Página** é aberta.

   >[!NOTE]
   >
   >Por padrão, as imagens em um canal são definidas com uma duração de reprodução de 8 segundos e os vídeos são reproduzidos com sua duração padrão.

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   Edite a **Duração** de 8000 (ms) a 3000 (ms), ou seja, 3 segundos. Clique na marca de seleção na parte superior direita da caixa de diálogo **Página** para salvar as alterações.

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### Como visualizar o resultado {#viewing-the-result}

Depois de atualizar a duração da reprodução do canal (neste exemplo, todas as três imagens), você observará que as imagens serão reproduzidas por 3 segundos em vez de 8 segundos (valor padrão).

![channel_preview](assets/channel_preview.gif)

