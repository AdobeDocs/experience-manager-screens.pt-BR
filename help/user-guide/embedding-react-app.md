---
title: Incorporação de um aplicativo REACT usando o Editor SPA AEM e Integração com o AEM Screens Analytics
seo-title: Incorporação de um aplicativo REACT usando o Editor SPA AEM e Integração com o AEM Screens Analytics
description: Siga esta página para saber como incorporar um aplicativo interativo de página única usando REACT (ou Angular) usando o editor AEM SPA que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.
seo-description: Siga esta página para saber como incorporar um aplicativo interativo de página única usando REACT (ou Angular) usando o editor AEM SPA que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.
uuid: fb56ede0-7b36-4f47-b9e5-d806c9a3c707
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
translation-type: tm+mt
source-git-commit: bca6dc0f6a022a4a9005053320e5047b9321270d
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---


# Incorporação de um aplicativo REACT usando o Editor SPA AEM e Integração com o AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

Esta seção descreve como incorporar um aplicativo interativo de página única usando REACT (ou Angular) usando o editor AEM SPA que pode ser configurado pelos profissionais de negócios no AEM e também como integrar seu aplicativo interativo ao Adobe Analytics offline.

## Uso do Editor SPA AEM {#using-the-aem-spa-editor}

Siga as etapas abaixo para usar o Editor SPA AEM:

1. Clonar o AEM repo do Editor SPA em [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Esse arquétipo cria um projeto mínimo do Adobe Experience Manager como ponto de partida para seus próprios projetos SPA. As propriedades que devem ser fornecidas ao usar esse arquétipo permitem nomear como desejado todas as partes deste projeto.

1. Siga as instruções do readme para criar um projeto de arquétipo do editor AEM SPA:

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
   >Usamos o **GroupId** como ***com.adobe.aem.screens*** e o **ArtiactualId** como ***My Sample SPA*** (que é o padrão). Você pode escolher o seu próprio, conforme necessário.

1. Depois que o projeto for criado, use um IDE ou editor de sua escolha e importe o projeto Maven gerado.
1. Implante para sua instância AEM local usando o comando ***mvn clean install -PautoInstallPackage***.

### Editar conteúdo no aplicativo REACT {#editing-content-in-the-react-app}

Para editar o conteúdo no aplicativo REACT:

1. Navegue até `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (substitua o nome do host, a porta e o nome do projeto, conforme aplicável).
1. Você deve poder editar o texto que está sendo exibido no aplicativo Hello world.

### Adicionar o aplicativo REACT interativo à AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Siga as etapas abaixo para adicionar o aplicativo REACT interativo à AEM Screens:

1. Crie um novo projeto da AEM Screens. Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para obter mais detalhes.

   >[!NOTE]
   >
   >Crie um Canal **de** sequência ao criar um canal na pasta **Canais** do projeto do Screens.
   >
   >
   >Consulte [Criação e gerenciamento de Canais](managing-channels.md) para obter mais detalhes.

   ![screen_shot_2019-02-15at100330am](assets/screen_shot_2019-02-15at100330am.png)

1. Edite qualquer canal de sequência e arraste e solte um componente de página incorporado.

   Consulte [Adicionando componentes a um Canal](adding-components-to-a-channel.md) para obter mais detalhes.

   >[!NOTE]
   >
   >Certifique-se de adicionar o evento de interação do usuário ao atribuir o canal à tela.

1. Clique em **Editar** na barra de ações para editar as propriedades do canal de sequência.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Arraste e solte o componente Página **** incorporada e selecione o home page no aplicativo mysamplespa, por exemplo, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Registre um player neste projeto e agora você pode ver seu aplicativo interativo em execução no AEM Screens.

   Consulte Registro [do](device-registration.md) dispositivo para saber mais detalhes sobre como registrar um dispositivo.

## Integração do SPA com o Adobe Analytics com recursos offline por meio do AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Siga as etapas abaixo para integrar o SPA ao Adobe Analytics com recursos offline por meio do AEM Screens:

1. Configure o Adobe Analytics no AEM Screens.

   Consulte [Configuração do Adobe Analytics com o AEM Screens](configuring-adobe-analytics-aem-screens.md) para saber como executar o sequenciamento no Adobe Analytics com o AEM Screens e enviar eventos personalizados usando o Adobe Analytics offline.

1. Edite seu aplicativo de reação no IDE/editor de sua escolha (especialmente o componente de texto ou outro componente que você deseja que seja o start dos eventos que emitem).
1. No evento click ou em outro evento que você deseja capturar para seu componente, adicione as informações de análise usando o modelo de dados padrão.

   Consulte [Configuração do Adobe Analytics com](configuring-adobe-analytics-aem-screens.md)telas AEM para obter mais detalhes.

1. Chame a API do AEM Screens Analytics para salvar o evento off-line e enviá-lo em rastros para a Adobe Analytics.

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
   >O firmware do player adiciona automaticamente mais detalhes sobre o player e seu ambiente de tempo de execução aos dados personalizados de análise que você envia. Portanto, talvez você não precise capturar detalhes de SO/dispositivo de baixo nível, a menos que seja absolutamente necessário. Basta focar nos dados de análise de negócios.

