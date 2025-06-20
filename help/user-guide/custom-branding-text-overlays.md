---
title: Aplicação de marca e estilo personalizados a sobreposições de texto
description: Saiba como aplicar marca e estilo personalizados a sobreposições de texto aplicadas a ativos em um canal do AEM Screens.
contentOwner: Jyotika Syal
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 059e1b19-e9b5-48f0-8f2f-141f0c2f7842
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---

# Marca e estilo personalizados para sobreposições de texto {#creating-custom-branding-styling}

Saiba como aplicar marca e estilo personalizados a sobreposições de texto aplicadas aos seus ativos em um canal do AEM Screens.

## Criação de marca e estilo personalizados para sobreposições de texto {#steps-custom-branding}

Siga as etapas abaixo para criar marca e estilo personalizados para sobreposições de texto:

1. Crie um projeto do AEM Screens. Este exemplo mostra a funcionalidade criando um projeto chamado **`customstyle`** e um canal chamado **DemoBrand**, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand1.png)

1. No editor, arraste e solte uma imagem e adicione uma sobreposição de texto ao ativo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand2.png)

   >[!NOTE]
   >Para saber como adicionar uma sobreposição de texto ao seu ativo em um editor de canal, consulte [Sobreposição de texto](/help/user-guide/text-overlay.md).

1. Navegue até o CRXDE Lite na instância do AEM > ferramentas > **CRXDE Lite**.

1. Crie um design personalizado em `/apps/settings/wcm/designs/<your-project>/`. Por exemplo, neste caso, navegue até `/apps/settings/wcm/designs/customstyle/`

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand3.png)

1. Crie um arquivo *static.css* e defina as seguintes regras de css. Também é mostrado como exemplo na figura abaixo das regras de css.

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

1. Copie o caminho para o seu projeto, neste caso, o caminho é `/apps/settings/wcm/designs/customstyle`.

1. Navegue até o canal intitulado como **DemoBrand** (criado na etapa(1)) e clique em **Propriedades** na barra de ações depois de selecionar o canal.

1. Navegue até a guia **Avançado** e verifique o campo **Design**.
   ![imagem](/help/user-guide/assets/custom-brand/custom-brand5.png)

   >[!NOTE]
   >Por padrão, o campo **Design** mostra o caminho que aponta para designs na pasta libs.

1. Atualize o campo **Design** com o caminho para a pasta do projeto. Nesse caso, é `/apps/settings/wcm/designs/customstyle`.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand6.png)

1. Clique em **Salvar e fechar** para atualizar o caminho de design.

   >[!IMPORTANT]
   >Opcionalmente, é possível sobrepor os modelos existentes do Screens para inserir seus próprios designs por padrão ou criar seu próprio modelo completamente. Consulte as etapas abaixo para obter mais detalhes.

1. Para sobrepor os modelos existentes do Screens para inserir seus próprios designs por padrão:

   1. Sobreposição `/libs/screens/core/templates/sequencechannel` em `/apps/screens/core/templates/sequencechannel`.
   1. Modifique a propriedade *`cq:designPath`* em `/apps/screens/core/templates/sequencechannel/jcr:content` para que ela aponte para o novo design.

1. Para criar seu próprio template completamente:
   1. Copiar `/libs/screens/core/templates/sequencechannel` para `/apps/customstyle/templates/styled-sequencechannel`.
   1. Modifique a propriedade *`cq:designPath`* em `/apps/customstyle/templates/styled-sequencechannel/jcr:content` para que ela aponte para o novo design.


### Atualizando ACLs {#updating-acls}

Atualize as ACLs desses designs para que o reprodutor possa baixá-los.

1. Navegue até o administrador de usuários e escolha o `screens-<project>-devices group` e dê a ele permissão de leitura para o caminho de design personalizado.

1. Forneça permissões de leitura e modificação de grupo `screens-<project>-administrators` para este caminho.

## Exibir o resultado {#viewing-the-result}

Quando você tiver concluído as etapas anteriores, poderá atualizar seu arquivo *statatis.css* do **CRXDE Lite** e, portanto, exibir a atualização para sua sobreposição de texto que já foi adicionada ao ativo.

Siga as etapas abaixo para exibir o design atualizado para a sobreposição de texto:

1. Navegue até o projeto do AEM Screens intitulado como **`customstyle`** > **Canais** > **DemoBrand**. Clique no canal e em **Editar** na barra de ações.

1. Como você adicionou o design ao campo **Designs**, como mencionado acima, clique em **Visualizar** para exibir o estilo atual na imagem com sobreposição de texto.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand7.png)

1. Navegue até o arquivo *static.css* no CRXDE Lite e adicione a fonte, como `font-family: "Lucida Console", Courier, monospace;`, a esse arquivo, conforme mostrado abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand8.png)

1. Ao salvar as alterações e recarregar a visualização, você verá uma atualização da fonte de sobreposição de texto, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand9.png)

1. Além disso, você pode remover os dois últimos blocos de código do arquivo *static.css* para remover o estilo em caixa ao redor da sobreposição de texto.

![imagem](/help/user-guide/assets/custom-brand/custom-brand10.png)

1. Visualize a alteração atualizada em sua visualização, onde a sobreposição de texto é adicionada à imagem.

   ![imagem](/help/user-guide/assets/custom-brand/custom-brand11.png)

   Agora você está pronto para atualizar sua marca e estilo personalizado para sobreposições de texto adicionadas aos seus ativos.
