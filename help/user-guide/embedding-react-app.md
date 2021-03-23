---
title: Como incorporar um aplicativo REACT usando o Editor de SPA de AEM e Integração com o AEM Screens Analytics
seo-title: Como incorporar um aplicativo REACT usando o Editor de SPA de AEM e Integração com o AEM Screens Analytics
description: Siga esta página para saber como incorporar um aplicativo de página única interativo usando o REACT (ou Angular) usando o editor de SPA AEM que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.
seo-description: Siga esta página para saber como incorporar um aplicativo de página única interativo usando o REACT (ou Angular) usando o editor de SPA AEM que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Desenvolvendo telas
role: Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---


# Como incorporar um aplicativo REACT usando o Editor de SPA de AEM e Integração com o AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Esta seção descreve como incorporar um aplicativo de página única interativo usando REACT (ou Angular) usando o editor de SPA AEM que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.

## Uso do Editor de SPA de AEM {#using-the-aem-spa-editor}

Siga as etapas abaixo para usar o Editor de SPA de AEM:

1. Clona o repositório do Editor de SPA AEM em [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Esse arquétipo cria um projeto mínimo do Adobe Experience Manager como ponto de partida para seus próprios projetos de SPA. As propriedades que devem ser fornecidas ao usar esse arquétipo permitem nomear como desejado todas as partes deste projeto.

1. Siga as instruções do readme para criar um projeto de arquétipo SPA editor de AEM:

   ```
   mvn clean install archetype:update-local-catalog
   mvn archetype:crawl
   
   mvn archetype:generate \
   -DarchetypeCatalog=internal \
   -DarchetypeGroupId=com.adobe.cq.spa.archetypes \
   -DarchetypeArtifactId=aem-spa-project-archetype \
   -DarchetypeVersion=1.0.3-SNAPSHOT \
   ```

   >[!NOTE]
   >
   >Usamos o **GroupId** como ***com.adobe.aem.screens*** e o **ArtifactId** como ***My Sample SPA*** (que são os padrões). Você pode escolher o seu, conforme necessário.

1. Depois que o projeto for criado, use um IDE ou editor de sua escolha e importe o projeto Maven gerado.
1. Implante na instância de AEM local usando o comando ***mvn clean install -PautoInstallPackage***.

### Edição de conteúdo no aplicativo REACT {#editing-content-in-the-react-app}

Para editar o conteúdo no aplicativo REACT:

1. Navegue até `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (substitua o nome do host, a porta e o nome do projeto, conforme aplicável).
1. Você deve poder editar o texto sendo exibido no aplicativo Hello world.

### Adicionar o aplicativo REACT interativo ao AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Siga as etapas abaixo para adicionar o aplicativo REACT interativo ao AEM Screens:

1. Crie um novo projeto do AEM Screens. Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para obter mais detalhes.

   >[!NOTE]
   >
   >Crie um **Canal de sequência** ao criar um canal na pasta **Canais** do seu projeto do Screens.
   >
   >
   >Consulte [Criação e gerenciamento de canais](managing-channels.md) para obter mais detalhes.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Edite qualquer canal de sequência e arraste e solte um componente de página incorporado.

   Consulte [Adicionar componentes a um canal](adding-components-to-a-channel.md) para obter mais detalhes.

   >[!NOTE]
   >
   >Adicione o evento de interação do usuário ao atribuir o canal à exibição.

1. Clique em **Editar** na barra de ações para editar as propriedades do canal de sequência.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Arraste e solte o componente **Embedded Page** e selecione a página inicial no aplicativo mysamplespa, por exemplo, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registre um reprodutor neste projeto e você poderá ver seu aplicativo interativo em execução no AEM Screens.

   Consulte [Device Registration](device-registration.md) para saber mais detalhes sobre o registro de um dispositivo.

## Integração do SPA com o Adobe Analytics com recursos offline por meio do AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Siga as etapas abaixo para integrar o SPA com o Adobe Analytics com recurso offline por meio do AEM Screens:

1. Configure o Adobe Analytics no AEM Screens.

   Consulte [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md) para saber como executar o sequenciamento no Adobe Analytics com AEM Screens e enviar eventos personalizados usando Adobe Analytics offline.

1. Edite seu aplicativo de reação no IDE/editor de sua escolha (especialmente o componente de texto ou outro componente que você deseja iniciar a emissão de eventos).
1. No evento click ou em outro evento que você deseja capturar para o componente, adicione as informações de análise usando o modelo de dados padrão.

   Consulte [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md)s para obter mais detalhes.

1. Chame a API do AEM Screens Analytics para salvar o evento offline e enviá-lo em rajadas para o Adobe Analytics.

   Por exemplo,

   ```
   handleClick() {
       if ((window.parent) && (window.parent.CQ) && (window.parent.CQ.screens) && (window.parent.CQ.screens.analytics))
       {
           var analyticsEvent = {};
           analyticsEvent['event.type'] = 'play'; // Type of event
    analyticsEvent['event.coll_dts'] = new Date().toISOString(); // Start of collecting the event
    analyticsEvent['event.dts_start'] = new Date().toISOString(); // Event start
    analyticsEvent['content.type'] = 'Washing machine'; // Mime Type or product category
    analyticsEvent['content.action'] = 'Path to the washing machine asset in AEM'; // Path in AEM to relevant asset
    analyticsEvent['trn.product'] = 'Washing machine Model number'; // Product being explored
    analyticsEvent['trn.amount'] = 1000; // Product pricing or other numeric value or weight
    analyticsEvent['event.dts_end'] = new Date().toISOString(); // Event end
    analyticsEvent['event.count'] = 100; // Numeric value that may count a number of clicks or keystrokes or wait time in seconds for example
    analyticsEvent['event.value'] = 'My favorite analytics event';
           analyticsEvent['trn.quantity'] = 10; // Quantity of product selection
    analyticsEvent['event.subtype'] = 'end'; // Event subtype if applicable
    window.parent.CQ.screens.analytics.sendTrackingEvent(analyticsEvent);
       }
   }
   ```

   >[!NOTE]
   >
   >O firmware do reprodutor adiciona automaticamente mais detalhes sobre o reprodutor e seu ambiente de tempo de execução aos dados de análise personalizados que você envia. Portanto, talvez você não precise capturar detalhes de SO/dispositivo de baixo nível, a menos que seja absolutamente necessário. Você só precisa se concentrar nos dados de análise de negócios.

