---
title: Criação de modelos personalizados em layouts de várias zonas
seo-title: Criação de modelos personalizados em layouts de várias zonas
description: Siga esta página para saber mais sobre a criação de modelos personalizados em layouts MultiZone.
seo-description: Siga esta página para saber mais sobre a criação de modelos personalizados em layouts MultiZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 87a86d60de9ea09dae93d08a1e0b42271c39249f

---


# Criação de modelos personalizados em layouts de várias zonas {#creating-custom-templates-multizone}

Esta página mostra como você pode criar um modelo personalizado em um layout multizona.

## Convenção de nomenclatura {#name-terms}

Antes de entender como criar modelos personalizados de várias zonas para usar em um projeto do AEM Screens, é obrigatório entender a versão dos modelos que você deseja criar.

| **Nome do layout** | **Descrição** |
|---|---|
| Left20-LandscapeHD3Zone | Refere-se a um layout paisagem de 3 zonas que permite criar 3 zonas com zona 1 como 20% do ecrã horizontal e vertical a partir da esquerda, zona 2 como 80 % do ecrã horizontal e 20 % do ecrã vertical justificado à direita, zona 3 como 100 % da horizontal e 80 % do ecrã vertical com relação de aspecto de 16:9 |
| Upper20-PortraitHD2Zone | Refere-se a um modelo de retrato de 2 zonas que cobre 20% da tela do topo, com proporção de 16:9 |
| Right20-LandscapeSD3Zone | Refere-se a um modelo de 3 zonas que cobre 20% da tela da direita, com relação de aspecto de 4:3 |

##  Casos de uso de exemplo {#example-use-cases}

## Criação de um layout Left20-LandscapeHD3Zone {#landscape-layout-one}

Siga a seção abaixo demonstra como criar um modelo personalizado com a seguinte configuração:

* **Left20** refere-se à zona superior à esquerda, que cobre 20% do tamanho da tela horizontal e vertical.
* **Paisagem** refere-se à orientação do ecrã
* **HD** refere-se à proporção de 16:9
* **3A zona** se refere a três zonas do monitor

## Representação visual do layout de várias zonas {#multi-layout-visual-one}

O layout Left20-LandscapeHD3Zone permite criar o seguinte layout de várias zonas no seu projeto:

![image](/help/user-guide/assets/custom-multizone/custom-multizone1.png)






## Criação de um layout Upper20-PortraitHD2Zone {#landscape-layout-two}

Siga a seção abaixo demonstra como criar um modelo personalizado com a seguinte configuração:






![image](assets/custom-template1.png)


## Criando modelo personalizado com uma configuração específica {#basic-flow-setting}

Siga as etapas abaixo para criar um modelo personalizado.

1. Crie o modelo em `/apps/<project>/templates/my-custom-layout`

   ```shell
    <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
    jcr:description="My Custom 3-zones layout "
    jcr:primaryType="cq:Template"
    jcr:title="3-zones layout"
    allowedParents="[/libs/screens/core/templates/channelfolder]"
    allowedPaths="[/content/screens(/.*)?]"
    ranking="{Long}20000">
    <jcr:content
        cq:cssClass="aem-Layout aem-Layout--3x1 my-CustomLayout"
        cq:designPath="/apps/settings/wcm/designs/<project>"
        cq:deviceGroups="[mobile/groups/responsive]"
        jcr:primaryType="cq:PageContent"
        sling:resourceSuperType="screens/core/components/channel"
        sling:resourceType="screens/core/components/multiscreenchannel">
        <r1c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-top"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r2c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-middle"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <r3c1
            cq:cssClass="aem-LayoutCell--1-1 my-CustomLayout-bottom"
            jcr:primaryType="nt:unstructured"
            sling:resourceType="wcm/foundation/components/responsivegrid"/>
        <cq:responsive jcr:primaryType="nt:unstructured">
            <breakpoints jcr:primaryType="nt:unstructured"/>
        </cq:responsive>
        <offline-config/>
    </jcr:content>
   </jcr:root>
   ```

1. Criar um design de página no `/apps/settings/wcm/designs/<project>`.

   >[!NOTE]
   >
   >Certifique-se de que a imagem `cq:designPath` acima corresponde ao caminho.

1. Atualize o nó **offline-config** para que o design aponte também para o novo caminho

1. Adicione um arquivo **static.css** na `/apps/settings/wcm/designs/<project>` pasta e defina seu conteúdo como

   ```shell
   .cq-Screens-channel--multizone.my-CustomLayout {}
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-top { height: 150px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-middle { height: 1470px; }
   .cq-Screens-channel--multizone.my-CustomLayout .my-CustomLayout-bottom { height: 300px; }
   ```

## Inserir uma imagem como a camada de plano de fundo {#inserting-image}

É possível inserir uma imagem como uma camada de plano de fundo no layout:

Você pode ajustar a regra CSS para usar o que é chamado de &quot;data-uri&quot; e inserir diretamente a imagem (codificada em Base64) no arquivo CSS.

Isso é feito da seguinte forma:
`.cq-Screens-channel--multizone.my-CustomLayout { background: url('data:image/…;base64,…') no-repeat center center; }`

Ou você pode seguir as etapas abaixo:

1. Verifique se a imagem está incluída na configuração offline do canal
1. Use um link direto para a imagem no CSS acima, em vez da variante &quot;data-uri&quot;


## Atualização da cor de fundo {#updating-color}

Para alterar a cor do plano de fundo, adicione o seguinte código ao arquivo xml:

`.cq-Screens-channel--multizone.my-CustomLayout { background-color: …; }`



