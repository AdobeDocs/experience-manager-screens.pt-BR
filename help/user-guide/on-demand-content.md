---
title: Atualização de conteúdo sob demanda
description: Saiba mais sobre a Atualização de conteúdo por demanda para gerenciar publicações.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 9ffdb1eb-a1ba-42ac-a30f-260004e5b165
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---

# Atualização de conteúdo sob demanda {#on-demand}

Esta seção descreve conteúdo sob demanda para gerenciar publicações.

## Gerenciar publicação: entregar atualizações de conteúdo de autor para publicação para dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Você pode publicar e desfazer a publicação de conteúdo do AEM Screens. O recurso Gerenciar publicação permite entregar atualizações de conteúdo do autor para a publicação no dispositivo. Você pode publicar/desfazer a publicação de conteúdo para todo o projeto do AEM Screens ou apenas para um de seus canais, locais, dispositivos, aplicativos ou um agendamento.

### Gerenciar publicação de um projeto do AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga as etapas abaixo para fornecer atualizações de conteúdo do autor para a publicação no dispositivo para um projeto do AEM Screens:

1. Navegue até o projeto do AEM Screens.
1. Selecionar **Gerenciar publicação** na barra de ações para que você possa publicar o projeto na sua instância de Publicação.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. A variável **Gerenciar publicação** é aberto. É possível selecionar a variável **Ação** e também agendar o horário de publicação para agora ou depois. Selecione **Próximo**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque a caixa para poder selecionar o projeto inteiro na caixa **`Manage Publication`** assistente.

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Selecionar **+ Incluir secundárias** na barra de ações e desmarque todas as opções para poder publicar todos os módulos no seu projeto e selecionar **Adicionar** para publicar.

   >[!NOTE]
   >
   >Por padrão, todas as caixas são marcadas e você precisa desmarcar manualmente as caixas para publicar todos os módulos no seu projeto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Entendendo a caixa de diálogo Incluir filhos**

   As etapas mencionadas acima mostram como você pode publicar todo o conteúdo. Caso deseje usar as outras três alternativas disponíveis, é necessário marcar essa opção específica.
Por exemplo, a imagem a seguir mostra como é possível gerenciar e atualizar somente as páginas modificadas no seu projeto:
   ![imagem](assets/author-publish-manage.png)

   Siga as explicações abaixo para entender as opções disponíveis:

   1. **Incluir somente secundárias imediatas**: essa opção permite gerenciar atualizações somente nos subnós na estrutura do projeto.
   1. **Incluir somente as páginas modificadas**: essa opção permite gerenciar atualizações somente nas páginas modificadas do projeto em que as alterações são encontradas na estrutura do projeto.
   1. **Incluir somente páginas já publicadas**: essa opção permite gerenciar atualizações somente nas páginas que foram publicadas antes.


1. No **`Manage Publication wizard`**, selecione **Publish**.

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Aguarde alguns segundos/minutos para que o conteúdo atinja a instância de publicação.
   >
   >
   >    1. O fluxo de trabalho não funciona se não houver alterações no projeto e nada para **Atualizar conteúdo offline**.
   >    1. O fluxo de trabalho não funcionará se o autor não concluir o processo de replicação (o conteúdo ainda está sendo carregado na instância de publicação) após clicar no link **Publish** no fluxo de trabalho de publicação de gerenciamento.

   >[!CAUTION]
   >Se, como autor ou criador de conteúdo, você quiser ver as alterações nos dispositivos anexados à instância do autor, clique em **Atualizar conteúdo offline** no painel do canal ou selecionando o projeto. Nesse caso, a atualização do conteúdo offline é executada somente na instância do autor.

1. Navegue até o projeto e clique em **Atualizar conteúdo offline** na barra de ações. Essa ação encaminha o mesmo comando para publicar a instância, para que os zips offline também sejam criados na instância de publicação.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)


   >[!NOTE]
   >
   >Depois de concluir o fluxo de trabalho de publicação de gerenciamento e se houver um player apontando para a instância do autor, acione a atualização do conteúdo offline no autor. Isso cria a atualização offline na instância do Autor.

   >[!CAUTION]
   >
   >Acione a atualização do conteúdo offline na instância do autor, se você tiver um reprodutor registrado no servidor do autor. A atualização do conteúdo offline não é necessária para o reprodutor registrado na instância de publicação.

### Gerenciamento da publicação de um canal {#managing-publication-for-a-channel}

Siga as etapas abaixo para fornecer atualizações de conteúdo de Autor > Publicar > dispositivo para um Canal em um projeto do AEM Screens:

>[!NOTE]
>
>Siga esta seção somente se houver alterações em um canal. Se um canal não tiver alterações após a atualização anterior do conteúdo offline, o fluxo de trabalho de publicação de gerenciamento para um canal individual não funcionará.

1. Navegue até o projeto do AEM Screens e selecione o canal.
1. Selecionar **Gerenciar publicação** na barra de ações para que você possa publicar o canal na sua instância de Publicação.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. A variável **Gerenciar publicação** é aberto. É possível selecionar a variável **Ação** e também agendar o horário de publicação para agora ou depois. Selecione **Próximo**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Selecionar **Publish** do **`Manage Publication`** assistente.

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Aguarde alguns segundos/minutos para que o conteúdo atinja a instância de publicação.

1. Acionamento **Atualizar conteúdo offline** no painel de canal, o envia somente o conteúdo offline para a instância de Autor, mas não para a instância de Publicação. As etapas 1 a 4 são para enviar conteúdo offline para a instância de publicação.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Publique primeiro e acione a atualização do conteúdo offline conforme resumido nas etapas anteriores.

### Reatribuição de canal e dispositivo: {#channel-and-device-re-assignment}

Se tiver reatribuído um dispositivo, você deverá publicar a exibição inicial e a nova exibição, uma vez que o dispositivo tenha sido reatribuído à nova exibição.

Da mesma forma, se um canal tiver sido reatribuído, você deverá publicar a exibição inicial e a nova exibição, uma vez que o canal tenha sido reatribuído à nova exibição.
