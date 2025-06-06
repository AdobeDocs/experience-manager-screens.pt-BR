---
title: Criação de modelos personalizados em layouts de várias zonas
description: Saiba mais sobre como criar modelos personalizados em layouts MultiZone para AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 3f4813f8-0438-4ce0-9046-84025de0ddd1
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 1%

---

# Criação de modelos personalizados para layouts de várias zonas {#creating-custom-templates-multizone}

Esta página mostra como criar um modelo personalizado para um layout de várias zonas.

## Considerações importantes {#considerations}

Há duas considerações importantes que você deve estar ciente antes de criar um modelo personalizado em um layout de várias zonas:

1. **Tamanho ou Porcentagens de Pixel Fixo**:

   Decida se deseja usar tamanho de pixel fixo para zonas diferentes para o layout personalizado ou se deseja criar um layout personalizado usando porcentagens.

   >[!NOTE]
   >A vantagem de usar a porcentagem para definir zonas para o layout personalizado permite reutilizar o modelo em vários tamanhos de tela.

1. **Convenção de Nomenclatura**:

   Ajuda a entender como criar modelos de várias zonas personalizados para usar em um projeto do AEM Screens. Mas primeiro, você deve entender a terminologia dos modelos que deseja criar.

   | **Nome do layout** | **Descrição** |
   |---|---|
   | `Left20-LandscapeHD3Zone` | Um layout de paisagem de três zonas que permite criar três zonas: <br>* Zona 1 como 20% da tela horizontal e vertical da esquerda<br>* Zona 2 como 80% da tela horizontal e 20% da tela vertical justificada à direita<br>* Zona 3 como 100% da tela horizontal e 80% da tela vertical. A taxa de proporção é de 16:9 |
   | `Upper20-PortraitHD2Zone` | Um modelo em forma de retrato de duas zonas, que cobre 20% da tela a partir da parte superior, com uma proporção de 16:9 |
   | `Right20-LandscapeSD3Zone` | Um modelo de três zonas que cobre 20% da tela à direita, com uma proporção de 4:3 |

   >[!IMPORTANT]
   >As zonas definidas no layout personalizado podem não corresponder à taxa de proporção geral do layout inteiro. A convenção de nomenclatura seguida neste documento especifica a proporção do layout personalizado como um todo.

## Exemplo de layout de caso de uso `Left20-LandscapeHD3Zone` {#custom-template-one}

Siga a seção abaixo para criar um modelo personalizado *`Left20-LandscapeHD3Zone`* com a seguinte configuração:

* **`Left20`** - A zona superior à esquerda cobrindo 20% do tamanho da tela horizontal e vertical.
* **`Landscape`** - Orientação da tela.
* **`HD`** - Taxa de proporção como 16:9.
* **`3Zone`** - Três zonas da exibição.

## Representação visual do layout de várias zonas {#multi-layout-visual-one}

O layout `Left20-LandscapeHD3Zone` permite criar o seguinte layout de várias zonas no seu projeto:

