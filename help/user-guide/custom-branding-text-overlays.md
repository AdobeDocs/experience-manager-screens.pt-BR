---
title: Aplicação de marca personalizada e estilo para sobreposições de texto
seo-title: Aplicação de marca personalizada e estilo para sobreposições de texto
description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
seo-description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 04639198c5220e01af5945b8032c5fd86dc27499
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 1%

---


# Marca personalizada e estilo para sobreposições de texto {#creating-custom-branding-styling}

Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto aplicadas aos seus ativos em um canal do Screens.

## Criação de marcas personalizadas e de estilos para sobreposições de texto {#steps-custom-branding}

Siga as etapas abaixo para criar marcas e estilos personalizados para sobreposições de texto:

1. Crie um projeto do AEM Screens. Este exemplo mostra a funcionalidade ao criar um projeto chamado **customstyle** e um canal chamado **DemoBrand** , como mostrado na figura abaixo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. No editor, arraste e solte uma imagem e adicione uma sobreposição de texto ao ativo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para saber como adicionar uma sobreposição de texto ao ativo em um editor de canais, consulte Sobreposição de [texto](/help/user-guide/text-overlay.md).

1. Navegue até CRXDE Lite da sua instância do AEM —> Ferramentas —> **CRXDE Lite**.

1. É necessário criar um design personalizado em `/apps/settings/wcm/designs/<your-project>/`, por exemplo, neste caso, navegar até `/apps/settings/wcm/designs/customstyle/`

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crie o arquivo *static.css* e defina as seguintes regras css. Também é mostrado como um exemplo na figura abaixo das regras css.

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

   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie o caminho para o seu projeto, nesse caso, o caminho será `/apps/settings/wcm/designs/customstyle`.

1. Navegue até o canal chamado **DemoBrand** (criado na etapa 1) e clique em **Propriedades** na barra de ações depois de selecionar o canal.

1. Navegue até a guia **Avançado** e verifique o campo **Design** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Seja padrão, o campo **Design** mostra o caminho que aponta para designs na pasta libs.

1. Atualize o campo **Design** com o caminho para a pasta do projeto. Neste caso, será, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clique em **Salvar e fechar** para atualizar o caminho do design.

>[!IMPORTANT]
> Você tem a opção de sobrepor os modelos existentes do Screens para injetar seus próprios designs por padrão ou criar seu próprio modelo completamente. Consulte as etapas abaixo para obter mais detalhes.

1. Para sobrepor os modelos existentes do Screens para injetar seus próprios designs por padrão:

   1. Sobreposição `/libs/screens/core/templates/sequencechannel` em `/apps/screens/core/templates/sequencechannel`.
   1. Modifique a propriedade *cq:designPath* para apontar `/apps/screens/core/templates/sequencechannel/jcr:content` para o novo design.

1. Para criar seu próprio modelo completamente:
   1. Copie `/libs/screens/core/templates/sequencechannel` para `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique a propriedade *cq:designPath* para apontar `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para o novo design.


### Atualizando ACLs {#updating-acls}

Você deve atualizar as ACLs para esses designs para que possam ser baixados pelo player.

1. Navegue até useradmin e escolha o `screens-<project>-devices group` e conceda permissão de leitura ao caminho de design personalizado.

1. Forneça ao `screens-<project>-administrators` grupo permissões de leitura e modificação para este caminho.

## Como visualizar o resultado {#viewing-the-result}

Depois de concluir as etapas anteriores, você pode atualizar seu arquivo *statatis.css* do **CRXDE Lite** e, consequentemente, visualização a atualização para a sobreposição de texto que já foi adicionada ao ativo.

Siga as etapas abaixo para visualização do design atualizado à sobreposição de texto:

1. Navegue até o projeto do AEM Screens intitulado como **customstyle** —> **Canais** —> **DemoBrand**. Select the channel and click **Edit** from the action bar to open the editor.

1. Como você adicionou o design ao campo **Designs** , como mencionado acima, clique em **Pré-visualização** para visualização do estilo atual na imagem com a sobreposição de texto.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue até o arquivo *static.css* no CRXDE Lite e adicione a fonte como, por exemplo, `font-family: "Lucida Console", Courier, monospace;` a este arquivo, como mostrado abaixo.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Depois de salvar as alterações e recarregar a pré-visualização, você verá uma atualização na fonte da sobreposição de texto, como mostrado na figura abaixo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Além disso, você pode remover os dois últimos blocos de código do arquivo *static.css* para remover o estilo in a box em torno da sobreposição de texto.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. A alteração atualizada será visualização na sua pré-visualização, onde a sobreposição de texto será adicionada à imagem.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Como referência ao tutorial, agora você pode atualizar sua marca e estilo personalizado para sobreposições de texto adicionadas aos seus ativos.









