---
title: Desenvolvimento de um componente personalizado para o AEM Screens
description: Saiba como criar um componente personalizado para o AEM Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
targetaudience: target-audience new
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: d14f8c55-dc09-4ac9-8d75-bafffa82ccc0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 1%

---

# Desenvolvimento de um componente personalizado para o AEM Screens {#developing-a-custom-component-for-aem-screens}

O tutorial a seguir percorre as etapas para criar um componente personalizado para o AEM Screens. A AEM Screens reutiliza muitos padrões e tecnologias de design existentes de outros produtos da AEM. O tutorial destaca as diferenças e considerações especiais ao desenvolver para o AEM Screens.

## Visão geral {#overview}

Este tutorial destina-se a desenvolvedores novos no AEM Screens. Neste tutorial, um componente simples &quot;Olá, mundo&quot; é criado para um canal de sequência no AEM Screens. Uma caixa de diálogo permite que os autores atualizem o texto exibido.

![amostra](assets/overviewhellow.png)

## Pré-requisitos {#prerequisites}

Para concluir este tutorial, é necessário o seguinte:

1. [AEM 6.5](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes) e Pacote de Recursos mais recente do Screens.

1. [AEM Screens Player](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction)
1. Ambiente de desenvolvimento local

As etapas e capturas de tela do tutorial são executadas usando o **CRXDE-Lite**. IDEs também podem ser usados para concluir o tutorial. Mais informações sobre o uso de um IDE para desenvolver [com o AEM podem ser encontradas aqui.](https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)


## Configuração do projeto {#project-setup}

