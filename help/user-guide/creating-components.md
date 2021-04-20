---
title: Criar componentes
seo-title: Criar componentes
description: AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado nas suas páginas da Web. Siga esta página para saber mais sobre criação de canais e renderização de componentes.
seo-description: AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado nas suas páginas da Web. Siga esta página para saber mais sobre criação de canais e renderização de componentes.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---


# Criar componentes {#creating-components}

AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado nas suas páginas da Web.

>[!NOTE]
>
>Para saber mais sobre os detalhes da criação dos Componentes do AEM, consulte Desenvolvimento dos Componentes do AEM.

## Canais de criação {#authoring-channels}

O canal é o objeto central do conteúdo fornecido para um conjunto de exibições. Portanto, um autor de conteúdo normalmente abriria um canal no editor para adicionar ou modificar o conteúdo. Como o Canal é um ***cq:Page*** ele seguirá o mesmo padrão UX tradicional para adicionar e alterar componentes no canal.

No entanto, como os componentes em um canal normalmente são renderizados em tela cheia, a experiência de criação será afetada ao tentar editar componentes únicos ou compor novos pedidos. Portanto, o canal dependerá dos seletores para renderizar diferentes exibições dos componentes. O ambiente de criação aproveitará o seletor de edição para ativar a renderização de canal personalizado.

Por exemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

O usuário não precisa adicionar o seletor ao URL durante a edição. Uma lógica do lado do cliente está ouvindo o evento de troca de camada e adiciona o seletor se um canal tiver o tipo de recurso dedicado *screens/core/components/channel.*

## Componentes de renderização {#rendering-components}

Para ativar a criação adequada, os componentes precisam fornecer as duas renderizações a seguir:

| **Componente** | **Representações** |
|---|---|
| *my-component/my-component.html* | renderização de produção |
| *my-component/edit.html* | edição da renderização em uma exibição menor |

Os componentes incorporados aproveitam as seguintes categorias da biblioteca do cliente:

| **Componente** | **Biblioteca do cliente** |
|---|---|
| *cq.screens.components.edit* | CSS e JS que devem ser carregados durante a criação |
| *cq.screens.components.production* | CSS e JS que devem ser carregados quando o canal estiver em execução |
| *cq.screens.components* | CSS e JS compartilhados |

>[!NOTE]
>
>Para desenvolver componentes personalizados, use o ***[modelo de componente de amostra do AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.

