---
title: Criação e gerenciamento de uma Live Copy
seo-title: Gerenciar a LiveCopy
description: Esta página descreve como criar e gerenciar Live Copies de canais.
seo-description: Siga esta página para criar uma live copy de um canal, exibir as propriedades, verificar o status e propagar as alterações de um canal para sua live copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Criação e gerenciamento de uma Live Copy {#creating-and-managing-a-live-copy}

Esta página descreve como criar e gerenciar Live Copies de canais.

A ***Live Copy*** is a copy of specific site content for which a live relationship with the original source is maintained. Este relacionamento dinâmico permite que a live copy herde as propriedades do conteúdo e da página de origem.

Esta página descreve como criar uma live copy de um canal, exibir as propriedades, verificar o status e propagar as alterações de um canal para sua live copy.


## Criação de uma Live Copy {#creating-a-live-copy}

Siga as etapas abaixo para criar uma live copy de um canal na pasta do projeto.

1. Selecione o link do Adobe Experience Manager (parte superior esquerda) e o **Screens**. Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.

1. Navegue até o projeto do Screens e clique em **Canais**.
1. Click **Create** and select **Live Copy** to create a live copy of the channel.

1. Selecione o destino e clique em **Próximo**.
1. Selecione a localização da live copy.
1. Insira o **Título** e o **Nome** na página **Criar Live Copy**.

1. Clique em **Abrir** para exibir os conteúdos da nova live copy ou em **Concluído** para retornar à página principal.

Como alternativa, consulte as etapas abaixo para ver a representação visual da criação de uma nova Live Copy de um canal.

The following example shows the creation of a live copy (***IdleLiveCopy***) for ***Idle Channel*** with destination folder as ***Channels***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Exibir o conteúdo do canal da live copy {#viewing-content-of-the-live-copy-channel}

Uma Live Copy é uma cópia de um canal que já existe.

Para exibir o conteúdo da live copy, siga as seguintes etapas:

1. Navegue até o projeto do Screens e clique no local onde você criou originalmente a live copy, conforme mostrado na seção acima. (Here, the location was chosen as **Channels** folder)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Clique em **Editar** na barra de ações para exibir o conteúdo no canal.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Quando visualiza o conteúdo de um canal de live copy, você vê um item adicional no menu definido como **Status da Live Copy**. Consulte a seção abaixo para obter mais detalhes.

### Exibir as propriedades de uma live copy {#viewing-properties-of-a-live-copy}

Além disso, é possível exibir as propriedades do seu canal Live Copy.

1. Navegue até o canal da live copy e clique em **Propriedades** na barra de ações.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Selecione a guia **Live Copy** para exibir os detalhes do canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Status da Live Copy {#live-copy-status}

O modo** Live Copy Status**, conforme mostrado na figura abaixo, permite que você veja o status do relacionamento de todos os ativos no canal.

1. Click **Edit** to choose the **Live Copy Status** and view the association of your channel content to the original channel (from which the live copy is generated).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Selecione **Status da Live Copy** para exibir a página de visualização.

   Todos os recursos com borda verde mostram que o conteúdo foi herdada do canal original.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Interromper a herança {#breaking-the-inheritance}

Também é possível cancelar a herança da livecopy para tornar o conteúdo independente da ramificação original.

O exemplo a seguir mostra que você seleciona a imagem no modo de edição e clica no símbolo para cancelar a herança na parte superior direita.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagar as alterações ao canal da live copy {#propagating-changes-to-the-live-copy-channel}

Se você fizer alterações/atualizações no canal original, também será necessário propagar essas alterações no canal da Live Copy.

Siga as etapas abaixo para garantir que as alterações sejam propagadas do canal original ao canal da live copy:

1. Selecione o canal original (***Canal inativo***) e clique em **Editar** na barra de ações.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Edite esse conteúdo de canal. Por exemplo, exclua uma imagem deste canal.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Selecione a live copy do canal (***IdleLiveCopy***) e clique em **Editar** na barra de ações. Você notará que a imagem excluída ainda está visível na live copy.

   Para propagar as alterações, é necessário sincronizar o canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Para propagar alterações no canal da live copy, navegue até o painel do AEM, selecione o canal da live copy e clique em **Propriedades** na barra de ações.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Selecione a guia **Live Copy** e clique em **Sincronizar** na barra de ações.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Clique em **Sincronizar** para confirmar as alterações. Click **Save &amp; Close** to navigate back to the AEM dashboard..

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Você notará que a imagem também foi excluída do canal da live copy.
