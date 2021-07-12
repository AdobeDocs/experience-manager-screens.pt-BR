---
title: Sobreposição de texto
seo-title: Sobreposição de texto
description: A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta a uma imagem. Siga esta página para saber mais.
seo-description: A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta a uma imagem. Siga esta página para saber mais.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Telas de criação
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 3%

---

# Sobreposição de texto {#text-overlay}

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Uso da sobreposição de texto**
* **Como entender as propriedades de sobreposição de texto**
* **Uso dos valores do ContextHub na sobreposição de texto**

>[!CAUTION]
>
>O recurso **Sobreposição de texto** só estará disponível se você tiver instalado AEM Pacote de recursos 6.3 5 ou AEM 6.4 Feature Pack 3.

## Visão geral {#overview}

A sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um Canal de sequência fornecendo um título ou uma descrição sobreposta a uma imagem.

Para saber como criar seu próprio componente personalizado, consulte **Extensão de um componente do AEM Screens**.

Esta seção mostra apenas como usar e aproveitar o componente de pôster em um projeto do AEM Screens e usá-lo como sobreposição de texto em um de seus canais de sequência.

## Uso da sobreposição de texto {#using-text-overlay}

A seção a seguir descreve o uso de sobreposição de texto em um projeto do AEM Screens.

**Pré-requisitos**

Antes de implementar essa funcionalidade, certifique-se de configurar um projeto como pré-requisito para iniciar a implementação da sobreposição de texto. Por exemplo,

* Crie um projeto do AEM Screens (neste exemplo, **TextOverlayDemo**)

* Crie um canal de sequência chamado **TextSample** na pasta **Channels**

* Adicionar conteúdo ao seu canal **TextSample**

A imagem a seguir mostra o projeto **TextOverlayDemo** com o canal **TextSample** na pasta **Channels**.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Siga as etapas abaixo para usar a sobreposição de texto em um canal AEM Screens:

1. Navegue até **TextOverlayDemo** —> **Canais** —> **TextSample** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Selecione a imagem e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Selecione a opção **Sobreposição de texto** na barra de navegação da caixa de diálogo, conforme mostrado na figura abaixo.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Como entender as propriedades de sobreposição de texto {#understanding-text-overlay-properties}

Usando as propriedades de Sobreposição de texto, você pode adicionar texto a qualquer um dos componentes do seu projeto do Screens. A seção a seguir fornece uma visão geral das propriedades que estão disponíveis em Sobreposição de texto:

![text](assets/text.gif)

É possível adicionar um texto à caixa de texto e adicionar ênfase tipográfica, como negrito, itálico, sublinhado e assim por diante.

**Variante** de corEssa opção permite que o texto seja escuro (texto em cor preta) ou claro (texto em cor branca).

**Dimensionamento e** posicionamento Essa opção permite que o usuário alinhe o texto horizontal ou verticalmente ou, adicionalmente, usa ferramentas de granularidade fina para alinhamento do texto.

>[!NOTE]
>
>Para usar corretamente as ferramentas otimizadas, certifique-se de identificar a posição correta em pixels usando (px) como um sufixo, por exemplo, 200px. O resultado dessa expressão será 200 pixels a partir do ponto inicial.

## Uso dos valores do ContextHub na sobreposição de texto {#using-text-overlay-context-hub}

A seção a seguir descreve o uso de valores de um armazenamento de dados, por exemplo, o google sheets no componente de sobreposição de texto.

**Pré-requisitos**

Você deve configurar as configurações do ContextHub para o seu projeto do AEM Screens.

Para saber como configurar e gerenciar alterações de ativos orientados por dados usando um armazenamento de dados, consulte [Configuração do ContextHub no AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Depois de configurar as configurações necessárias para o seu projeto, siga as etapas abaixo para usar valores das planilhas do google:

1. Navegue até **TextOverlayDemo** —> **Canais** —> **TextSample** e clique em **Propriedades** na barra de ações.

1. Selecione a guia **Personalization** para configurar as configurações do ContextHub.

   1. Selecione o **Caminho do ContextHub** como **libs** > **configurações** > **cloudsettings** > **padrão** > **Configurações do ContextHub** e clique em &lt;a1 Selecione **.**

   1. Selecione o **Caminho de segmentos** como **conf** > **screens** > **definições** > **wcm** > **segmentos** e clique em **Selecionar&lt;a1 3/>.**

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      >
      >Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Navegue até **TextOverlayDemo** —> **Canais** —> **TextSample** e clique em **Editar** na barra de ações para abrir o editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Adicione um componente de sobreposição de imagem e texto à imagem, conforme descrito na seção [Uso da sobreposição de texto](/help/user-guide/text-overlay.md#using-text-overlay) desta página.

1. Clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo **Imagem**.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Navegue até a guia **ContextHub** na caixa de diálogo **Image**. Clique em **Adicionar**.

   >[!NOTE]
   >Se você não tiver configurado as configurações do ContextHub, essa opção será desativada para o seu projeto.

1. Insira **Value** no campo **Placeholder**, selecione a linha que deseja obter o valor da planilha do google em **Variável ContextHub** (nesse caso, o valor é recuperado da linha 2 e da coluna 1 das planilhas do google) e insira o **Valor padrão** como **20**, conforme mostrado na figura abaixo. Quando terminar, clique na marca de seleção.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Para sua referência, a imagem a seguir mostra o valor que é recuperado das planilhas do google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Navegue de volta à guia **Sobreposição de texto** da caixa de diálogo Imagem e adicione o texto *Temperatura atual {Valor}*, conforme mostrado na figura abaixo.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Clique em **Preview** para visualizar a saída desejada.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
