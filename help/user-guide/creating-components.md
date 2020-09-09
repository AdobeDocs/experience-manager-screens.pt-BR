---
title: Criação de componentes
seo-title: Criação de componentes
description: AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web. Siga esta página para saber mais sobre como criar canais e renderizar componentes.
seo-description: AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web. Siga esta página para saber mais sobre como criar canais e renderizar componentes.
uuid: 66c76dd5-495a-4dcb-ad18-7f8a92669752
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: cdc530d8-ef0e-4b61-b1f0-5f4d831f1392
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---


# Criação de componentes {#creating-components}

AEM componentes são usados para manter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web.

>[!NOTE]
>
>Para saber mais sobre os detalhes da criação de componentes AEM, consulte Desenvolvimento de componentes AEM.

## Criação de Canais {#authoring-channels}

O canal é o objeto central do conteúdo entregue a um conjunto de exibições. Portanto, um autor de conteúdo normalmente abriria um canal no editor para adicionar ou modificar conteúdo. Como o Canal é um ***cq:Page*** , ele seguirá o mesmo padrão UX tradicional para adicionar e alterar componentes no canal.

No entanto, como os componentes dentro de um canal normalmente são renderizados em tela cheia, a experiência de criação sofrerá ao tentar editar componentes únicos ou compor novos pedidos. Portanto, o canal dependerá de seletores para renderizar visualizações diferentes dos componentes. O ambiente de criação aproveitará o seletor de edição para ativar a renderização personalizada do canal.

Por exemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

O usuário não precisa adicionar o seletor ao URL durante a edição. Uma lógica do lado do cliente está ouvindo o evento de switch de camada e adiciona o seletor se o canal tiver *telas de tipo de recurso dedicado/núcleo/componentes/canal.*

## Componentes de renderização {#rendering-components}

Para habilitar a criação adequada, os componentes precisam fornecer as duas renderizações a seguir:

| **Componente** | **Representações** |
|---|---|
| *my-component/my-component.html* | renderização de produção |
| *my-component/edit.html* | edição da renderização em uma visualização menor |

Os componentes incorporados aproveitam as seguintes categorias da biblioteca do cliente:

| **Componente** | **Biblioteca do cliente** |
|---|---|
| *cq.screens.components.edit* | CSS e JS que devem ser carregados durante a criação |
| *cq.screens.components.production* | CSS e JS que devem ser carregados quando o canal estiver em execução |
| *cq.screens.components* | CSS e JS compartilhados |

>[!NOTE]
>
>Para desenvolver componentes personalizados, use o ***modelo[de componente de amostra da](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)AEM Screens***.

