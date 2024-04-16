---
title: Incorporação de um aplicativo REACT usando o Editor SPA AEM e Integração com o AEM Screens Analytics
description: Saiba como incorporar um aplicativo interativo de página única usando o REACT (ou Angular) usando o editor SPA do AEM.
content-type: reference
topic-tags: developing
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: e4ecc179-e421-4687-854c-14d31bed031d
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 7dc7d07e-cd94-4ce1-a106-98669be62046
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Incorporação de um aplicativo REACT usando o Editor SPA AEM e Integração com o AEM Screens Analytics {#embedding-a-react-application-using-the-aem-spa-editor-and-integrating-with-aem-screens-analytics}

É possível incorporar um aplicativo interativo de página única usando o REACT (ou Angular). Você faz isso usando o editor SPA AEM que é configurado por profissionais de negócios no AEM. Você também pode aprender a integrar seu aplicativo interativo com o Adobe Analytics offline.

## AEM Utilização do editor SPA {#using-the-aem-spa-editor}

Siga as etapas abaixo para usar o Editor de SPA AEM:

1. AEM Clonar o repositório do Editor SPA em [https://github.com/adobe/aem-spa-project-archetype.](https://github.com/adobe/aem-spa-project-archetype)

   >[!NOTE]
   >
   >Esse arquétipo cria um projeto mínimo do Adobe Experience Manager como ponto de partida para seus próprios projetos SPA. As propriedades que devem ser fornecidas ao usar esse arquétipo permitem nomear como desejado todas as partes desse projeto.

1. Para criar um projeto de arquétipo do editor SPA AEM, siga as instruções do arquivo readme:

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
   >Esta documentação usa o **GroupId** as ***com.adobe.aem.screens*** e a variável **ArtifactId** as ***Meu SPA de Exemplo*** (que são os padrões). Você pode escolher o seu próprio conforme necessário.

1. Depois que o projeto for criado, use um IDE ou editor de sua escolha e importe o projeto Maven gerado.
1. Implante na instância local do AEM usando o comando ***mvn clean install - PautoInstallPackage***.

### Edição de conteúdo no aplicativo REACT {#editing-content-in-the-react-app}

Para editar o conteúdo no aplicativo REACT:

1. Navegue até `https://localhost:4502/editor.html/content/mysamplespa/en/home.html` (substitua o nome do host, a porta e o nome do projeto, conforme aplicável).
1. Você deve ser capaz de editar o texto que está sendo exibido no aplicativo Hello world.

### Adição do aplicativo REACT interativo ao AEM Screens {#adding-the-interactive-react-app-to-aem-screens}

Siga as etapas abaixo para adicionar o aplicativo REACT interativo ao AEM Screens:

1. Crie um projeto do AEM Screens. Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para obter mais detalhes.
1. Criar um **Canal do aplicativo** (de preferência) (ou modelo 1x1 ou canal de várias zonas) no **Canais** pasta do seu projeto do AEM Screens.

   >[!NOTE]
   >**Canais de sequência** não são incentivados neste caso de uso porque eles vêm, por natureza, com uma lógica de apresentação de slides que entra em conflito com a natureza interativa da experiência.
   >Consulte [Criação e gerenciamento de canais](managing-channels.md) para obter mais detalhes.

1. Edite qualquer canal de sequência e arraste e solte um componente de página incorporado.

   Consulte [Adicionar componentes a um canal](adding-components-to-a-channel.md) para obter mais detalhes.

   >[!NOTE]
   >
   >Adicione o evento de interação do usuário ao atribuir o canal à exibição.

1. Clique em **Editar** na barra de ações, para poder editar as propriedades do canal.

   ![screen_shot_2019-02-15at100555am](assets/screen_shot_2019-02-15at100555am.png)

1. Arraste e solte a **Página incorporada** componente ou reutilize o componente existente em um canal de aplicativo, e clique na página inicial no aplicativo mysamplespa, por exemplo, ***/content/mysamplespa/en/home***.

   ![screen_shot_2019-02-15at101104am](assets/screen_shot_2019-02-15at101104am.png)

1. Atribua o canal a uma exibição.

   >[!NOTE]
   >Adicione o evento de interação do usuário ao atribuir o canal à exibição.

1. Registrar um reprodutor neste projeto e atribuí-lo à exibição. Agora é possível ver seu aplicativo interativo em execução no AEM Screens.

   Consulte [Registro do dispositivo](device-registration.md) para obter mais informações sobre como registrar um dispositivo.

## Integração do SPA ao Adobe Analytics com recurso offline por meio do AEM Screens {#integrating-the-spa-with-adobe-analytics-with-offline-capability-through-aem-screens}

Siga as etapas abaixo para integrar o SPA ao Adobe Analytics com o recurso offline por meio do AEM Screens:

1. Configure o Adobe Analytics no AEM Screens.

   Consulte [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md) para obter mais informações sobre como executar o sequenciamento no Adobe Analytics com AEM Screens e enviar eventos personalizados usando o Adobe Analytics offline.

1. Edite o aplicativo react no IDE/editor de sua escolha (especialmente o componente de texto ou outro componente que você deseja começar a emitir eventos).
1. No evento de clique ou outro evento que você deseja capturar para o componente, adicione as informações do Analytics usando o modelo de dados padrão.

   Consulte [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md) para obter mais detalhes.

1. Chame a API do AEM Screens Analytics para salvar o evento offline e enviá-lo em intermitência para o Adobe Analytics.

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
   >O firmware do player adiciona automaticamente mais detalhes sobre o player e seu ambiente de tempo de execução aos dados de análise personalizados enviados. Portanto, talvez seja necessário capturar detalhes de sistema operacional/dispositivo de baixo nível, a menos que seja necessário. Concentre-se nos dados de análise de negócios.
