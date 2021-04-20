---
title: Desenvolvimento de um componente personalizado para o AEM Screens
seo-title: Desenvolvimento de um componente personalizado para o AEM Screens
description: O tutorial a seguir apresenta as etapas para criar um componente personalizado para o AEM Screens. A AEM Screens reutiliza muitos padrões e tecnologias de design existentes de outros produtos AEM. O tutorial destaca as diferenças e considerações especiais ao desenvolver o para AEM Screens.
seo-description: Um tutorial introdutório para criar um componente "Hello World" simples para AEM Screens. A AEM Screens reutiliza muitos padrões e tecnologias de design existentes de outros produtos AEM. O tutorial a seguir pretende destacar as diferenças e considerações específicas ao desenvolver o para AEM Screens.
uuid: 8ec8be5a-6348-48f2-9cb7-75b2bad555a6
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
discoiquuid: 24eb937f-ab51-4883-8236-8ebe6243f6e3
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '2190'
ht-degree: 2%

---


# Desenvolvimento de um componente personalizado para o AEM Screens {#developing-a-custom-component-for-aem-screens}

O tutorial a seguir apresenta as etapas para criar um componente personalizado para o AEM Screens. A AEM Screens reutiliza muitos padrões e tecnologias de design existentes de outros produtos AEM. O tutorial destaca as diferenças e considerações especiais ao desenvolver o para AEM Screens.

## Visão geral {#overview}

Este tutorial é destinado a desenvolvedores novos no AEM Screens. Neste tutorial, um componente simples &quot;Hello World&quot; é criado para um canal de sequência no AEM Screens. Uma caixa de diálogo permite que os autores atualizem o texto exibido.

![overviewhellow](assets/overviewhellow.png)

## Pré-requisitos {#prerequisites}

Para concluir este tutorial, é necessário o seguinte:

