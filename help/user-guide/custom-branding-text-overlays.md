---
title: Aplicação de marca personalizada e estilo para sobreposições de texto
seo-title: Aplicação de marca personalizada e estilo para sobreposições de texto
description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
seo-description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
contentOwner: Jyotika Syal
feature: Desenvolvendo telas
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---


# Marca personalizada e estilo para sobreposições de texto {#creating-custom-branding-styling}

Siga esta página para saber como aplicar marcas e estilos personalizados a Sobreposições de texto aplicadas a seus ativos em um canal do AEM Screens.

## Criação de marca personalizada e estilo para sobreposições de texto {#steps-custom-branding}

Siga as etapas abaixo para criar marcas e estilos personalizados para sobreposições de texto:

1. Crie um projeto do AEM Screens. Este exemplo mostra a funcionalidade ao criar um projeto chamado **customstyle** e um canal chamado **DemoBrand** , conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. No editor, arraste e solte uma imagem e adicione uma sobreposição de texto ao ativo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para saber como adicionar uma sobreposição de texto ao seu ativo em um editor de canal, consulte [Sobreposição de texto](/help/user-guide/text-overlay.md).

1. Navegue até CRXDE Lite da sua instância de AEM —> ferramentas —> **CRXDE Lite**.

1. Você precisa criar um design personalizado em `/apps/settings/wcm/designs/<your-project>/`, por exemplo, neste caso, navegue até `/apps/settings/wcm/designs/customstyle/`

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crie o arquivo *static.css* e defina as seguintes regras de css. Também mostrado como um exemplo na figura abaixo das regras de css.

   ```shell
    //global styles
    cq-Screens-textOverlay {
    padding: 1em;
    font-size: 3rem;
    line-height: 1em;
     }
    //authoring overrides
   .aem-AuthorLayer-Edit .cq-Screens-textOverlay {
    display: none;
    padding: 0;
    font-size: 1rem;
    }
     // light text variant
    .cq-Screens-textOverlay-color--light {
     background-color: rgba(0, 0, 0, .6);
     }
     // dark text variant
     .cq-Screens-textOverlay-color--dark {
      background-color: rgba(255, 255, 255, .6);
    }
   ```

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie o caminho para seu projeto. Nesse caso, o caminho será `/apps/settings/wcm/designs/customstyle`.

1. Navegue até o canal chamado **DemoBrand** (criado na etapa 1) e clique em **Properties** na barra de ações depois de selecionar o canal.

1. Navegue até a guia **Advanced** e marque o campo **Design**.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Seja padrão, o campo **Design** mostra o caminho apontando para designs na pasta libs.

1. Atualize o campo **Design** com o caminho para a pasta do projeto. Nesse caso, será `/apps/settings/wcm/designs/customstyle`.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clique em **Salvar e fechar** para atualizar o caminho do design.

   >[!IMPORTANT]
   >Você tem a opção de sobrepor os modelos existentes do Screens para injetar seus próprios designs por padrão ou criar seu próprio modelo completamente. Consulte as etapas abaixo para obter mais detalhes.

1. Para sobrepor os modelos existentes do Screens para injetar seus próprios designs por padrão:

   1. Sobreponha `/libs/screens/core/templates/sequencechannel` em `/apps/screens/core/templates/sequencechannel`.
   1. Modifique a propriedade *cq:designPath* em `/apps/screens/core/templates/sequencechannel/jcr:content` para apontar para o novo design.

1. Para criar seu próprio template completamente:
   1. Copie `/libs/screens/core/templates/sequencechannel` para `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique a propriedade *cq:designPath* em `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para apontar para o novo design.


### Atualizando ACLs {#updating-acls}

Você deve atualizar as ACLs desses designs para que elas possam ser baixadas pelo reprodutor.

1. Navegue até user admin e escolha o `screens-<project>-devices group` e conceda a ele permissão de leitura para o caminho de design personalizado.

1. Forneça ao grupo `screens-<project>-administrators` permissões de leitura e modificação para este caminho.

## Visualização do resultado {#viewing-the-result}

Depois de concluir as etapas anteriores, você pode atualizar seu arquivo *statis.css* de **CRXDE Lite** e, consequentemente, exibir a atualização para sua sobreposição de texto que já está adicionada ao ativo.

Siga as etapas abaixo para exibir o design atualizado para a sobreposição de texto:

1. Navegue até o projeto do AEM Screens chamado **customstyle** —> **Channels** —> **DemoBrand**. Selecione o canal e clique em **Edit** na barra de ações para abrir o editor.

1. Como você adicionou o design ao seu campo **Designs**, conforme mencionado acima, clique em **Preview** para exibir o estilo atual na imagem com sobreposição de texto.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue até o arquivo *static.css* no CRXDE Lite e adicione a fonte, como `font-family: "Lucida Console", Courier, monospace;`, a esse arquivo, conforme mostrado abaixo.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Depois de salvar as alterações e recarregar a visualização, você verá uma atualização na fonte da sobreposição de texto, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Além disso, você pode remover os dois últimos blocos de código do arquivo *static.css* para remover o estilo in a box em torno da sobreposição de texto.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Você visualizará a alteração atualizada na sua visualização, onde a sobreposição de texto é adicionada à imagem.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Agora, você está pronto para atualizar a marca e o estilo personalizado para as sobreposições de texto adicionadas aos ativos.









