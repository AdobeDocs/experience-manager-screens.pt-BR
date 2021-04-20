---
title: Sequências incorporadas
seo-title: Sequências incorporadas
description: Siga esta página para saber mais sobre sequências incorporadas para canais que permitem ao usuário adicionar componentes no canal pai e também reutilizar o conteúdo de um canal diferente e incorporá-lo ao canal pai.
seo-description: Siga esta página para saber mais sobre sequências incorporadas para canais que permitem ao usuário adicionar componentes no canal pai e também reutilizar o conteúdo de um canal diferente e incorporá-lo ao canal pai.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 43%

---


# Sequências incorporadas {#embedded-sequences}

Usar ***Sequências incorporadas***, para canais, permite que o usuário adicione componentes ao canal pai e também reutilize o conteúdo de um canal diferente e incorpore-o ao canal pai.

## Adição de sequências incorporadas {#adding-embedded-sequences}

Você tem a opção de adicionar os seguintes componentes ao seu canal de sequência:

* Sequência incorporada
* Sequência incorporada dinâmica

>[!NOTE]
>
>Para aprender a usar outros componentes no seu projeto do Screens, consulte [Adição de componentes a um canal](adding-components-to-a-channel.md).

### Adição de uma sequência incorporada {#adding-an-embedded-sequence}

Você pode adicionar uma sequência incorporada ao seu canal. Uma sequência incorporada é outro canal que inclui ativos como imagens ou vídeos. A adição de uma sequência incorporada permite que o usuário adicione a sequência a um canal por ***Caminho do canal***.

>[!NOTE]
>***Caminho do canal*** define uma referência explícita ao canal.
>Para saber mais sobre *Caminho do canal*, consulte [Atribuição de canal](channel-assignment.md) na seção sobre criação da documentação do Screens.

Siga as etapas abaixo para adicionar uma sequência incorporada ao seu canal:

1. Selecione o canal em que você deseja incorporar uma página. Por exemplo, **We.Retail In-Store** —> **Canais** —> **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o canal no modo de editor.
1. Clique no ícone de componentes na barra lateral esquerda para adicionar a página incorporada. Arraste e solte o **Embedded Sequence** no editor.
1. Clique duas vezes no componente **Sequência incorporada** para adicionar o canal ao seu canal de sequência original.
1. Selecione o **Caminho do canal.**
1. Selecione **Duration (ms)** para seu canal incorporado na guia **Sequence**. Por padrão, a duração é definida como **-1**, o que significa que o canal incorporado é totalmente executado. Se o usuário especificar uma duração, a subsequência será interrompida (ou seja, será cortada) no tempo especificado.

1. Defina a **Estratégia de reprodução medida** para **normal**.

Por padrão, ele é definido como **normal**. Definir o valor como **normal** (Reproduzir todos os itens) significa que a subsequência será totalmente executada em cada ciclo da sequência pai. O outro valor possível é **Reproduzir um único item** (Reproduzir um único item) e que mostraria apenas um item da subsequência em cada execução (por exemplo, o primeiro item no primeiro loop, o segundo item no segundo loop e assim por diante).

>[!IMPORTANT]
>
>Você deve atribuir o canal (usado em sequência incorporada), à mesma exibição.
>
>Siga as etapas abaixo após adicionar uma sequência incorporada ao seu canal a partir das etapas anteriores:
>
>1. Navegue até a exibição e selecione a exibição da pasta **Localizações**.
>1. Clique em **Dashboard** na barra de ações para navegar até o painel de exibição.
>1. Selecione **+ Atribuir canais** a partir de **CANAIS ATRIBUÍDOS E PAINÉIS AGENDADOS** para abrir a caixa de diálogo **Atribuição de canal**.

   >
   >
1. Selecione o caminho do canal (usado em sequência incorporada) em **Caminho do Canal**.
>1. Certifique-se de que a **Priority** seja inferior ao canal principal.

   >
   >
1. Você não deve selecionar **Eventos Suportados**.
>1. Clique em **Salvar** uma vez concluído.

>



O exemplo a seguir mostra a adição de uma sequência incorporada (**Canal ocioso - Noite**) a um canal já existente (**Canal ocioso**).

![new2](assets/new2.gif)

### Adição de uma sequência incorporada dinâmica {#adding-a-dynamic-embedded-sequence}

Você pode adicionar uma sequência incorporada dinâmica ao seu canal. Uma sequência incorporada dinâmica é semelhante a uma sequência incorporada, mas permite que o usuário siga uma hierarquia em que as alterações/atualizações feitas em um canal sejam propagadas para o outro usuário. Ela segue a hierarquia pai/filho e também inclui ativos como imagens ou vídeos. Adicionar uma sequência dinâmica permite que o usuário adicione um canal por função de canal.

>[!NOTE]
>
>***Função do canal*** define o contexto da exibição.
>
>Para saber mais sobre *Função do canal*, consulte [Atribuição de canal](channel-assignment.md) na seção sobre criação da documentação do Screens.

Siga as etapas abaixo para adicionar uma sequência incorporada ao seu canal:

1. Selecione o canal em que você deseja incorporar uma sequência dinâmica. Por exemplo, **We.Retail In-Store** —> **Canais** —> **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o canal no modo de editor.
1. Clique no ícone de componentes na barra lateral esquerda para adicionar a sequência incorporada dinâmica. Arraste e solte o **Dinâmico** **Sequência incorporada** no editor.

1. Clique duas vezes no componente **Dinâmico** **Sequência incorporada** para adicionar a página ao seu canal de sequência.

1. Insira a **Função de Atribuição de Canal**.
1. Defina a **Estratégia de reprodução medida** para **normal**. Por padrão, ele é definido como **normal**. Definir o valor como **normal** (Reproduzir todos os itens) significa que a subsequência será totalmente executada em cada ciclo da sequência pai. O outro valor possível é **Reproduzir um único item** (Reproduzir um único item) e que mostraria apenas um item da subsequência em cada execução (por exemplo, o primeiro item no primeiro loop, o segundo item no segundo loop e assim por diante).

1. Selecione a guia **Duration (ms)** em **Sequence** para seu canal incorporado na sequência.

![mais recente](assets/latest.gif)

