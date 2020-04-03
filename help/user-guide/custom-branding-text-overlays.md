---
title: Aplicação de marca personalizada e estilo para sobreposições de texto
seo-title: Aplicação de marca personalizada e estilo para sobreposições de texto
description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
seo-description: Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: f91faa23c7c5c4f0f705c77251554b64efaf2611

---


# Marca personalizada e estilo para sobreposições de texto {#creating-custom-branding-styling}

Siga esta página para saber como aplicar marcas e estilos personalizados a sobreposições de texto.

## Criação de marcas personalizadas e de estilos para sobreposições de texto {#steps-custom-branding}

Siga as etapas abaixo para criar marcas e estilos personalizados para sobreposições de texto:

1. Crie um projeto do AEM Screens intitulado como estilo **** personalizado e um canal chamado **DemoBrand**, como mostrado na figura abaixo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. No editor, arraste e solte uma imagem e adicione uma sobreposição de texto ao ativo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para saber como adicionar uma sobreposição de texto ao ativo em um editor de canais, consulte Sobreposição de [texto](/help/user-guide/text-overlay.md).

1. Navegue até CRXDE Lite da sua instância do AEM —> Ferramentas —> **CRXDE Lite**.

1. É necessário criar um design personalizado em, por exemplo, `/apps/settings/wcm/designs/<your-project>/`neste caso

   ![image](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Navegue até o arquivo static.css e defina as seguintes regras css. Também é mostrado na figura abaixo.

   ```shell
    //global styles
    .cq-Screens-textOverlay
    { … }
    //authoring overrides
    .aem-AuthorLayer-Edit .cq-Screens-textOverlay { … }
    // light text variant
    .cq-Screens-textOverlay-color--light
    { … }
     // dark text variant
    .cq-Screens-textOverlay-color--dark { … }
   ```
   ![image](/help/user-guide/assets/custom-brand/custom-brand4.png)

1. Copie o caminho para o seu projeto, nesse caso, o caminho será `/apps/settings/wcm/designs/customstyle`.

1. Navegue até o canal intitulado como **DemoBrand** (criado na etapa 1) e clique em **Propriedades** na barra de ações depois de selecionar o canal.

1. Navegue até a guia **Avançado** e verifique o campo **Design** .
   ![image](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Seja padrão, o campo **Design** mostra o caminho que aponta para designs na pasta libs.

1. Atualize o campo **Design** com o caminho para a pasta do projeto. Neste caso, será, `/apps/settings/wcm/designs/customstyle`.

   ![image](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clique em **Salvar e fechar** para atualizar o caminho do design.


## Como visualizar o resultado {#viewing-the-result}

Depois de concluir as etapas anteriores, você pode atualizar seu arquivo *statatis.css* do **CRXDE Lite** e, consequentemente, visualização a atualização para seu layout de texto adicionado ao ativo.

Siga as etapas abaixo para visualização do design atualizado ao layout do texto:

1. Navegue até o projeto do AEM Screens intitulado como estilo **** personalizado e um canal chamado **DemoBrand** e clique em **Editar** na barra de ações para abrir o editor.

1. Como você adicionou o design ao campo **Designs** , como mencionado acima, clique em **Pré-visualização** para visualização do estilo atual na imagem com a sobreposição de texto.

   ![image](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue até o arquivo static.css no CRXDE Lite, por exemplo, adicione a fonte.
   ![image](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Depois de salvar as alterações e recarregar a pré-visualização, você verá uma atualização da fonte de sobreposição de texto, como mostrado na figura abaixo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Além disso, você pode remover os dois últimos blocos de código do arquivo static.css para remover o estilo in a box em torno da sobreposição de texto.
   ![image](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. A alteração atualizada será visualização na sua pré-visualização, onde a sobreposição de texto será adicionada à imagem, como mostrado abaixo.

   ![image](/help/user-guide/assets/custom-brand/custom-brand11.png)

Assim, seguindo as etapas nas seções anteriores, você pode atualizar sua marca e o estilo personalizado para sobreposições de texto adicionadas aos seus ativos.









