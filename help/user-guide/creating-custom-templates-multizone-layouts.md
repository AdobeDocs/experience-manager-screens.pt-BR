---
title: Criação de modelos personalizados em layouts de várias zonas
seo-title: Criação de modelos personalizados em layouts de várias zonas
description: Siga esta página para saber mais sobre como criar modelos personalizados em layouts de várias zonas.
seo-description: Siga esta página para saber mais sobre como criar modelos personalizados em layouts de várias zonas.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# Criação de modelos personalizados para layouts de várias zonas {#creating-custom-templates-multizone}

Esta página mostra como criar um modelo personalizado para um layout de várias zonas.

## Considerações importantes {#considerations}

Há duas considerações importantes que você deve estar ciente antes de criar um modelo personalizado no layout de várias zonas:

1. **Tamanho ou porcentagens** de pixels fixos:

   Você deve decidir se deseja usar o tamanho fixo de pixel para diferentes zonas para o layout personalizado ou criar um layout personalizado usando porcentagens.

   >[!NOTE]
   >A vantagem de usar a porcentagem para definir zonas para o seu layout personalizado permite reutilizar o modelo em uma variedade de tamanhos de tela.

1. **Convenção** de nomenclatura:

   Antes de entender como criar modelos de várias zonas personalizados para usar em um projeto do AEM Screens, é recomendável entender a versão dos modelos que deseja criar.

   | **Nome do layout** | **Descrição** |
   |---|---|
   | Left20-LandscapeHD3Zone | Refere-se a um layout de paisagem de 3 zonas que permite criar 3 zonas com zona 1 como 20% do ecrã horizontal e vertical à esquerda, zona 2 como 80 % do ecrã horizontal e 20 % do ecrã vertical justificado à direita, zona 3 como 100 % do ecrã horizontal e 80 % do ecrã vertical com relação de aspecto de 16:9 |
   | Upper20-PortraitHD2Zone | Refere-se a um modelo de retrato de duas zonas que cobre 20% da tela de cima, com proporção de aspecto de 16:9 |
   | Right20-LandscapeSD3Zone | Refere-se a um modelo de 3 zonas que cobre 20% da tela da direita, com proporção de aspecto de 4:3 |

   >[!IMPORTANT]
   >As zonas definidas no layout personalizado podem não corresponder à taxa de proporção geral do layout inteiro. A convenção de nomenclatura seguida neste documento especifica a proporção do layout personalizado como um todo.

## Exemplo de uso Caso esquerdo20-PaisagemHD3Layout de zona {#custom-template-one}

Siga a seção abaixo para criar um modelo personalizado *Left20-LandscapeHD3Zone* com a seguinte configuração:

* **Left20** refere-se à zona superior à esquerda, que cobre 20% do tamanho horizontal e vertical da tela.
* **** Paisagens se referem à orientação da tela
* **** HDrefere-se à proporção de aspecto como 16:9
* **3** Zonerefere para três zonas do monitor

## Representação visual do layout de várias zonas {#multi-layout-visual-one}

O layout Left20-LandscapeHD3Zone permite criar o seguinte layout de várias zonas no seu projeto:

![imagem](/help/user-guide/assets/custom-multizone/landscape-3-zone-new.png)

## Criação de um layout de zona HD3Zone Left20-Landscape {#landscape-layout-one}

Siga as etapas abaixo para criar um Layout de Zona HD3PaisagemEsquerda20 para um projeto AEM Screens:

1. Crie um projeto do AEM Screens chamado **customtemplate**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template2.png)

1. Navegue até **CRXDE Lite** da sua instância de AEM —> Ferramentas —> **CRXDE Lite**.

1. Crie uma pasta em **apps** com o título **customtemplate**. Da mesma forma, crie outra pasta denominada **template** em **customtemplate**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template1.png)

   >[!NOTE]
   >É recomendável clicar em **Salvar tudo** na barra de ações no CRXDE Lite sempre que criar, editar ou copiar conteúdo para qualquer um dos nós, caso contrário não será possível confirmar as atualizações.

1. Copie o modelo da barra esquerda de `/libs/screens/core/templates/splitscreenchannel/lbar-left` para `/apps/customtemplate/template`.

