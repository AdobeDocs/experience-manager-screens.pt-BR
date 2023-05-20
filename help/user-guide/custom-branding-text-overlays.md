---
title: Aplicação de marca e estilo personalizados a sobreposições de texto
seo-title: Applying Custom Branding and Styling for Text Overlays
description: Siga esta página para saber como aplicar a identidade visual e o estilo personalizados às Sobreposições de Texto.
seo-description: Follow this page to learn how to apply custom branding and styling for Text Overlays.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 1%

---

# Marca e estilo personalizados para sobreposições de texto {#creating-custom-branding-styling}

Siga esta página para saber como aplicar a marca e o estilo personalizados para Sobreposições de texto aplicadas aos seus ativos em um canal do AEM Screens.

## Criação de marca e estilo personalizados para sobreposições de texto {#steps-custom-branding}

Siga as etapas abaixo para criar marca e estilo personalizados para sobreposições de texto:

1. Crie um projeto do AEM Screens. Este exemplo mostra a funcionalidade criando um projeto chamado **customstyle** e um canal intitulado **DemoBrand** , conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. No editor, arraste e solte uma imagem e adicione sobreposição de texto ao ativo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para saber como adicionar uma sobreposição de texto ao seu ativo em um editor de canal, consulte [Sobreposição de texto](/help/user-guide/text-overlay.md).

1. Navegue até o CRXDE Lite a partir da instância do AEM —> ferramentas —> **CRXDE Lite**.

1. Você precisa criar um design personalizado no `/apps/settings/wcm/designs/<your-project>/`, por exemplo, nesse caso, navegue até `/apps/settings/wcm/designs/customstyle/`

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Criar *static.css* e defina as seguintes regras de css. Também é mostrado como exemplo na figura abaixo das regras de css.

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

1. Copie o caminho para o projeto. Nesse caso, o caminho será `/apps/settings/wcm/designs/customstyle`.

1. Navegue até o canal intitulado como **DemoBrand** (criado na etapa(1)) e clique em **Propriedades** na barra de ações depois de selecionar o canal.

1. Navegue até a **Avançado** e verifique a **Design** campo.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Por padrão, a variável **Design** mostra o caminho que aponta para designs na pasta libs.

1. Atualize o **Design** com o caminho para a pasta do projeto. Neste caso, será, `/apps/settings/wcm/designs/customstyle`.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clique em **Salvar e fechar** para atualizar o caminho de design.

   >[!IMPORTANT]
   >Você tem a opção de sobrepor os modelos do Screens existentes para inserir seus próprios designs por padrão ou criar seu próprio modelo completamente. Consulte as etapas abaixo para obter mais detalhes.

1. Para sobrepor os modelos do Screens existentes para inserir seus próprios designs por padrão:

   1. Sobreposição `/libs/screens/core/templates/sequencechannel` in `/apps/screens/core/templates/sequencechannel`.
   1. Modifique o *cq:designPath* propriedade no `/apps/screens/core/templates/sequencechannel/jcr:content` para apontar para o novo design.

1. Para criar seu próprio template completamente:
   1. Copiar `/libs/screens/core/templates/sequencechannel` para `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique o *cq:designPath* propriedade no `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para apontar para o novo design.


### Atualizando ACLs {#updating-acls}

Você deve atualizar as ACLs desses designs para que elas possam ser baixadas pelo reprodutor.

1. Navegue até administrador de usuários e escolha a `screens-<project>-devices group` e conceda permissão de leitura ao caminho de design personalizado.

1. Fornecer `screens-<project>-administrators` permissões de leitura e modificação de grupo para este caminho.

## Exibir o resultado {#viewing-the-result}

Depois de concluir as etapas anteriores, você poderá atualizar *stat.css* arquivo de **CRXDE Lite** e, consequentemente, visualize a atualização da sobreposição de texto que já foi adicionada ao ativo.

Siga as etapas abaixo para exibir o design atualizado para a sobreposição de texto:

1. Navegue até o projeto do AEM Screens intitulado como **customstyle** —> **Canais** —> **DemoBrand**. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor.

1. Como você adicionou o design ao seu **Designs** como mencionado acima, clique em **Visualizar** para exibir o estilo atual na imagem com sobreposição de texto.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue até o *static.css* arquivo no CRXDE Lite e adicione a fonte como, `font-family: "Lucida Console", Courier, monospace;` nesse arquivo, conforme mostrado abaixo.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Depois de salvar as alterações e recarregar a visualização, você verá uma atualização para a fonte de sobreposição de texto, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Além disso, você pode remover os dois últimos blocos de código do *static.css* arquivo para remover o estilo em caixa ao redor da sobreposição de texto.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Você visualizará a alteração atualizada em sua visualização, na qual a sobreposição de texto é adicionada à imagem.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Agora você está pronto para atualizar sua marca e estilo personalizado para sobreposições de texto adicionadas aos seus ativos.
