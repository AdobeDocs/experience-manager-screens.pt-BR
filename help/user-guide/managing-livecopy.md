---
title: Criação e gerenciamento de uma Live Copy
seo-title: Managing LiveCopy
description: Esta página descreve a criação e o gerenciamento de Live Copies de canais.
seo-description: Follow this page to create live copy of a channel, view properties, check status, and propagate changes from a channel to its live copy.
uuid: 78ec7219-95ab-44d1-9514-1b97aded5bf4
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 84085a03-1798-4f1d-858c-6014a3f6aff6
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 4a4b3a83-2b02-42a0-86a7-fce6bbf47c7d
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 1%

---

# Criação e gerenciamento de uma Live Copy {#creating-and-managing-a-live-copy}

Esta página descreve a criação e o gerenciamento de Live Copies de canais.

A ***Live Copy*** é uma cópia do conteúdo específico do site para o qual é mantido um relacionamento dinâmico com a origem original. Esse relacionamento dinâmico permite que a live copy herde conteúdo e propriedades de página da origem.

Esta página descreve a criação e a propagação de uma live copy de um canal, a exibição de propriedades, a verificação de status e a propagação de alterações de um canal para sua live copy.


## Criação de uma Live Copy {#creating-a-live-copy}

Siga as etapas abaixo para criar uma Live Copy de um canal na pasta do projeto.

1. Selecione o link Adobe Experience Manager (canto superior esquerdo) e **Screens**. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.

1. Navegue até o projeto do Screens e clique em **Canais**.
1. Clique em **Criar** e selecione **Live Copy** para criar uma live copy do canal.

1. Selecione o destino e clique em **Próxima**.
1. Selecione o local em que a live copy ficará.
1. Insira o **Título** e **Nome** no **Criar Live Copy** página.

1. Clique em **Abertura** para exibir o conteúdo da nova live copy ou **Concluído** para retornar à página principal.

Como alternativa, consulte as etapas abaixo para obter representação visual para criar uma nova live copy de um canal.

O exemplo a seguir mostra a criação de uma live copy (***IdleLiveCopy***) para ***Canal ocioso*** com a pasta de destino como ***Canais***.

![chlimage_1-2](assets/chlimage_1-2.gif)

## Exibição de conteúdo do canal da Live Copy {#viewing-content-of-the-live-copy-channel}

Uma Live Copy é uma cópia de um canal que já existe.

Para exibir o conteúdo da live copy, consulte as etapas abaixo:

1. Navegue até o projeto do Screens e clique no local em que você criou a live copy originalmente, como mostrado na seção acima. (Aqui, a localização foi escolhida como **Canais** pasta)

   ![chlimage_1-18](assets/chlimage_1-18.png)

1. Clique em **Editar** na barra de ações para exibir o conteúdo no canal.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   >[!NOTE]
   >
   >Ao visualizar o conteúdo de um canal de live copy, você verá um item extra no menu como **Status da Live Copy**. Consulte a seção abaixo para obter mais detalhes.

### Visualização de propriedades de uma Live Copy {#viewing-properties-of-a-live-copy}

Além disso, é possível visualizar as propriedades do canal da live copy.

1. Navegue até o canal da live copy e clique em **Propriedades** na barra de ações.

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Selecione o **Live Copy** para exibir detalhes do seu canal.

   ![chlimage_1-21](assets/chlimage_1-21.png)

### Status da Live Copy   {#live-copy-status}

O modo **Status da Live Copy**, como mostrado na figura abaixo, permite visualizar o status do relacionamento de todos os ativos no canal.

1. Clique em **Editar** para escolher o **Status da Live Copy** e visualizam a associação do conteúdo do canal ao canal original (do qual a live copy é gerada).

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Selecionar **Status da Live Copy** para exibir a página de visualização.

   Todos os recursos com borda verde mostram que o conteúdo é herdado do canal original.

   ![chlimage_1-23](assets/chlimage_1-23.png)

### Interromper a herança {#breaking-the-inheritance}

Você também pode cancelar a herança da live copy, para que o conteúdo se torne independente da ramificação original.

O exemplo a seguir mostra como selecionar a imagem no modo de edição e clicar no símbolo de herança de cancelamento na parte superior direita.

![chlimage_1-24](assets/chlimage_1-24.png)

### Propagação de alterações no canal da Live Copy {#propagating-changes-to-the-live-copy-channel}

Se você fizer alterações/atualizações no canal original, será necessário propagar essas alterações para o canal da Live Copy também.

Siga as etapas abaixo para garantir que as alterações sejam propagadas do canal original para o canal de live copy:

1. Selecione o canal original (***Canal ocioso***) e clique em **Editar** na barra de ações.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Faça edições no conteúdo deste canal. Por exemplo, exclua uma imagem deste canal.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Selecione a live copy do canal (***IdleLiveCopy***) e clique em **Editar** na barra de ações. Você observará que a imagem excluída ainda está visível na live copy.

   Para propagar as alterações, é necessário sincronizar o canal.

   ![chlimage_1-27](assets/chlimage_1-27.png)

1. Para propagar alterações no canal da live copy, navegue até o painel AEM, selecione o canal da live copy e clique em **Propriedades** na barra de ações.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Selecione o **Live Copy** e clique em **Sincronizar** na barra de ações.

   ![chlimage_1-29](assets/chlimage_1-29.png)

1. Clique em **Sincronizar** para confirmar as alterações. Clique em **Salvar e fechar** para voltar para o painel AEM.

   ![chlimage_1-30](assets/chlimage_1-30.png)

   Você observará que a imagem agora também foi excluída do canal da live copy.
