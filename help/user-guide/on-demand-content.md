---
title: Atualização de conteúdo sob demanda
seo-title: Atualização de conteúdo sob demanda
description: 'Siga esta página para saber mais sobre a Atualização de conteúdo sob demanda.  '
seo-description: 'Siga esta página para saber mais sobre a Atualização de conteúdo sob demanda.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 221243c537e708aac44145c8d5d5a181ea80a293

---


# Atualização de conteúdo sob demanda {#on-demand}

Esta seção descreve o conteúdo sob demanda para o gerenciamento de publicações.

## Gerenciando a publicação: Fornecer atualizações de conteúdo do autor para o dispositivo {#managing-publication-delivering-content-updates-from-author-to-publish-to-device}

Você pode publicar e cancelar a publicação de conteúdo do AEM Screens. O recurso Gerenciar publicação permite fornecer atualizações de conteúdo do autor para o dispositivo. Você pode publicar/cancelar a publicação de conteúdo para todo o projeto do AEM Screens ou somente para um de seus canais, locais, dispositivos, aplicativos ou agendamentos.

### Gerenciar publicação para um projeto do AEM Screens {#managing-publication-for-an-aem-screens-project}

Siga as etapas abaixo para fornecer atualizações de conteúdo do autor para publicar em um dispositivo para um projeto do AEM Screens:

1. Navegue até o projeto do AEM Screens.
1. Clique em **Gerenciar publicação** na barra de ações para publicar a instância do projeto.

   ![screen_shot_2019-02-25at21420pm](assets/screen_shot_2019-02-25at21420pm.png)

1. The **Manage Publication** wizard opens. Você pode selecionar a **Ação** e também agendar o tempo de publicação para agora ou para depois. Clique em **Avançar**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Marque a caixa para selecionar o projeto inteiro no assistente **Gerenciar publicação** .

   ![screen_shot_2019-02-25at22712pm](assets/screen_shot_2019-02-25at22712pm.png)

1. Clique em **+ Incluir filhos** na barra de ações e desmarque todas as opções para publicar todos os módulos no seu projeto e clique em **Adicionar** para publicar.

   >[!NOTE]
   >
   >Por padrão, todas as caixas serão marcadas e você terá que desmarcar manualmente as caixas para publicar todos os módulos em seu projeto.

   ![screen_shot_2019-02-25at23116pm](assets/screen_shot_2019-02-25at23116pm.png)

   **Noções Gerais da caixa de diálogo Incluir filhos**

   A etapa mencionada acima mostra como você pode publicar o conteúdo inteiro. Caso deseje usar as outras três alternativas disponíveis, será necessário verificar essa opção específica.
Por exemplo, a imagem a seguir permite que você gerencie e atualize somente as páginas modificadas no seu projeto:
   ![image](assets/author-publish-manage.png)

   Siga as explicações abaixo para entender as opções disponíveis:

   1. **Incluir apenas filhos**imediatos:
Essa opção permite gerenciar atualizações somente nos subnós da estrutura do projeto.
   1. **Incluir somente páginas**modificadas:
Essa opção permite gerenciar atualizações somente nas páginas modificadas do projeto em que as alterações são encontradas na estrutura do projeto.
   1. **Incluir somente páginas**já publicadas:
Essa opção permite gerenciar atualizações somente para as páginas que foram publicadas antes.


1. Clique em **Publicar** no assistente **Gerenciar publicação.**

   ![screen_shot_2019-02-25at23341pm](assets/screen_shot_2019-02-25at23341pm.png)

   >[!NOTE]
   >
   >Aguarde alguns segundos/minutos para que o conteúdo chegue à instância de publicação.
   >
   >
   >O processo **Gerenciar publicação** com atualizar o conteúdo offline é de duas etapas e as etapas devem estar na ordem correta.
   >
   >
   >
   >    1. O fluxo de trabalho não funcionará se **Atualizar conteúdo** offline for acionado antes de publicar usando **Gerenciar publicação**.
      >
      >    
   1. O fluxo de trabalho não funcionará se não houver alterações no projeto e nada para **Atualizar conteúdo** offline.
   >    1. O fluxo de trabalho não funcionará se o autor não concluir o processo de replicação (o conteúdo ainda está sendo carregado para a instância de publicação) depois de clicar no botão **Publicar** no fluxo de trabalho de gerenciamento da publicação.


1. Após concluir o fluxo de trabalho de gerenciamento da publicação, você deve acionar a atualização do conteúdo offline no autor, que criará a atualização offline na instância do autor.

   Navegue até o projeto e clique em **Atualizar conteúdo** offline na barra de ações. Essa ação encaminha o mesmo comando para publicar a instância, de modo que os zips offline também sejam criados na instância de publicação.

   ![screen_shot_2019-02-25at23451pm](assets/screen_shot_2019-02-25at23451pm.png)

   >[!CAUTION]
   >
   >Primeiro, você deve publicar e depois acionar a atualização do conteúdo offline, como resumido nas etapas anteriores.

### Gerenciando a publicação de um canal {#managing-publication-for-a-channel}

Siga as etapas abaixo para fornecer atualizações de conteúdo do autor para publicar em um dispositivo para um canal em um projeto do AEM Screens:

>[!NOTE]
>
>Siga esta seção somente se houver alterações em um canal. Se um canal não tiver alterações após a atualização anterior do conteúdo offline, o fluxo de trabalho de gerenciamento de publicação de um canal individual não funcionará.

1. Navegue até o projeto do Screens e selecione o canal.
1. Clique em **Gerenciar publicação** na barra de ações para publicar o canal para a instância de publicação.

   ![screen_shot_2019-02-07at115800am](assets/screen_shot_2019-02-07at115800am.png)

1. The **Manage Publication** wizard opens. Você pode selecionar a **Ação** e também agendar o tempo de publicação para agora ou para depois. Clique em **Avançar**.

   ![screen_shot_2019-02-07at120304pm](assets/screen_shot_2019-02-07at120304pm.png)

1. Clique em **Publicar** no assistente **Gerenciar publicação.**

   ![screen_shot_2019-02-07at120507pm](assets/screen_shot_2019-02-07at120507pm.png)

   >[!NOTE]
   >
   >Aguarde alguns segundos/minutos para que o conteúdo chegue à instância de publicação.

1. Após concluir o fluxo de trabalho de gerenciamento da publicação, você deve acionar a atualização do conteúdo offline no autor, que criará a atualização offline na instância do autor.

   Navegue até o painel do canal e clique em **Atualizar conteúdo** offline. Essa ação encaminha o mesmo comando para publicar a instância, de modo que os zips offline também sejam criados na instância de publicação.

   ![screen_shot_2019-02-07at21608pm](assets/screen_shot_2019-02-07at21608pm.png)

   >[!CAUTION]
   >
   >Primeiro, você deve publicar e depois acionar a atualização do conteúdo offline, como resumido nas etapas anteriores.

### Reatribuição de canal e dispositivo: {#channel-and-device-re-assignment}

Se você tiver atribuído novamente um dispositivo, deverá publicar a exibição inicial e a nova exibição, assim que o dispositivo for atribuído novamente à nova exibição.

Da mesma forma, se você tiver atribuído novamente um canal, deverá publicar a exibição inicial e a nova exibição, assim que o canal tiver sido atribuído novamente à nova exibição.