![imagem](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Criando um layout `Left20-LandscapeHD3Zone` {#landscape-layout-one}

Siga as etapas abaixo para criar um Layout `Left20-LandscapeHD3Zone` para um projeto AEM Screens.

1. Crie um projeto do AEM Screens chamado **`customtemplate`**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Navegue até **CRXDE Lite** da instância AEM > Ferramentas > **CRXDE Lite**.

1. Crie uma pasta em **aplicativos** com o título **`customtemplate`**. Da mesma forma, crie outra pasta denominada **modelo** em **`customtemplate`**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >Clique em **Salvar tudo** na barra de ações do CRXDE Lite sempre que criar, editar ou copiar conteúdo para qualquer um dos nós. Caso contrário, não será possível confirmar as atualizações.

1. Copie o modelo lbar-left de `/libs/screens/core/templates/splitscreenchannel/lbar-left` para `/apps/customtemplate/template`.

1. Renomeie a **lbar-left** (`/apps/customtemplate/template`) copiada para **my-custom-layout**.
   ![imagem](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Navegue até `/apps/customtemplate/template/my-custom-layout` e atualize as propriedades **`jcr:description`** para *Modelo para`Left20-LandscapeHD3Zone`* e **`jcr:title`** para *`Left20-LandscapeHD3Zone`*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Navegue até o nó **`offline-config`** em `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e atualize o **`jcr:title`** para *`Left20-LandscapeHD3Zone`*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Navegue até a propriedade *`jcr:content`* de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` e atualize a propriedade **`cq:cssClass`** para poder usar **aem-Layout my-custom-layout**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Referindo-se à etapa (4) na qual você copiou o modelo de barra esquerda, é possível visualizar três grades responsivas em `my-custom-layout/jcr:content`. Adicione a classe css personalizada a cada grade responsiva na propriedade *`cq:cssClass`*, por exemplo, *my-custom-layout-top-left* para o nó *r1c1*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Da mesma forma, adicione *my-custom-layout-top-right* para *r1c2* e *my-custom-layout-bottom* para o nó *r2c1*.

   >[!NOTE]
   >Essas classes personalizadas são usadas no css para definir a largura/altura dessas grades responsivas.

   >[!NOTE]
   >É possível adicionar ou remover as grades responsivas com base no número total de grades desejadas. Neste exemplo, duas grades na primeira linha e uma grade na segunda linha são exibidas, portanto, há um total de três grades responsivas (r1c1, r1c2, r2c1).

1. Copie `/libs/settings/wcm/designs/screens` para `/apps/settings/wcm/designs/` e renomeie o design copiado como **custom-template-designs**.

1. Navegue até `/apps/settings/wcm/designs/custom-template-designs` e atualize a propriedade *`jcr:title`* de **custom-template-designs** para **customtemplate-design**.

1. Navegue até `/apps/settings/wcm/designs/custom-template-designs` e crie um arquivo static.css.

1. Copiar o conteúdo para o arquivo `static.css`:

   ```shell
       /*my-custom-layout styles*/
      .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-left {
       width:20%;
       height: 36%;
      float: left !important;
      }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--top-right {
      width:80%;
      height: 36%;
     float: left !important;
     }
     .cq-Screens-channel--multizone.my-custom-layout .my-custom-layout--bottom {
     width:100%;
     height: 64%;
     }
   ```

   >[!NOTE]
   >É possível atualizar as porcentagens para corresponder aos requisitos do modelo personalizado.

1. Navegue até `/apps/<project>/templates/my-custom-layout/jcr:content` e atualize a propriedade *`cq:designPath`* para `/apps/settings/wcm/designs/customtemplate-designs` para carregar os estilos configurados em static.css.

   >[!NOTE]
   >Digite todos os estilos em vez de copiar ou colar, o que pode causar espaços em branco que resultam em problemas de estilo css.

## Exibir o resultado {#viewing-result}

Siga as etapas abaixo para usar o modelo personalizado acima em seu projeto do AEM Screens:

1. Navegue até o projeto do Screens criado na etapa (1) e clique na pasta **Canais**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Clique em **Criar** na barra de ações e clique no modelo **`Left20-LandscapeHD3Zone`** no assistente **Criar**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Depois de criar um canal com o modelo personalizado, é possível adicionar ativos ao canal por meio do editor. A visualização a seguir mostra as imagens em um modelo personalizado.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserir uma imagem como a Camada de Plano de Fundo {#inserting-image}

É possível inserir uma imagem como camada de plano de fundo no layout:

Você pode ajustar a regra CSS para usar &quot;data-uri&quot; e embutir diretamente a imagem (`Base64` codificada) no arquivo CSS que você criou em (etapa 13), *static.css*.

Essa organização é feita da seguinte maneira:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Ou você pode seguir as etapas abaixo:

1. Certifique-se de que a imagem esteja de alguma forma incluída na configuração offline do canal.
1. Use um link direto para a imagem no CSS acima, em vez da variante &quot;data-uri&quot;.


## Atualizando cor de fundo {#updating-color}

Para alterar a cor do plano de fundo, adicione o seguinte código ao arquivo xml (etapa 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`