1. Renomeie o **barra esquerda** (`/apps/customtemplate/template`) copiado para **my-custom-layout**.
   ![imagem](/help/user-guide/assets/custom-multizone/custom-template3.png)

1. Navegue até `/apps/customtemplate/template/my-custom-layout` e atualize as propriedades **jcr:description** para *Modelo para Left20-LandscapeHD3Zone* e **jcr:title** para *Left20-LandscapeHD3Zone*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template4.png)

1. Navegue até o nó **offline-config** de `/apps/customtemplate/template/my-custom-layout/jcr:content/offline-config` e atualize o **jcr:title** para *Left20-LandscapeHD3Zone*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template5.png)

1. Navegue até a propriedade *jcr:content* de **my-custom-template** de `/apps/customtemplate/template/my-custom-layout/jcr:content` e atualize a propriedade **cq:cssClass** para **aem-Layout my-custom-layout**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template6.png)

1. Referindo-se à etapa (4), na qual, você copiou o modelo da barra esquerda, visualizará 3 grades responsivas em `my-custom-layout/jcr:content`. Adicione a classe css personalizada a cada grade responsiva na propriedade *cq:cssClass*, por exemplo, *my-custom-layout—top-left* para o nó *r1c1*.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template7.png)

   Da mesma forma, adicione *my-custom-layout—top-right* para *r1c2* e *my-custom-layout—bottom* para o nó *r2c1*.

   >[!NOTE]
   >Essas classes personalizadas serão usadas no css para definir a largura/altura para essas grades responsivas.

   >[!NOTE]
   >Você pode adicionar ou remover as grades responsivas com base no número total de grades que deseja. Neste exemplo, mostramos 2 grades na primeira linha e 1 grade na segunda linha, então há um total de 3 grades responsivas (r1c1, r1c2, r2c1).

1. Copie `/libs/settings/wcm/designs/screens` para `/apps/settings/wcm/designs/` e renomeie o design copiado como **custom-template-designs**.

1. Navegue até `/apps/settings/wcm/designs/custom-template-designs` e atualize a propriedade *jcr:title* de **custom-template-designs** para **customtemplate-design**.

1. Navegue até `/apps/settings/wcm/designs/custom-template-designs` e crie um arquivo static.css.

1. Copie o conteúdo para o arquivo `static.css`:

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

1. Navegue até `/apps/<project>/templates/my-custom-layout/jcr:content` e atualize a propriedade *cq:designPath* para `/apps/settings/wcm/designs/customtemplate-designs` para carregar os estilos configurados em static.css

   >[!NOTE]
   >É recomendável digitar todos os estilos em vez de copiar ou colar, o que pode causar espaços em branco, resultando em problemas de estilo css.

## Visualização do resultado {#viewing-result}

Siga as etapas abaixo para usar o modelo personalizado acima em seu projeto do AEM Screens:

1. Navegue até o projeto do Screens criado na etapa 1 e selecione a pasta **Channels**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template8.png)

1. Clique em **Create** na barra de ações e selecione o modelo **Left20-LandscapeHD3Zone** do assistente **Create**.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template9.png)

1. Depois de criar um canal com o modelo personalizado, você pode adicionar ativos ao seu canal a partir do editor. A visualização a seguir mostra as imagens em um modelo personalizado.

   ![imagem](/help/user-guide/assets/custom-multizone/custom-template10.png)

## Inserção de uma imagem como a camada de fundo {#inserting-image}

É possível inserir uma imagem como uma camada de plano de fundo no layout:

É possível ajustar a regra de CSS para usar o que é chamado de &quot;data-uri&quot; e diretamente embutir a imagem (Base64 codificada) no arquivo CSS, criado em (etapa 13), *static.css*.

Isso é feito da seguinte maneira:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Ou siga as etapas abaixo:

1. Certifique-se de que a imagem esteja incluída na configuração offline do canal
1. Use um link direto para a imagem no CSS acima, em vez da variante &quot;data-uri&quot;


## Atualizando Cor do Plano de Fundo {#updating-color}

Para alterar a cor de fundo, adicione o seguinte código ao arquivo xml (etapa 13), *static.css*.

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



