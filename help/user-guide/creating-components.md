---
title: Criar componentes
seo-title: Creating Components
description: Os componentes do AEM são usados para reter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web. Siga esta página para saber mais sobre a criação de canais e a renderização de componentes.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages. Follow this page to learn about authoring channels and rendering components.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 3%

---

# Criar componentes {#creating-components}

Os componentes do AEM são usados para reter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web.

>[!NOTE]
>
>Para saber mais sobre os detalhes da criação de componentes do AEM, consulte Desenvolvimento de componentes do AEM.

## Criação de canais {#authoring-channels}

O canal é o objeto central do conteúdo entregue a um conjunto de exibições. Portanto, um autor de conteúdo normalmente abriria um canal no editor para adicionar ou modificar conteúdo. Como o Canal é um ***cq:Page*** ele seguirá o mesmo padrão de UX tradicional para adicionar e alterar componentes no canal.

No entanto, como os componentes em um canal normalmente são renderizados em tela cheia, a experiência de criação sofrerá ao tentar editar componentes únicos ou compor novos pedidos. Portanto, o canal dependerá de seletores para renderizar diferentes visualizações dos componentes. O ambiente de criação aproveitará o seletor de edição para ativar a renderização do canal personalizado.

Por exemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

O usuário não precisa cuidar da adição do seletor ao URL durante a edição. Uma lógica do lado do cliente escuta o evento de alternância de camadas e adiciona o seletor se um canal tiver o tipo de recurso dedicado *telas/núcleo/componentes/canal.*

## Componentes de renderização {#rendering-components}

Para ativar a criação adequada, os componentes precisam fornecer as duas renderizações a seguir:

| **Componente** | **Representações** |
|---|---|
| *my-component/my-component.html* | renderização de produção |
| *my-component/edit.html* | edição da renderização em uma exibição menor |

Os componentes integrados usam as seguintes categorias de bibliotecas de clientes:

| **Componente** | **Biblioteca do cliente** |
|---|---|
| *cq.screens.components.edit* | CSS e JS que devem ser carregados durante a criação |
| *cq.screens.components.production* | CSS e JS que devem ser carregados quando o canal estiver em execução |
| *cq.screens.components* | CSS e JS compartilhados |

>[!NOTE]
>
>Para desenvolver componentes personalizados, use o ***[Modelo do componente de amostra do AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
