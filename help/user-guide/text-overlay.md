---
title: Sobreposição de texto
seo-title: Sobreposição de texto
description: A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta sobre uma imagem. Siga esta página para saber mais.
seo-description: A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta sobre uma imagem. Siga esta página para saber mais.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Sobreposição de texto {#text-overlay}

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Uso da sobreposição de texto**
* **Pré-requisitos**
* **Como entender as propriedades da sobreposição de texto**

>[!CAUTION]
>
>O recurso Sobreposição **de** texto só estará disponível se você tiver instalado o AEM 6.3 Feature Pack 5 ou o AEM 6.4 Feature Pack 3.

## Visão geral {#overview}

A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta sobre uma imagem.

Para saber como criar seu próprio componente personalizado, consulte **Extensão de um componente** do AEM Screens.

Esta seção só mostra como usar e aproveitar o componente de pôster em um projeto do AEM Screens e usá-lo como sobreposição de texto em um de seus canais de sequência.

## Uso da sobreposição de texto {#using-text-overlay}

A seção a seguir descreve o uso de sobreposição de texto em um projeto do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, certifique-se de configurar um projeto como pré-requisito para iniciar a implementação da sobreposição de texto. Por exemplo,

* Criar um projeto do AEM Screens (neste exemplo, **TextOverlayDemo**)

* Criar um canal como **TextSample** na pasta **Canais**

* Adicionar conteúdo ao seu Canal **de amostra** de texto

A imagem a seguir mostra o projeto **TextOverlayDemo** com o canal **TextSample** na pasta **Canais** .

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

1. Navegue até **TextOverlayDemo** —&gt; **Channels** —&gt; **TextSample** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Selecione a imagem e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo de propriedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Selecione a opção Sobreposição **** de texto na barra de navegação da caixa de diálogo, conforme mostrado na figura abaixo.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Como entender as propriedades da sobreposição de texto {#understanding-text-overlay-properties}

Usando as propriedades de Sobreposição de texto, é possível adicionar texto a qualquer um dos componentes do projeto do Screens. A seção a seguir fornece uma visão geral das propriedades que estão disponíveis em Sobreposição de texto:

![text](assets/text.gif)

É possível adicionar um texto à caixa de texto e adicionar ênfase tipográfica, como negrito, itálico, sublinhado e assim por diante.

**Variante** de cor Essa opção permite que o texto seja escuro (texto em preto) ou claro (texto em branco).

**Dimensionamento e posicionamento** Essa opção permite que o usuário alinhe o texto horizontal ou verticalmente ou, adicionalmente, use ferramentas de granulado fino para alinhamento de texto.

>[!NOTE]
>
>Para usar corretamente ferramentas de granulado fino, identifique a posição correta em pixels usando (px) como sufixo, por exemplo 200px. O resultado dessa expressão será de 200 pixels a partir do ponto inicial.