1. [AEM 6.5](https://helpx.adobe.com/br/experience-manager/6-4/release-notes.html) ou  [AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html) + Pacote de recursos do Screens mais recente

1. [Player do AEM Screens](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-screens-introduction.html)
1. Ambiente de desenvolvimento local

As etapas tutoriais e capturas de tela são executadas usando **CRXDE-Lite**. Os IDEs também podem ser usados para concluir o tutorial. Mais informações sobre como usar um IDE para desenvolver [com AEM podem ser encontradas aqui.](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#eclipse-ide)


## Configuração do projeto {#project-setup}

O código-fonte de um projeto do Screens geralmente é gerenciado como um projeto Maven de vários módulos. Para acelerar o tutorial, um projeto foi pré-gerado usando o [AEM Arquétipo de projeto 13](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype). Mais detalhes sobre a [criação de um projeto com o Maven AEM Project Archetype podem ser encontrados aqui](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html#maven-multimodule).

1. Baixe e instale os seguintes pacotes usando o [Gerenciador de pacotes CRX](http://localhost:4502/crx/packmgr/index.jsp):

   [Obter arquivo](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Obter arquivo](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **** Como opção, se estiver trabalhando com o Eclipse ou outro IDE, baixe o pacote de origem abaixo. Implante o projeto em uma instância de AEM local usando o comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Inicie o projeto HelloWorld SRC Screens We.Retail Run

   [Obter arquivo](assets/src-screens-weretail-run.zip)

1. Em [Gerenciador de Pacotes CRX](http://localhost:4502/crx/packmgr/index.jsp), verifique se os dois pacotes a seguir estão instalados:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![O Screens Executará os pacotes Ui.Apps e Ui.Content instalados pelo Gerenciador de Pacotes do CRX](assets/crx-packages.png)

   O Screens Executará os pacotes Ui.Apps e Ui.Content instalados pelo Gerenciador de Pacotes do CRX

1. O pacote **screens-weretail-run.ui.apps** instala o código abaixo de `/apps/weretail-run`.

   Este pacote contém o código responsável pela renderização de componentes personalizados para o projeto. Esse pacote inclui o código do componente e qualquer JavaScript ou CSS necessário. Este pacote também incorpora **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** que contém qualquer código Java necessário para o projeto.

   >[!NOTE]
   >
   >Neste tutorial, nenhum código Java é gravado. Se for necessária uma lógica comercial mais complexa, o Java de back-end poderá ser criado e implantado usando o pacote Java principal.

   ![Representação do código ui.apps no CRXDE Lite](assets/uipps-contents.png)

   Representação do código ui.apps no CRXDE Lite

   No momento, o componente **helloworld** é apenas um espaço reservado. Ao longo do tutorial, a funcionalidade será adicionada, permitindo que um autor atualize a mensagem exibida pelo componente.

1. O pacote **screens-weretail-run.ui.content** instala o código abaixo de:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Este pacote contém o conteúdo inicial e a estrutura de configuração necessária para o projeto. **`/conf/we-retail-run`** contém todas as configurações para o projeto Execução We.Retail. **`/content/dam/we-retail-run`** O inclui o início de ativos digitais para o projeto. **`/content/screens/we-retail-run`** contém a estrutura de conteúdo do Screens. O conteúdo abaixo de todos esses caminhos é atualizado principalmente no AEM. Para promover a consistência entre ambientes (local, Dev, Stage, Prod), geralmente uma estrutura de conteúdo base é salva no controle de origem.

1. **Navegue até o projeto AEM Screens > Execução We.Retail:**

   No menu Iniciar AEM > Clique no ícone do Screens. Verifique se o projeto We.Retail Run (Execução do We.Retail) pode ser visualizado.

   ![we-retaiul-run-starter](assets/we-retaiul-run-starter.png)

## Crie o componente Hello World {#hello-world-cmp}

O componente Hello World é um componente simples que permite que um usuário insira uma mensagem na tela. O componente é baseado no [Modelo do Componente AEM Screens: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

O AEM Screens tem algumas restrições interessantes que não são necessariamente verdadeiras para os componentes tradicionais de Sites WCM.

* A maioria dos componentes do Screens precisa ser executada em tela cheia nos dispositivos de sinalização digital de destino
* A maioria dos componentes do Screens precisam ser incorporados nos canais de sequência para gerar apresentações de slides
* A criação deve permitir a edição de componentes individuais em um canal de sequência, de modo que a renderização desses componentes na tela cheia está fora de questão

1. Em **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (ou IDE de escolha) navegue até `/apps/weretail-run/components/content/helloworld.`

   Adicione as seguintes propriedades ao componente `helloworld`:

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Propriedades para /apps/weretail-run/components/content/helloworld](assets/2018-04-28_at_4_23pm.png)

   Propriedades para /apps/weretail-run/components/content/helloworld

   O componente **helloworld** estende o componente **foundation/components/parbase** para que ele possa ser usado adequadamente dentro de um canal de sequência.

1. Crie um arquivo sob `/apps/weretail-run/components/content/helloworld` chamado `helloworld.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/helloworld.html
   
   */-->
   
   <!--/* production: preview authoring mode + unspecified mode (i.e. on publish) */-->
   <sly data-sly-test.production="${wcmmode.preview || wcmmode.disabled}" data-sly-include="production.html" />
   
   <!--/* edit: any other authoring mode, i.e. edit, design, scaffolding, etc. */-->
   <sly data-sly-test="${!production}" data-sly-include="edit.html" />
   ```

   Os componentes do Screens exigem duas renderizações diferentes, dependendo de qual [modo de criação](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/author-environment-tools.html#PageModes) está sendo usado:

   1. **Produção**: Modo de visualização ou publicação (wcmmode=disabled)
   1. **Editar**: usado para todos os outros modos de criação, ou seja, edição, design, scaffolding, desenvolvedor..

   `helloworld.html`atua como um switch, verificando qual modo de criação está ativo no momento e redirecionando para outro script HTL. Uma convenção comum usada por componentes de telas é ter um script `edit.html` para o modo Editar e um script `production.html` para o modo Produção.

1. Crie um arquivo sob `/apps/weretail-run/components/content/helloworld` chamado `production.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   Acima está a marcação de produção do componente Hello World. Um atributo `data-duration` é incluído, pois o componente é usado em um canal de Sequência. O atributo `data-duration` é usado pelo canal de sequência para saber por quanto tempo um item de sequência deve ser exibido.

   O componente renderiza um `div` e uma tag `h1` com texto. `${properties.message}` é uma parte do script HTL que resultará no conteúdo de uma propriedade JCR chamada  `message`. Uma caixa de diálogo é criada posteriormente, permitindo que o usuário insira um valor para o texto da propriedade `message`.

   Observe também que a notação BEM (Bloquear modificador de elemento) é usada com o componente. O BEM é uma convenção de codificação de CSS que facilita a criação de componentes reutilizáveis. BEM é a notação usada por [AEM Componentes principais](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/wiki/CSS-coding-conventions). Mais informações podem ser encontradas em: [https://getbem.com/](https://getbem.com/)

1. Crie um arquivo sob `/apps/weretail-run/components/content/helloworld` chamado `edit.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
   
    /apps/weretail-run/components/content/helloworld/edit.html
   
   */-->
   
   <!--/* if message populated */-->
   <div
    data-sly-test.message="${properties.message}"
    class="aem-Screens-editWrapper cmp-hello-world">
    <p class="cmp-hello-world__message">${message}</p>
   </div>
   
   <!--/* empty place holder */-->
   <div data-sly-test="${!message}"
        class="aem-Screens-editWrapper cq-placeholder cmp-hello-world"
        data-emptytext="${'Hello World' @ i18n, locale=request.locale}">
   </div>
   ```

   Acima está a marcação de edição para o componente Hello World. O primeiro bloco exibe uma versão de edição do componente se a mensagem de diálogo tiver sido preenchida.

   O segundo bloco é renderizado se nenhuma mensagem de diálogo tiver sido inserida. As `cq-placeholder` e `data-emptytext` renderizam o rótulo ***Hello World*** como um espaço reservado nesse caso. A sequência de caracteres do rótulo pode ser internacionalizada usando o i18n para oferecer suporte à criação em várias localidades.

1. **Caixa de diálogo Copiar imagem do Screens para ser usada para o componente Hello World.**

   É mais fácil começar com uma caixa de diálogo existente e depois fazer modificações.

   1. Copie a caixa de diálogo de: `/libs/screens/core/components/content/image/cq:dialog`
   1. Cole a caixa de diálogo abaixo de `/apps/weretail-run/components/content/helloworld`

   ![copiar-imagem-diálogo](assets/copy-image-dialog.gif)

1. **Atualize a caixa de diálogo Hello World para incluir uma guia para a mensagem.**

   Atualize a caixa de diálogo para que corresponda ao seguinte. A estrutura do nó JCR da caixa de diálogo final é apresentada abaixo em XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
       jcr:primaryType="nt:unstructured"
       jcr:title="Hello World"
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content
           jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/coral/foundation/tabs"
           size="L">
           <items jcr:primaryType="nt:unstructured">
               <message
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Message"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <message
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/textfield"
                                   fieldDescription="Message for component to display"
                                   fieldLabel="Message"
                                   name="./message"/>
                           </items>
                       </column>
                   </items>
               </message>
               <sequence
                   jcr:primaryType="nt:unstructured"
                   jcr:title="Sequence"
                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns">
                   <items jcr:primaryType="nt:unstructured">
                       <column
                           jcr:primaryType="nt:unstructured"
                           sling:resourceType="granite/ui/components/coral/foundation/container">
                           <items jcr:primaryType="nt:unstructured">
                               <duration
                                   jcr:primaryType="nt:unstructured"
                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield"
                                   defaultValue=""
                                   fieldDescription="Amount of time the image will be shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (ms)"
                                   min="0"
                                   name="./duration"/>
                           </items>
                       </column>
                   </items>
               </sequence>
           </items>
       </content>
   </jcr:root>
   ```

   O campo de texto para a Mensagem será salvo em uma propriedade chamada `message` e o campo de número para a Duração será salvo em uma propriedade chamada `duration`. Essas duas propriedades são referenciadas em `/apps/weretail-run/components/content/helloworld/production.html` pelo HTL como `${properties.message}` e `${properties.duration}`.

   ![Hello World - diálogo concluído](assets/2018-04-29_at_5_21pm.png)

   Hello World - diálogo concluído

## Criar bibliotecas do lado do cliente {#clientlibs}

As bibliotecas do lado do cliente fornecem um mecanismo para organizar e gerenciar arquivos CSS e JavaScript necessários para uma implementação de AEM.

Os componentes do AEM Screens são renderizados de forma diferente no modo de Edição e no modo de Visualização/Produção. Duas bibliotecas de clientes serão criadas, uma para o modo Editar e outra para Visualização/Produção.

1. Crie uma pasta para bibliotecas do lado do cliente para o componente Hello World.

   Abaixo de `/apps/weretail-run/components/content/helloworld`crie uma nova pasta chamada `clientlibs`.

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. Abaixo da pasta `clientlibs` crie um novo nó chamado `shared` do tipo `cq:ClientLibraryFolder.`

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. Adicione as seguintes propriedades à biblioteca do cliente compartilhada:

   * `allowProxy` | Booleano | `true`

   * `categories`| String[] |  `cq.screens.components`

   ![Propriedades para /apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Propriedades para /apps/weretail-run/components/content/helloworld/clientlibs/shared

   A propriedade categories é uma string que identifica a biblioteca do cliente. A categoria cq.screens.components é usada no modo Editar e Visualizar/Produção. Portanto, qualquer CSS/JS definido no sharedclientlib é carregado em todos os modos.

   É uma prática recomendada nunca expor nenhum caminho diretamente para /apps em um ambiente de produção. A propriedade allowProxy garante que a biblioteca do cliente CSS e JS sejam referenciadas por meio de um prefixo of/etc.clientlibs.

1. Crie o arquivo com o nome `css.txt` abaixo da pasta compartilhada.

   Preencha o arquivo com o seguinte:

   ```
   #base=css
   
   styles.less
   ```

1. Crie uma pasta chamada `css` abaixo da pasta `shared`. Adicione um arquivo com o nome `style.less` abaixo da pasta `css`. A estrutura das bibliotecas de clientes agora deve ser semelhante a esta:

   ![2018-04-30_at_3_11pm](assets/2018-04-30_at_3_11pm.png)

   Em vez de escrever CSS diretamente, este tutorial usa MENOS. [](https://lesscss.org/) O LESS é um popular pré-compilador de CSS compatível com variáveis, mixins e funções de CSS. AEM bibliotecas de clientes oferecem suporte nativo a menos compilação. É possível utilizar software ou outros pré-compiladores, mas é necessário compilá-los fora do AEM.

1. Preencha `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` com o seguinte:

   ```css
   /**
       Shared Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less
   
   **/
   
   .cmp-hello-world {
       background-color: #fff;
   
    &__message {
     color: #000;
     font-family: Helvetica;
     text-align:center;
    }
   }
   ```

1. Copie e cole a pasta `shared` da biblioteca do cliente para criar uma nova biblioteca do cliente chamada `production`.

   ![Copie a biblioteca do cliente compartilhada para criar uma nova biblioteca do cliente de produção](assets/copy-clientlib.gif)

   Copie a biblioteca do cliente compartilhada para criar uma nova biblioteca do cliente de produção

1. Atualize a propriedade `categories` da biblioteca de clientes de produção para ser `cq.screens.components.production.`

   Isso garante que os estilos sejam carregados somente no modo de Visualização/Produção.

   ![Propriedades para /apps/weretail-run/components/content/helloworld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propriedades para /apps/weretail-run/components/content/helloworld/clientlibs/production

1. Preencha `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` com o seguinte:

   ```css
   /**
       Production Styles
      /apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less
   
   **/
   .cmp-hello-world {
   
       height: 100%;
       width: 100%;
       position: fixed;
   
    &__message {
   
     position: relative;
     font-size: 5rem;
     top:25%;
    }
   }
   ```

   Os estilos acima exibirão a mensagem centralizada no meio da tela, mas somente no modo de produção.

Uma terceira categoria de biblioteca de clientes: `cq.screens.components.edit` pode ser usado para adicionar estilos específicos somente edição ao componente.

| Categoria Clientlib | Uso |
|---|---|
| `cq.screens.components` | Estilos e scripts compartilhados entre os modos de edição e produção |
| `cq.screens.components.edit` | Estilos e scripts que são usados apenas no modo de edição |
| `cq.screens.components.production` | Estilos e scripts que são usados apenas no modo de produção |

## Criar uma página de design {#design-page}

O AEM Screens usa [Modelos de página estáticos](https://helpx.adobe.com/br/experience-manager/6-5/sites/developing/using/page-templates-static.html) e [Configurações de design](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/default-components-designmode.html) para alterações globais. As configurações de design são usadas frequentemente para configurar os componentes permitidos para o Parsys em um canal. Uma prática recomendada é armazenar essas configurações de maneira específica do aplicativo.

Abaixo de uma página de Design de execução We.Retail é criada e armazenará todas as configurações específicas do projeto Execução We.Retail.

1. Em **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs` navegue até `/apps/settings/wcm/designs`
1. Crie um novo nó abaixo da pasta de designs, chamado `we-retail-run` com um tipo de `cq:Page`.
1. Abaixo da página `we-retail-run`, adicione outro nó chamado `jcr:content` do tipo `nt:unstructured`. Adicione as seguintes propriedades ao nó `jcr:content`:

   | Nome | Tipo | Valor |
   |---|---|---|
   | jcr:title | Sequência de caracteres | Execução We.Retail |
   | sling:resourceType | Sequência de caracteres | wcm/core/components/designer |
   | cq:doctype | Sequência de caracteres | html_5 |

   ![Página de design em /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   Página de design em /apps/settings/wcm/designs/we-retail-run

## Criar um Canal de Sequência {#create-sequence-channel}

O componente Hello World deve ser usado em um Canal de sequência. Para testar o componente, um novo Canal de sequência é criado.

1. No menu Iniciar AEM, navegue até **Screens** > **We.Retail Ru** n > e selecione **Canais**.

1. Clique no botão **Criar**

   1. Escolha **Criar Entidade**

   ![2018-04-30_at_5_18](assets/2018-04-30_at_5_18pm.png)

1. No assistente Criar :

1. Etapa do modelo - escolha **Canal de sequência**

   1. Etapa Propriedades
   * Guia Básica > Título = **Canal Ocioso**
   * Guia Canal > marque **Tornar canal online**

   ![canal inativo](assets/idle-channel.gif)

1. Abra as propriedades da página para o Canal inativo. Atualize o campo Design para apontar para `/apps/settings/wcm/designs/we-retail-run,`a página de design criada na seção anterior.

   ![Configuração de design /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   Configuração de design apontando para /apps/settings/wcm/designs/we-retail-run

1. Edite o Canal ocioso recém-criado para abri-lo.

1. Alterne o modo de página para Modo **Design**

   1. Clique no ícone **chave** no Parsys para configurar os componentes permitidos

   1. Selecione o grupo **Screens** e o grupo **Execução We.Retail - Content**.

   ![2018-04-30_at_5_43](assets/2018-04-30_at_5_43pm.png)

1. Alterne o modo da página para **Edit**. O componente Hello World agora pode ser adicionado à página e combinado com outros componentes de canal de sequência.

   ![2018-04-30_at_5_53](assets/2018-04-30_at_5_53pm.png)

1. Em **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par` navegue até `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. Observe que a propriedade `components` agora inclui `group:Screens`, `group:We.Retail Run - Content`.

   ![Configuração de design em /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1_14pm.png)

   Configuração de design em /apps/settings/wcm/designs/we-retail-run

## Modelo para Manipuladores Personalizados {#custom-handlers}

Caso seu componente personalizado esteja usando recursos externos, como ativos (imagens, vídeos, fontes, ícones, etc.), representações de ativos específicos ou bibliotecas do lado do cliente (css, js, etc.), eles não serão adicionados automaticamente à configuração offline, pois apenas agrupamos a marcação HTML por padrão.

Para permitir que você personalize e otimize os ativos exatos que são baixados no reprodutor, oferecemos um mecanismo de extensão para componentes personalizados para expor suas dependências à lógica de cache offline no Screens.

A seção abaixo mostra o modelo para manipuladores de recursos offline personalizados e os requisitos mínimos no `pom.xml` para esse projeto específico.

```java
package …;

import javax.annotation.Nonnull;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceUtil;
import org.apache.sling.api.resource.ValueMap;

import com.adobe.cq.screens.visitor.OfflineResourceHandler;

@Service(value = OfflineResourceHandler.class)
@Component(immediate = true)
public class MyCustomHandler extends AbstractResourceHandler {

 @Reference
 private …; // OSGi services injection

 /**
  * The resource types that are handled by the handler.
  * @return the handled resource types
  */
 @Nonnull
 @Override
 public String[] getSupportedResourceTypes() {
     return new String[] { … };
 }

 /**
  * Accept the provided resource, visit and traverse it as needed.
  * @param resource The resource to accept
  */
 @Override
 public void accept(@Nonnull Resource resource) {
     ValueMap properties = ResourceUtil.getValueMap(resource);
     
     /* You can directly add explicit paths for offline caching using the `visit`
        method of the visitor. */
     
     // retrieve a custom property from the component
     String myCustomRenditionUrl = properties.get("myCustomRenditionUrl", String.class);
     // adding that exact asset/rendition/path to the offline manifest
     this.visitor.visit(myCustomRenditionUrl);
     
     
     /* You can delegate handling for dependent resources so they are also added to
        the offline cache using the `accept` method of the visitor. */
     
     // retrieve a referenced dependent resource
     String referencedResourcePath = properties.get("myOtherResource", String.class);
     ResourceResolver resolver = resource.getResourceResolver();
     Resource referencedResource = resolver.getResource(referencedResourcePath);
     // let the handler for that resource handle it
     if (referencedResource != null) {
         this.visitor.accept(referencedResource);
     }
   }
}
```

O código a seguir fornece os requisitos mínimos no `pom.xml` para o projeto específico:

```css
   <dependencies>
        …
        <!-- Felix annotations -->
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.9.0</version>
            <scope>provided</scope>
        </dependency>

        <!-- Screens core bundle with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.cq.screens</groupId>
            <artifactId>com.adobe.cq.screens</artifactId>
            <version>1.5.90</version>
            <scope>provided</scope>
        </dependency>
        …
      </dependencies>
```

## Colocando tudo junto {#putting-it-all-together}

O vídeo abaixo mostra o componente finalizado e como ele pode ser adicionado a um canal de Sequência. O Canal é adicionado a uma exibição Local e, em última análise, atribuído a um player do Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Código finalizado {#finished-code}

Abaixo está o código concluído do tutorial. Os **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** são os pacotes AEM compilados. O **SRC-screens-weretail-run-0.0.1.zip **é o código-fonte não compilado que pode ser implantado usando o Maven.

[Obter arquivo](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Obter arquivo](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Obter arquivo](assets/screens-weretail-run.zip)
