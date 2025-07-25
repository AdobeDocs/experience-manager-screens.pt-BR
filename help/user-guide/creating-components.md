---
title: Criar componentes
description: Saiba mais sobre como os componentes do AEM são usados para manter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 4d673039-4963-458a-89e9-023a993dd354
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 1%

---

# Criar componentes {#creating-components}

Os componentes do AEM são usados para reter, formatar e renderizar o conteúdo disponibilizado em suas páginas da Web.

>[!NOTE]
>
>Para saber mais sobre os detalhes da criação de componentes do AEM, consulte Desenvolvimento de componentes do AEM.

## Canais de autor {#authoring-channels}

O canal é o objeto central do conteúdo entregue a um conjunto de exibições. Portanto, um Autor de conteúdo normalmente abriria um canal no editor para adicionar ou modificar conteúdo. Como o Canal é um ***`cq:Page`***, ele segue o mesmo padrão UX tradicional para adicionar e alterar componentes no canal.

No entanto, como os componentes em um canal normalmente são renderizados em tela cheia, a experiência de criação é afetada ao tentar editar componentes únicos ou compor novos pedidos. Portanto, o canal depende de seletores para renderizar diferentes visualizações dos componentes. O ambiente de criação usa o seletor `edit` para ativar a renderização do canal personalizado.

Por exemplo, `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

O usuário não precisa cuidar da adição do seletor ao URL durante a edição. Uma lógica do lado do cliente está escutando o evento de troca de camada e adiciona o seletor se o canal tiver o tipo de recurso dedicado *telas/núcleo/componentes/canal*.

## Renderizar componentes {#rendering-components}

Para ativar a criação adequada, os componentes devem fornecer as duas renderizações a seguir:

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
>Para desenvolver componentes personalizados, use o ***[modelo de componente de amostra do AEM Screens](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
