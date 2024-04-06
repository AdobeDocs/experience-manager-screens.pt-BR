---
title: Sobreposição de texto
seo-title: Text Overlay
description: A Sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um canal de sequência fornecendo um título ou uma descrição sobreposta sobre uma imagem. Siga esta página para saber mais.
seo-description: Text Overlay is a feature available in AEM Screens that allows you to create a compelling experience in a Sequence Channel by providing a title or a description overlaid on top of an image. Follow this page to learn more.
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

---

# Sobreposição de texto {#text-overlay}

Esta seção abrange os seguintes tópicos:

* **Visão geral**
* **Uso de sobreposição de texto**
* **Noções básicas sobre propriedades de sobreposição de texto**
* **Utilização de valores do ContextHub na sobreposição de texto**

>[!CAUTION]
>
>A variável **Sobreposição de texto** Este recurso só estará disponível se você tiver instalado o AEM 6.3 Feature Pack 5 ou o AEM 6.4 Feature Pack 3.

## Visão geral {#overview}

A Sobreposição de texto é um recurso disponível no AEM Screens que permite criar uma experiência atraente em um canal de sequência fornecendo um título ou uma descrição sobreposta sobre uma imagem.

Para saber como criar seu próprio componente personalizado, consulte **Extensão de um componente do AEM Screens**.

Esta seção mostra apenas como usar e aplicar o componente de pôster em um projeto do AEM Screens e usá-lo como sobreposição de texto em um de seus canais de sequência.

## Uso de sobreposição de texto {#using-text-overlay}

A seção a seguir descreve o uso de sobreposição de texto em um projeto do AEM Screens.

**Pré-requisitos**

Antes de começar a implementar essa funcionalidade, configure um projeto como pré-requisito para começar a implementar a sobreposição de texto. Por exemplo,

* Criar um projeto do AEM Screens (neste exemplo, **DemonstraçãoDeSobreposiçãoDeTexto**)

* Criar um canal de sequência com o título **TextSample** em **Canais** pasta

* Adicionar conteúdo ao seu **TextSample** Canal

A imagem a seguir mostra o **DemonstraçãoDeSobreposiçãoDeTexto** projeto com **TextSample** entrada de canal **Canais** pasta.

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

Siga as etapas abaixo para usar a sobreposição de texto em um canal do AEM Screens:

1. Navegue até **DemonstraçãoDeSobreposiçãoDeTexto** > **Canais** > **TextSample** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. Selecione a imagem e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. Selecione o **Sobreposição de texto** opção na barra de navegação da caixa de diálogo, conforme mostrado na figura abaixo.

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### Noções básicas sobre propriedades de sobreposição de texto {#understanding-text-overlay-properties}

Usando as propriedades de Sobreposição de texto, é possível adicionar texto a qualquer um dos componentes no projeto do Screens. A seção a seguir fornece uma visão geral das propriedades que estão disponíveis em Sobreposição de texto:

![texto](assets/text.gif)

É possível adicionar um texto à caixa de texto e adicionar ênfase tipográfica, como negrito, itálico e sublinhado.

**Variante de cor** Essa opção permite que o texto seja Escuro (texto na cor preta) ou Claro (texto na cor branca).

**Dimensionamento e posicionamento** Essa opção permite que o usuário alinhe o texto horizontal ou verticalmente ou também use ferramentas refinadas para alinhamento de texto.

>[!NOTE]
>
>Para usar ferramentas otimizadas corretamente, identifique a posição correta em pixels usando (px) como sufixo, por exemplo, 200 px. O resultado dessa expressão é 200 pixels a partir do ponto inicial.

## Utilização de valores do ContextHub na sobreposição de texto {#using-text-overlay-context-hub}

A seção a seguir descreve o uso de valores de um armazenamento de dados, por exemplo, google sheets em componente de sobreposição de texto.

**Pré-requisitos**

Defina as configurações do ContextHub para o seu projeto do AEM Screens.

Para saber como configurar e gerenciar alterações de ativos orientadas por dados usando um armazenamento de dados, consulte [Configuração do ContextHub no AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/configuring-context-hub.html).

Depois de definir as configurações necessárias para o seu projeto, siga as etapas abaixo para usar valores das planilhas do google:

1. Navegue até **DemonstraçãoDeSobreposiçãoDeTexto** > **Canais** > **TextSample** e clique em **Propriedades** na barra de ações.

1. Selecione o **Personalização** para definir as configurações do ContextHub.

   1. Selecione o **Caminho do ContextHub** as **libs** > **configurações** > **cloudsettings** > **padrão** > **Configurações do ContextHub** e clique em **Selecionar**.

   1. Selecione o **Caminho de segmentos** as **conf** > **telas** > **configurações** > **wcm** > **segmentos** e clique em **Selecionar**.

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      >
      >Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente as configurações e os segmentos do seu hub de contexto.

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. Navegue até **DemonstraçãoDeSobreposiçãoDeTexto** > **Canais** > **TextSample** e clique em **Editar** na barra de ações para abrir o editor.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. Adicione um componente de sobreposição de imagem e texto à imagem, conforme descrito em [Uso de sobreposição de texto](/help/user-guide/text-overlay.md#using-text-overlay) seção desta página.

1. Clique em **Configurar** (ícone de chave inglesa) para abrir a **Imagem** caixa de diálogo.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. Navegue até a **ContextHub** na guia **Imagem** caixa de diálogo. Clique em **Adicionar**.

   >[!NOTE]
   >Se você não definiu as configurações do ContextHub, essa opção está desativada para o seu projeto.

1. Enter **Valor** no **Espaço reservado** campo. Selecione a linha na qual você deseja obter o valor da sua planilha do Google **Variável do ContextHub**. Nesse caso, o valor é recuperado da linha 2 e da coluna 1 das planilhas Google. Agora, insira o **Valor padrão** as **20**, como mostrado na figura abaixo. Quando terminar, clique na marca de seleção.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >Para sua referência, a imagem a seguir mostra o valor recuperado das planilhas do Google:

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. Volte para a **Sobreposição de texto** na caixa de diálogo Imagem e adicione o texto *Temperatura atual {Value}*, conforme mostrado na figura abaixo.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. Clique em **Visualizar** para exibir a saída desejada.

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