O código-fonte de um projeto Screens geralmente é gerenciado como um projeto Maven de vários módulos. Para acelerar o tutorial, um projeto foi pré-gerado usando o [Arquétipo de Projetos AEM 13](https://github.com/adobe/aem-project-archetype). Mais detalhes sobre [a criação de um projeto com o Maven AEM Project Archetype podem ser encontrados aqui](https://experienceleague.adobe.com/pt-br/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup).

1. Baixe e instale os seguintes pacotes usando o [Gerenciador de Pacotes do CRX](http://localhost:4502/crx/packmgr/index.jsp):

[Obter arquivo](assets/base-screens-weretail-runuiapps-001-snapshot.zip)

   [Obter arquivo](assets/base-screens-weretail-runuicontent-001-snapshot.zip)
   **Opcionalmente** Se estiver trabalhando com o Eclipse ou outro IDE, baixe o pacote de origem abaixo. Implante o projeto em uma instância local do AEM usando o comando Maven:

   **`mvn -PautoInstallPackage clean install`**

   Inicie o projeto de execução `We.Retail` do HelloWorld SRC Screens.

[Obter arquivo](assets/src-screens-weretail-run.zip)

1. No [Gerenciador de Pacotes do CRX](http://localhost:4502/crx/packmgr/index.jsp), verifique se os dois pacotes a seguir estão instalados:

   1. **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip**
   1. **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip**

   ![Screens We.Retail Execute pacotes Ui.Apps e Ui.Content instalados por meio do Gerenciador de Pacotes do CRX](assets/crx-packages.png)

   Screens `We.Retail` Execute pacotes `Ui.Apps` e `Ui.Content` instalados por meio do Gerenciador de Pacotes do CRX.

1. O pacote **screens-weretail-run.ui.apps** instala o código abaixo de `/apps/weretail-run`.

   Este pacote contém o código responsável pela renderização dos componentes personalizados do projeto. Esse pacote inclui o código do componente e qualquer JavaScript ou CSS necessário. Este pacote também incorpora o **screens-weretail-run.core-0.0.1-SNAPSHOT.jar** que contém qualquer código Java™ necessário ao projeto.

   >[!NOTE]
   >
   >Neste tutorial, nenhum código Java™ é gravado. Se uma lógica de negócios mais complexa for necessária, o Java™ de back-end pode ser criado e implantado usando o pacote Core Java™.

   ![Representação do código ui.apps no CRXDE Lite](assets/uipps-contents.png)

   Representação do código ui.apps no CRXDE Lite

   O componente **Olá, mundo** é apenas um espaço reservado. Ao longo do tutorial, uma funcionalidade é adicionada, permitindo que um autor atualize a mensagem exibida pelo componente.

1. O pacote **screens-weretail-run.ui.content** instala o código abaixo de:

   * `/conf/we-retail-run`
   * `/content/dam/we-retail-run`
   * `/content/screens/we-retail-run`

   Este pacote contém o conteúdo inicial e a estrutura de configuração necessária para o projeto. **`/conf/we-retail-run`** contém todas as configurações para o projeto de execução `We.Retail`. **`/content/dam/we-retail-run`** inclui iniciar ativos digitais para o projeto. **`/content/screens/we-retail-run`** contém a estrutura de conteúdo do Screens. O conteúdo de todos esses caminhos é atualizado principalmente no AEM. Para promover a consistência entre ambientes (local, desenvolvimento, preparo, produção), geralmente uma estrutura de conteúdo básica é salva no controle de origem.

1. **Navegue até AEM Screens > `We.Retail` Executar projeto:**

   No menu Iniciar do AEM, clique no ícone Screens. Verifique se `We.Retail` Executar projeto está sendo visto.

   ![we-retail-run-starter](assets/we-retaiul-run-starter.png)

## Criar o componente Hello World {#hello-world-cmp}

O componente Olá, mundo é um componente simples que permite que um usuário insira uma mensagem a ser exibida na tela. O componente é baseado no [Modelo de Componente do AEM Screens: https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template).

O AEM Screens tem algumas restrições interessantes que não são necessariamente verdadeiras para componentes WCM tradicionais do Sites.

* A maioria dos componentes do Screens deve ser executada em tela cheia nos dispositivos de sinalização digital de destino
* A maioria dos componentes do Screens deve ser incorporável nos canais de sequência para gerar apresentações de slides
* A criação deve permitir a edição de componentes individuais em um canal de sequência, portanto, renderizá-los em tela cheia está fora de questão

1. No **CRXDE-Lite** `http://localhost:4502/crx/de/index.jsp` (ou IDE de escolha), navegue até `/apps/weretail-run/components/content/helloworld.`

   Adicionar as seguintes propriedades ao componente `helloworld`:

   ```
       jcr:title="Hello World"
       sling:resourceSuperType="foundation/components/parbase"
       componentGroup="We.Retail Run - Content"
   ```

   ![Propriedades de /apps/weretail-run/components/content/helloworld](assets/2018-04-28_at_4_23pm.png)

   Propriedades de /apps/weretail-run/components/content/helloworld

   O componente **Olá, mundo** estende o componente **foundation, components, parbase** para que ele possa ser usado corretamente dentro de um canal de Sequência.

1. Criar um arquivo abaixo de `/apps/weretail-run/components/content/helloworld` chamado `helloworld.html.`

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

   Os componentes do Screens exigem duas renderizações diferentes, dependendo de qual [modo de criação](https://experienceleague.adobe.com/pt-br/docs/experience-manager-64/authoring/authoring/author-environment-tools) está sendo usado:

   1. **Produção**: modo de Visualização ou Publicação (wcmmode=disabled)
   1. **Editar**: usado para todos os outros modos de criação, ou seja, editar, design, andaime, desenvolvedor...

   `helloworld.html`age como uma opção, verificando qual modo de criação está ativo e redirecionando para outro script HTL. Uma convenção comum usada por componentes de telas é ter um script `edit.html` para o modo de Edição e um script `production.html` para o modo de Produção.

1. Criar um arquivo abaixo de `/apps/weretail-run/components/content/helloworld` chamado `production.html.`

   Preencha o arquivo com o seguinte:

   ```xml
   <!--/*
    /apps/weretail-run/components/content/helloworld/production.html
   
   */-->
   
   <div data-duration="${properties.duration}" class="cmp-hello-world">
    <h1 class="cmp-hello-world__message">${properties.message}</h1>
   </div>
   ```

   O conteúdo acima é a marcação de produção do componente Hello World. Um atributo `data-duration` foi incluído, pois o componente é usado em um canal de Sequência. O atributo `data-duration` é usado pelo canal Sequência para saber por quanto tempo um item de sequência deve ser exibido.

   O componente renderiza uma marca `div` e uma marca `h1` com texto. `${properties.message}` é uma parte do script HTL que gera o conteúdo de uma propriedade JCR chamada `message`. Uma caixa de diálogo será criada posteriormente permitindo que um usuário insira um valor para o texto de propriedade `message`.

   Observe também que a notação BEM (Block Element Modifier) é usada com o componente. BEM é uma convenção de codificação CSS que facilita a criação de componentes reutilizáveis. BEM é a notação usada pelos [Componentes principais do AEM](https://github.com/adobe/aem-core-wcm-components/wiki/CSS-coding-conventions). <!-- DEAD LINK More info can be found at: [https://getbem.com/](https://getbem.com/) -->

1. Criar um arquivo abaixo de `/apps/weretail-run/components/content/helloworld` chamado `edit.html.`

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

   A tabela acima é a marcação editada para o componente Hello World. O primeiro bloco exibe uma versão editada do componente se a mensagem de diálogo tiver sido preenchida.

   O segundo bloco é renderizado se nenhuma mensagem de caixa de diálogo for inserida. O `cq-placeholder` e o `data-emptytext` renderizam o rótulo ***Olá, mundo*** como um espaço reservado nesse caso. A string do rótulo pode ser internacionalizada usando i18n para oferecer suporte à criação em vários locais.

1. **A caixa de diálogo Copiar Imagem do Screens a ser usada para o componente Olá, Mundo.**

   É mais fácil começar com uma caixa de diálogo existente e, em seguida, fazer modificações.

   1. Copiar a caixa de diálogo de: `/libs/screens/core/components/content/image/cq:dialog`
   1. Colar a caixa de diálogo abaixo de `/apps/weretail-run/components/content/helloworld`

   ![copiar-imagem-caixa-de-diálogo](assets/copy-image-dialog.gif)

1. **Atualize a caixa de diálogo Olá, Mundo, para incluir uma guia para a mensagem.**

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
                                   fieldDescription="Amount of time the image is shown in the sequence, in milliseconds"
                                   fieldLabel="Duration (milliseconds)"
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

   O campo de texto da Mensagem é salvo em uma propriedade chamada `message` e o campo de número da Duração é salvo em uma propriedade chamada `duration`. Essas duas propriedades são referenciadas em `/apps/weretail-run/components/content/helloworld/production.html` pelo HTL como `${properties.message}` e `${properties.duration}`.

   ![Olá, Mundo - caixa de diálogo concluída](assets/2018-04-29_at_5_21pm.png)

   Olá, mundo - caixa de diálogo concluída

## Criar bibliotecas do lado do cliente {#clientlibs}

As bibliotecas do lado do cliente fornecem um mecanismo para organizar e gerenciar arquivos CSS e JavaScript necessários para uma implementação do AEM.

Os componentes do AEM Screens são renderizados de forma diferente no modo de Edição vs. no modo de Pré-visualização-Produção. Duas bibliotecas de clientes são criadas: uma para o modo Editar e a segunda para o modo Pré-visualização-Produção.

1. Crie uma pasta para bibliotecas do lado do cliente para o componente Hello World.

   Abaixo de `/apps/weretail-run/components/content/helloworld`, crie uma pasta chamada `clientlibs`.

   ![2018-04-30_at_1046am](assets/2018-04-30_at_1046am.png)

1. Abaixo da pasta `clientlibs`, crie um nó chamado `shared` do tipo `cq:ClientLibraryFolder`.

   ![2018-04-30_at_1115am](assets/2018-04-30_at_1115am.png)

1. Adicione as seguintes propriedades à biblioteca de cliente compartilhada:

   * `allowProxy` | Booleano | `true`

   * `categories`| Cadeia de caracteres[] | `cq.screens.components`

   ![Propriedades de /apps/weretail-run/components/content/helloworld/clientlibs/shared](assets/2018-05-03_at_1026pm.png)

   Propriedades de /apps/weretail-run/components/content/helloworld/clientlibs/shared

   A propriedade categories é uma string que identifica a biblioteca do cliente. A categoria cq.screens.components é usada nos modos Editar e Visualizar produção. Portanto, qualquer CSS ou JS definido em sharedclientlib é carregado em todos os modos.

   Como prática recomendada, qualquer caminho diretamente para `/apps` em um ambiente de produção nunca deve ser exposto. A propriedade allowProxy garante que o CSS e o JS da biblioteca do cliente sejam referenciados por meio de um prefixo `/etc.clientlibs`.

1. Crie o arquivo chamado `css.txt` abaixo da pasta compartilhada.

   Preencha o arquivo com o seguinte:

   ```
   #base=css
   
   styles.less
   ```

1. Crie uma pasta chamada `css` abaixo da pasta `shared`. Adicione um arquivo chamado `style.less` abaixo da pasta `css`. A estrutura das bibliotecas de clientes agora deve ficar assim:

   ![2018-04-30_às_3_11h](assets/2018-04-30_at_3_11pm.png)

   Em vez de escrever CSS diretamente, este tutorial usa MENOS. [LESS](https://lesscss.org/) é um pré-compilador de CSS popular que oferece suporte a variáveis, mixins e funções de CSS. As bibliotecas de clientes do AEM oferecem suporte nativo à compilação LESS. Você pode usar o Sass ou outros pré-compiladores, mas deve compilá-los fora do AEM.

1. Popular `/apps/weretail-run/components/content/helloworld/clientlibs/shared/css/styles.less` com o seguinte:

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

1. Copie e cole a pasta da biblioteca cliente `shared` para criar uma biblioteca cliente chamada `production`.

   ![Copie a biblioteca de cliente compartilhada para criar uma nova biblioteca de cliente de produção](assets/copy-clientlib.gif)

   Copie a biblioteca de cliente compartilhada para criar uma biblioteca de cliente de produção.

1. Atualize a propriedade `categories` da biblioteca de cliente de produção para `cq.screens.components.production.`

   Isso garante que os estilos só sejam carregados quando estiverem no modo de Pré-visualização-produção.

   ![Propriedades de /apps/weretail-run/components/content/helloworld/clientlibs/production](assets/2018-04-30_at_5_04pm.png)

   Propriedades de `/apps/weretail-run/components/content/helloworld/clientlibs/production`.

1. Popular `/apps/weretail-run/components/content/helloworld/clientlibs/production/css/styles.less` com o seguinte:

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

   Os estilos acima exibem a mensagem centralizada no meio da tela, mas somente no modo de Produção.

Uma terceira categoria de biblioteca cliente: `cq.screens.components.edit` pode ser usada para adicionar estilos específicos somente Edição ao componente.

| Categoria do Clientlib | Uso |
|---|---|
| `cq.screens.components` | Estilos e scripts compartilhados entre os modos de edição e de produção |
| `cq.screens.components.edit` | Estilos e scripts que são usados somente no modo de edição |
| `cq.screens.components.production` | Estilos e scripts que são usados somente no modo de produção |

## Criar uma página de design {#design-page}

O AEM Screens usa [Modelos de página estáticos](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-static) e [Configurações de design](https://experienceleague.adobe.com/pt-br/docs/experience-manager-64/authoring/siteandpage/default-components-designmode) para alterações globais. As configurações de design são usadas com frequência para configurar componentes permitidos para o Parsys em um canal. Uma prática recomendada é armazenar essas configurações de uma maneira específica do aplicativo.

Abaixo de uma página de Design de Execução `We.Retail`, criada, que armazena todas as configurações específicas do projeto de Execução `We.Retail`.

1. Em **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs`, navegue até `/apps/settings/wcm/designs`.
1. Crie um nó abaixo da pasta de designs, chamado `we-retail-run`, com um tipo de `cq:Page`.
1. Abaixo da página `we-retail-run`, adicione outro nó chamado `jcr:content` do tipo `nt:unstructured`. Adicione as seguintes propriedades ao nó `jcr:content`:

   | Nome | Tipo | Valor |
   |---|---|---|
   | `jcr:title` | String | `We.Retail` Executar |
   | `sling:resourceType` | String | `wcm`, `core`, `components`, `designer` |
   | `cq:doctype` | String | html_5 |

   ![Página de Design em /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1219pm.png)

   Página de Design em `/apps/settings/wcm/designs/we-retail-run`.

## Criar um canal de sequência {#create-sequence-channel}

O componente Hello World é para uso em um canal de sequência. Para testar o componente, um novo canal de sequência é criado.

1. No menu Iniciar do AEM, navegue até **Screens** > **`We.Retail`Executar** > e clique em **Canais**.

1. Clique no botão **Criar**

   1. Escolher **Criar Entidade**

   ![2018-04-30_às_5_18h](assets/2018-04-30_at_5_18pm.png)

1. No assistente Criar:

1. Etapa de Modelo - escolher **Canal de Sequência**

   1. Etapa Propriedades

   * Guia Básica > Título = **Canal Ocioso**
   * Guia Canal > verificar **Tornar o canal online**

   ![canal ocioso](assets/idle-channel.gif)

1. Abra as propriedades de página do Canal ocioso.
1. Atualize o campo Design para que ele aponte para `/apps/settings/wcm/designs/we-retail-run`, a página de design criada na seção anterior.

   ![Configuração de design /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1240pm.png)

   Configuração de design apontando para /apps/settings/wcm/designs/we-retail-run

1. Edite o canal ocioso recém-criado para que você possa abri-lo.

1. Mudar o modo de página para o Modo de **Design**.

   1. Clique na **chave inglesa** no Parsys para poder configurar os componentes permitidos.

   1. Clique no grupo **Screens** e no grupo **`We.Retail`Executar - Conteúdo**.

   ![2018-04-30_às_5_43h](assets/2018-04-30_at_5_43pm.png)

1. Mudar o modo de página para **Editar**. O componente Olá, mundo agora pode ser adicionado à página e combinado com outros componentes do canal de sequência.

   ![2018-04-30_às_5_53h](assets/2018-04-30_at_5_53pm.png)

1. Em **CRXDE Lite** `http://localhost:4502/crx/de/index.jsp#/apps/settings/wcm/designs/we-retail-run/jcr%3Acontent/sequencechannel/par`, navegue até `/apps/settings/wcm/designs/we-retail-run/jcr:content/sequencechannel/par`. Observe que a propriedade `components` agora inclui `group:Screens`, `group:We.Retail Run - Content`.

   ![Configuração de design em /apps/settings/wcm/designs/we-retail-run](assets/2018-05-07_at_1_14pm.png)

   Configuração de design em /apps/settings/wcm/designs/we-retail-run

## Modelo para manipuladores personalizados {#custom-handlers}

Se o componente personalizado usar recursos externos, como ativos (imagens, vídeos, fontes e ícones), representações de ativos específicas ou bibliotecas do lado do cliente (css e js), esses recursos não serão adicionados automaticamente à configuração offline. O motivo é porque somente a marcação HTML é agrupada por padrão.

Para permitir personalizar e otimizar os ativos exatos que são baixados no reprodutor, o Adobe oferece um mecanismo de extensão. Esse mecanismo permite que os componentes personalizados exponham suas dependências à lógica de cache offline no AEM Screens.

A seção abaixo mostra o modelo para manipuladores de recursos offline personalizados. Ela também mostra os requisitos mínimos no `pom.xml` para esse projeto específico.

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

O código a seguir fornece os requisitos mínimos em `pom.xml` para esse projeto específico:

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

**OBSERVAÇÃO**: se houver AEM as a Cloud Service, use a dependência abaixo em `pom.xml` para esse projeto específico.

```css
   <dependencies>
        …
        <!-- AEM Screens SDK API with OfflineResourceHandler/AbstractResourceHandler -->
        <dependency>
            <groupId>com.adobe.aem</groupId>
            <artifactId>aem-screens-sdk-api</artifactId>
            <version>1.0.8</version>
        </dependency>
        …
      </dependencies>
```

## Tudo junto na prática {#putting-it-all-together}

O vídeo abaixo mostra o componente concluído e como ele pode ser adicionado a um canal de sequência. O Canal é então adicionado a uma exibição de Localização e, por fim, atribuído a um reprodutor do Screens.

>[!VIDEO](https://video.tv.adobe.com/v/22385?quaity=9)

## Outras considerações para componentes personalizados que incorporam outras páginas ou fragmentos {#additional-considerations}

Se o objetivo do componente personalizado for incluir outras páginas ou Fragmentos de experiência e você quiser que as alterações no conteúdo incorporado sejam selecionadas automaticamente pelo reprodutor, sem republicar o canal, considere estas duas restrições:

1. Em vez de estender diretamente `foundation/components/parbase`, você teria que estender `screens/core/components/content/page` ou `screens/core/components/content/experiencefragment`
2. O nome da propriedade que você usa para referenciar o conteúdo inserido deve ser `pagePath`.

O uso desses dois componentes principais do Screens também traz o benefício adicional de que eles podem cuidar do agrupamento de algumas dependências que você precisa (bibliotecas do lado do cliente, fontes e assim por diante). Essa funcionalidade é feita por meio das opções de configuração offline na caixa de diálogo do componente. Em seguida, reduz a responsabilidade de qualquer manipulador off-line personalizado que você teria que usar para ele. Às vezes, pode até mesmo eliminar completamente a necessidade de usar um em primeiro lugar.

## Código concluído {#finished-code}

Abaixo está o código concluído do tutorial. Os **screens-weretail-run.ui.apps-0.0.1-SNAPSHOT.zip** e **screens-weretail-run.ui.content-0.0.1-SNAPSHOT.zip** são os pacotes compilados do AEM. O **SRC-screens-weretail-run-0.0.1.zip &#x200B;** é o código-fonte não compilado que pode ser implantado usando Maven.

[Obter arquivo](assets/screens-weretail-runuiapps-001-snapshot.zip)

[Obter arquivo](assets/screens-weretail-runuicontent-001-snapshot.zip)

[Obter arquivo](assets/screens-weretail-run.zip)
