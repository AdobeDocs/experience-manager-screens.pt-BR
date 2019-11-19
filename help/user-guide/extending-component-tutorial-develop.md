---
title: Extensão de um componente do AEM Screens
seo-title: Extensão de um componente do AEM Screens
description: O tutorial a seguir descreve as etapas e práticas recomendadas para estender os componentes do AEM Screens para fora da caixa. O componente de Imagem é estendido para adicionar uma sobreposição de texto autorável.
seo-description: O tutorial a seguir descreve as etapas e práticas recomendadas para estender os componentes do AEM Screens para fora da caixa. O componente de Imagem é estendido para adicionar uma sobreposição de texto autorável.
uuid: 38ee3a2b-a51a-4c35-b93a-89a0e5fc3837
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 46bdc191-5056-41a4-9804-8f7c4a035abf
targetaudience: target-audience new
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Extensão de um componente do AEM Screens {#extending-an-aem-screens-component}

O tutorial a seguir descreve as etapas e práticas recomendadas para estender os componentes do AEM Screens para fora da caixa. O componente de Imagem é estendido para adicionar uma sobreposição de texto autorável.

## Visão geral {#overview}

Este tutorial destina-se a desenvolvedores novos no AEM Screens. Neste tutorial, o componente Imagem da tela é estendido para criar um componente de Pôster. O título, a descrição e o logotipo são sobrepostos sobre uma imagem para criar uma experiência atraente em um Canal de sequência.

>[!NOTE]
>
>Antes de iniciar este tutorial, é recomendável concluir o tutorial: [Desenvolvimento de um componente personalizado para telas](developing-custom-component-tutorial-develop.md)AEM.

![Componente Pôster personalizado](assets/2018-05-07_at_4_09pm.png)

O componente Pôster personalizado é criado estendendo o componente de Imagem.

## Pré-requisitos {#prerequisites}

## Configuração do projeto {#project-setup}

1. Baixe e instale os seguintes pacotes usando o gerenciamento **do pacote** CRX `http://localhost:4502/crx/packmgr/index.jsp)r:`

   [Obter arquivo](assets/start-poster-screens-weretail-runuiapps-001-snapshot.zip)

   [Obter arquivo](assets/start-poster-screens-weretail-runuicontent-001-snapshot.zip)
   **Opcionalmente,** se estiver trabalhando com o Eclipse ou outro IDE, baixe o pacote de origem abaixo. Implante o projeto para uma instância AEM local usando o comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Telas de Início SRC We.Retail Run Project

   [Obter arquivo](assets/start-poster-screens-weretail-run.zip)

1. No **CRX Package Manager** `http://localhost:4502/crx/packmgr/index.jsp` , os dois pacotes a seguir estão instalados:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**
   ![Screens We.Retail Run Ui.Apps e Pacotes Ui.Content instalados pelo CRX Package Manager](assets/crx-packages.png)

   Screens We.Retail Run Ui.Apps e Pacotes Ui.Content instalados pelo CRX Package Manager

## Criar o componente de pôster {#poster-cmp}

O componente Pôster estende o componente de imagem para fora da caixa. Um mecanismo do Sling, `sling:resourceSuperType`, é usado para herdar a funcionalidade principal do componente de Imagem sem precisar copiar e colar. Mais informações sobre as noções básicas do Processamento de solicitação de [sling podem ser encontradas aqui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/the-basics.html#SlingRequestProcessing)

O componente Pôster é renderizado em tela cheia no modo de visualização/produção. No modo de edição, é importante renderizar o componente de forma diferente para facilitar a criação do canal de sequência.

1. Em **CRXDE-Lite** (ou IDE de escolha) abaixo para `http://localhost:4502/crx/de/index.jsp` criar um novo `/apps/weretail-run/components/content`nome `cq:Component` `poster`.

   Adicione as seguintes propriedades ao `poster` componente:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Poster"
       sling:resourceSuperType="screens/core/components/content/image"
       componentGroup="We.Retail Run - Content"/>
   ```

   ![Propriedades para /apps/weretail-run/components/content/poster](assets/poster.png)

   Propriedades para /apps/weretail-run/components/content/poster

   Ao definir a `sling:resourceSuperType`propriedade igual ao componente Pôster, `screens/core/components/content/image` o componente herda efetivamente toda a funcionalidade do componente de Imagem. Nós e arquivos equivalentes encontrados abaixo `screens/core/components/content/image` podem ser adicionados abaixo do `poster` componente para substituir e estender a funcionalidade.

1. Copie o `cq:editConfig` nó abaixo de `/libs/screens/core/components/content/image.`Colar o `cq:editConfig` abaixo do `/apps/weretail-run/components/content/poster` componente.

   No `cq:editConfig/cq:dropTargets/image/parameters` nó, atualize a `sling:resourceType` propriedade para igual `weretail-run/components/content/poster`.

   ![edit-config](assets/edit-config.png)

   Representação XML de cq:editConfig representada abaixo:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="cq:EditConfig">
       <cq:dropTargets jcr:primaryType="nt:unstructured">
           <image
               jcr:primaryType="cq:DropTargetConfig"
               accept="[image/.*]"
               groups="[media]"
               propertyName="./fileReference">
               <parameters
                   jcr:primaryType="nt:unstructured"
                   sling:resourceType="weretail-run/components/content/poster"
                   imageCrop=""
                   imageMap=""
                   imageRotate=""/>
           </image>
       </cq:dropTargets>
   </jcr:root>
   ```

1. Copie a caixa de diálogo do WCM Foundation `image` para ser usada para o `poster` componente.

   É mais fácil começar de uma caixa de diálogo existente e depois fazer modificações.

   1. Copie a caixa de diálogo de: `/libs/wcm/foundation/components/image/cq:dialog`
   1. Colar a caixa de diálogo abaixo `/apps/weretail-run/components/content/poster`
   ![Caixa de diálogo copiada de /libs/wcm/Foundation/components/image/cq:dialog para /apps/weretail-run/components/content/poster](assets/2018-05-03_at_4_13pm.png)

   Caixa de diálogo copiada de /libs/wcm/Foundation/components/image/cq:dialog para /apps/weretail-run/components/content/poster

   O componente Screens `image` é sobreposto ao componente WCM Foundation `image` . Portanto, o `poster` componente herda a funcionalidade de ambos. A caixa de diálogo do componente de pôster é composta por uma combinação dos diálogos Screens e Foundation. Os recursos da Fusão **de Recursos do** Sling são usados para ocultar campos de diálogo irrelevantes e guias herdadas dos componentes com supertipos.

1. Atualize a caixa de diálogo cq:abaixo `/apps/weretail-run/components/content/poster` com as seguintes alterações representadas no XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Poster"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout
               jcr:primaryType="nt:unstructured"
               sling:resourceType="granite/ui/components/foundation/layouts/tabs"
               type="nav"/>
           <items jcr:primaryType="nt:unstructured">
               <image
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Elements"
                   sling:resourceType="granite/ui/components/foundation/section">
                   <layout
                       jcr:primaryType="nt:unstructured"
                       sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
                       margin="{Boolean}false"/>
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/foundation/container">
                           <items
                               jcr:primaryType="nt:unstructured"
                               sling:hideChildren="[linkURL,size]">
                               <file
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="cq/gui/components/authoring/dialog/fileupload"
                                   autoStart="{Boolean}false"
                                   class="cq-droptarget"
                                   fieldLabel="Image asset"
                                   fileNameParameter="./fileName"
                                   fileReferenceParameter="./fileReference"
                                   mimeTypes="[image]"
                                   multiple="{Boolean}false"
                                   name="./file"
                                   title="Upload Image Asset"
                                   uploadUrl="${suffix.path}"
                                   useHTML5="{Boolean}true"/>
                               <title
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textfield"
                                   fieldLabel="Title"
                                   name="./jcr:title"/>
                               <description
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/foundation/form/textarea"
                                   fieldLabel="Description"
                                   name="./jcr:description"/>
                               <position
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Position"
                                   name="./textPosition">
                                   <items jcr:primaryType="nt:unstructured">
                                       <left
                                           jcr:primaryType="nt:unstructured"
                                           text="Left"
                                           value="left"/>
                                       <center
                                           jcr:primaryType="nt:unstructured"
                                           text="Center"
                                           value="center"/>
                                       <right
                                           jcr:primaryType="nt:unstructured"
                                           text="Right"
                                           value="right"/>
                                   </items>
                               </position>
                               <color
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/select"
                                   fieldLabel="Text Color"
                                   name="./textColor">
                                   <items jcr:primaryType="nt:unstructured">
                                       <light
                                           jcr:primaryType="nt:unstructured"
                                           text="Light"
                                           value="light"/>
                                       <dark
                                           jcr:primaryType="nt:unstructured"
                                           text="Dark"
                                           value="dark"/>
                                   </items>
                               </color>
                           </items>
                       </column>
                   </items>
               </image>
               <accessibility
                   jcr:primaryType="nt:unstructured"
                   sling:hideResource="{Boolean}true"/>
           </items>
       </content>
   </jcr:root>
   ```

   A propriedade `sling:hideChildren`= `"[linkURL,size]`" é usada no `items` nó para garantir que os campos **linkURL** e **tamanho** estejam ocultos na caixa de diálogo. A remoção desses nós da caixa de diálogo do pôster não é suficiente. A propriedade `sling:hideResource="{Boolean}true"` na guia acessibilidade é usada para ocultar a guia inteira.

   Dois campos de seleção são adicionados à caixa de diálogo para dar aos autores controle sobre a posição e a cor do texto do Título e da Descrição.

   ![Pôster - Estrutura de diálogo final](assets/2018-05-03_at_4_49pm.png)

   Pôster - Estrutura de diálogo final

   Nesse ponto, uma instância do `poster` componente pode ser adicionada à página **Idle Channel** no projeto We.Retail Run:  `http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`.

   ![Campos da caixa de diálogo Pôster](assets/poster-dialog-full.png)

   Campos da caixa de diálogo Pôster

1. Crie um arquivo sob o `/apps/weretail-run/components/content/poster` nome `production.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/production.html
   
   */-->
   <div data-sly-use.image="image.js"
        data-duration="${properties.duration}"
        class="cmp-poster"
        style="background-image: url(${request.contextPath @ context='uri'}${image.src @ context='uri'});">
       <div class="cmp-poster__text
                   cmp-poster__text--${properties.textPosition @ context='attribute'}
                   cmp-poster__text--${properties.textColor @ context='attribute'}">
           <h1 class="cmp-poster__title">${properties.jcr:title}</h1>
            <h2 class="cmp-poster__description">${properties.jcr:description}</h2>
       </div>
    <img class="cmp-poster__logo" src="/content/dam/we-retail-run/logos/we-retail-run_dark.png" alt="we-retail-logo" />
   </div>
   ```

   Acima está a marcação de produção do Componente de cartaz. O script HTL é substituído `screens/core/components/content/image/production.html`. O `image.js` é um script do lado do servidor que cria um objeto de imagem semelhante ao POJO. O objeto Image pode então ser chamado para renderizar o objeto `src` como uma imagem de fundo de estilo incorporado.

   `The h1` e as tags h2 são adicionadas exibem o Título e a Descrição com base nas propriedades do componente: `${properties.jcr:title}` e `${properties.jcr:description}`.

   Ao redor das tags `h1` e `h2` é um invólucro div com três classes CSS com variações de " `cmp-poster__text`". O valor das propriedades `textPosition` e `textColor` é usado para alterar a classe CSS renderizada com base na seleção da caixa de diálogo do autor. Na próxima seção, o CSS das bibliotecas do cliente será gravado para ativar essas alterações na exibição.

   Um logotipo também é incluído como uma sobreposição no componente. Neste exemplo, o caminho para o logotipo We.Retail é codificado no DAM. Dependendo do caso de uso, pode fazer mais sentido criar um novo campo de diálogo para tornar o caminho do logotipo um valor preenchido dinamicamente.

   Observe também que a notação BEM (Block Element Modifier) é usada com o componente. O BEM é uma convenção de codificação de CSS que facilita a criação de componentes reutilizáveis. BEM é a notação usada pelos Componentes [principais do](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions)AEM. Mais informações podem ser encontradas em: [https://getbem.com/](https://getbem.com/)

1. Crie um arquivo sob o `/apps/weretail-run/components/content/poster` nome `edit.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
   
       /apps/weretail-run/components/content/poster/edit.html
   
   */-->
   
   <div class="aem-Screens-editWrapper ${image.cssClass} cmp-poster" data-sly-use.image="image.js" data-emptytext="${'Poster' @ i18n, locale=request.locale}">
       <img class="cmp-poster__image" src="${request.contextPath}${image.src @ context='uri'}" width="100%" />
       <div class="cmp-poster__text
              cmp-poster__text--${properties.textPosition @ context='attribute'}
          cmp-poster__text--${properties.textColor @ context='attribute'}">
         <p class="cmp-poster__title">${properties.jcr:title}</p>
         <p class="cmp-poster__description">${properties.jcr:description}</p>
       </div>
   </div>
   ```

   Acima está a marcação de **edição** do Componente de cartaz. O script HTL é substituído `/libs/screens/core/components/content/image/edit.html`. A marcação é semelhante à `production.html` marcação e exibirá o título e a descrição na parte superior da imagem.

   O componente `aem-Screens-editWrapper`é adicionado para que não renderize tela cheia no editor. O `data-emptytext` atributo garante que o espaço reservado seja exibido quando nenhuma imagem ou conteúdo tiver sido preenchido.

## Criar bibliotecas do lado do cliente {#clientlibs}

As bibliotecas do lado do cliente fornecem um mecanismo para organizar e gerenciar arquivos CSS e JavaScript necessários para uma implementação do AEM. Mais informações sobre o uso das bibliotecas do lado do [cliente podem ser encontradas aqui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html)

Os componentes do AEM Screens são renderizados de forma diferente no modo de edição vs. modo de visualização/produção. Dois conjuntos de bibliotecas clientes são criados, um para o modo de edição e outro para a Visualização/Produção.

1. Crie uma pasta para bibliotecas do lado do cliente para o componente Pôster.

   Abaixo, `/apps/weretail-run/components/content/poster,`crie uma nova pasta chamada `clientlibs`.

   ![2018-05-03_at_1008](assets/2018-05-03_at_1008pm.png)

1. Abaixo da `clientlibs` pasta, crie um novo nó com o nome `shared` do tipo `cq:ClientLibraryFolder.`

   ![2018-05-03_at_1011](assets/2018-05-03_at_1011pm.png)

1. Adicione as seguintes propriedades à biblioteca de clientes compartilhados:

   * `allowProxy` | Booleano | `true`
   * `categories` | String[] | `cq.screens.components`
   ![Propriedades para /apps/weretail-run/components/content/poster/clientlibs/shared](assets/2018-05-03_at_1026pm-1.png)

   Propriedades para /apps/weretail-run/components/content/poster/clientlibs/shared

   A `categories` propriedade é uma string que identifica a biblioteca do cliente. A `cq.screens.components` categoria é usada nos modos Editar e Visualizar/Produção. Portanto, qualquer CSS/JS definido na `shared` clientlib é carregado em todos os modos.

   É uma prática recomendada nunca expor nenhum caminho diretamente para /apps em um ambiente de produção. A `allowProxy` propriedade garante que a biblioteca do cliente CSS e JS sejam referenciadas por meio de um prefixo de `/etc.clientlibs`. Mais informações sobre a propriedade [allowProxy podem ser encontradas aqui.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/clientlibs.html#main-pars_title_8ced)

1. Crie um arquivo com o nome `css.txt` abaixo da pasta compartilhada.

   Preencha o arquivo com o seguinte:

   ```
   #base=css
   
   styles.less
   ```

1. Crie uma pasta chamada `css` abaixo da `shared` pasta. Adicione um arquivo com o nome `style.less` abaixo da `css` pasta. A estrutura das bibliotecas de clientes agora deve ser parecida com esta:

   ![2018-05-03_at_1057](assets/2018-05-03_at_1057pm.png)

   Em vez de gravar CSS diretamente, este tutorial usa MENOS. [LESS](https://lesscss.org/) é um pré-compilador de CSS popular que suporta variáveis, mixins e funções de CSS. As bibliotecas de clientes AEM oferecem suporte nativo a compilação LESS. É possível usar Sass ou outros pré-compiladores, mas eles precisam ser compilados fora do AEM.

1. Preencha `/apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less` com o seguinte:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/shared/css/styles.less
    Poster Component - Shared Style
   */
   
   @import url('https://fonts.googleapis.com/css?family=Fjalla+One|Open+Sans:400i');
   
   @text-light-color: #fff;
   @text-dark-color: #000;
   @title-font-family: 'Fjalla One', sans-serif;
   @description-font-family: 'Open Sans', sans-serif;
   
   .cmp-poster {
   
         &__text {
         position: absolute;
         color: @text-light-color;
         top: 0;
         text-align:center;
         width: 100%;
   
         &--left {
          text-align: left;
                margin-left: 1em;
         }
   
         &--right {
          text-align: right;
                margin-right: 1em;
         }
   
         &--dark {
          color: @text-dark-color;
         }
       }
   
       &__title {
         font-weight: bold;
            font-family: @title-font-family;
            font-size: 1.2em;
       }
   
       &__description {
     font-style: italic;
           font-family: @description-font-family;
    }
   
   }
   ```

   >[!NOTE]
   >
   >As fontes da Web do Google são usadas para as famílias de fontes. As fontes da Web exigem conectividade com a Internet e nem todas as implementações de telas terão uma conexão confiável. O planejamento para o modo offline é uma consideração importante para as implantações do Screens.

1. Copie a pasta da biblioteca do `shared` cliente. Cole-o como um irmão e renomeie-o para `production`.

   ![2018-05-03_at_1114](assets/2018-05-03_at_1114pm.png)

1. Atualizar a `categories` propriedade da biblioteca de cliente de produção a ser `cq.screens.components.production.`

   A `cq.screens.components.production` categoria garante que os estilos só sejam carregados quando estiverem no modo de Visualização/Produção.

   ![Propriedades para /apps/weretail-run/components/content/poster/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propriedades para /apps/weretail-run/components/content/poster/clientlibs/production

1. Preencha `/apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less` com o seguinte:

   ```css
   /*
    /apps/weretail-run/components/content/poster/clientlibs/production/css/styles.less
    Poster Component - Production Style
   */
   
   .cmp-poster {
   
       background-size: cover;
    height: 100%;
    width: 100%;
    position:absolute;
   
        &__text {
   
           top: 2em;
   
           &--left {
               width: 40%;
               top: 5em;
           }
   
           &--right {
               width: 40%;
               right: 1em;
           }
       }
   
       &__title {
     font-size: 5rem;
     font-weight: 900;
     margin: 0.1rem;
    }
   
    &__description {
     font-size: 2rem;
     margin: 0.1rem;
     font-weight: 400;
   
    }
   
       &__logo {
     position: absolute;
     max-width: 200px;
     top: 1em;
     left: 0;
    }
   
   }
   ```

   Os estilos acima exibem o Título e a Descrição em uma posição absoluta na tela. O título será exibido significativamente maior que a descrição. A notação BEM do componente facilita o escopo cuidadoso dos estilos na classe cmp-poster.

Uma terceira categoria da biblioteca de clientes: `cq.screens.components.edit` poderia ser usado para adicionar Editar somente estilos específicos ao componente.

| Categoria Clientlib | Uso |
|---|---|
| `cq.screens.components` | Estilos e scripts que são compartilhados entre os modos de edição e produção |
| `cq.screens.components.edit` | Estilos e scripts usados somente no modo de edição |
| `cq.screens.components.production` | Estilos e scripts que são usados apenas no modo de produção |

## Adicionar componente de pôster a um canal de sequência {#add-sequence-channel}

O componente Pôster deve ser usado em um Canal de sequência. O pacote inicial deste tutorial incluía um Canal ocioso. O Idle Channel está pré-configurado para permitir componentes do grupo **We.Retail Run - Content**. O grupo do componente Pôster está definido como `We.Retail Run - Content` e disponível para ser adicionado ao canal.

1. Abra o Idle Channel do projeto We.Retail Run: **`http://localhost:4502/editor.html/content/screens/we-retail-run/channels/idle-channel.edit.html`**
1. Arraste + Solte uma nova instância do componente **Pôster** da barra lateral na página.

   ![2018-05-07_at_3_23](assets/2018-05-07_at_3_23pm.png)

1. Edite a caixa de diálogo do componente Pôster para adicionar uma Imagem, Título, Descrição. Use as opções Posição do texto e Cor do texto para garantir que o Título/Descrição esteja legível sobre a Imagem.

   ![2018-05-07_at_3_25](assets/2018-05-07_at_3_25pm.png)

1. Repita as etapas acima para adicionar alguns componentes de Pôster. Adicione transições entre os componentes.

   ![2018-05-07_at_3_28](assets/2018-05-07_at_3_28pm.png)

## Juntando tudo {#putting-it-all-together}

O vídeo abaixo mostra o componente finalizado e como ele pode ser adicionado a um canal de Sequência. O Canal é então adicionado a uma exibição Local e, por fim, atribuído a um player do Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22414?quaity=9&captions=por_br)

## Código finalizado {#finished-code}

Abaixo está o código finalizado do tutorial. Os **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** são os pacotes AEM compilados. O **SRC-screens-weretail-run-0.0.1.zip **é o código fonte não compilado que pode ser implantado usando o Maven.

[Obter arquivo](assets/final-poster-screens-weretail-runuiapps-001-snapshot.zip)

[Obter arquivo](assets/final-poster-screens-weretail-runuicontent-001-snapshot.zip)

Projeto de execução de varejo e telas finais SRC

[Obter arquivo](assets/src-screens-weretail-run-001.zip)
