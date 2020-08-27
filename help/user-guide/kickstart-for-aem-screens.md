---
title: Guia de Início Rápido
seo-title: Guia de Início Rápido
description: Siga esta página para criar um projeto de demonstração do AEM Screens. Ajuda a criar uma experiência de assinatura digital começando pela instalação e configurando um novo projeto para exibir seu conteúdo no AEM Screens player.
translation-type: tm+mt
source-git-commit: 8ffa53c6ffb24ff80adfdce33a69a9d80e03bb75
workflow-type: tm+mt
source-wordcount: '1630'
ht-degree: 13%

---


# Guia de Início Rápido {#kickstart-guide}

Esta seção é um início rápido para a AEM Screens e mostra como realizar ações básicas. Ele o orienta a configurar uma experiência básica de sinalização digital com conteúdo/ativos e publicação em um player do Screens.

## Criação de uma experiência com cartazes digitais em 5 minutos {#creating-a-digital-signage-experience-in-minutes}

As etapas a seguir permitem que você crie um projeto de amostra para o Screens e publique conteúdo no Screens player.

Para baixar o **AEM Screens Player**, clique [aqui](https://download.macromedia.com/screens/).


Para obter mais informações sobre a implementação do Chrome OS Player, consulte Console [de gerenciamento do](implementing-chrome-os-player.md) Chrome.

Para instalar e configurar os players de telas em seus dispositivos, consulte [Instalação e configuração de telas](configuring-screens-introduction.md) para obter mais detalhes.

>[!NOTE]
>**Configurações de OSGI**
>É necessário ativar a quem indicou vazia para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade quem indicou vazia estiver desativada, o dispositivo não poderá postar uma captura de tela novamente. Atualmente, alguns desses recursos só estão disponíveis se o Filtro de Quem indicou Apache Sling Permitir vazio estiver ativado na configuração OSGI. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.
>
>
>Siga as etapas abaixo para ativar o Filtro de Quem indicou Sling ***Apache Permitir vazio***:


## Permitir solicitações de Quem indicou vazias {#allow-empty-referrer-requests}

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por AEM instância —> ícone de martelo —> **Operações** —> Console **da** Web.

   ![imagem](assets/config/empty-ref1.png)

1. **A Configuração** do Adobe Experience Manager Web Console é aberta. Procure por quem indicou de sling.

   Para pesquisar a propriedade sling quem indicou, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

1. Marque a opção **Permitir vazio** , conforme mostrado na figura abaixo.

   ![imagem](assets/config/empty-ref2.png)

1. Clique em **Salvar** para ativar o Filtro de Quem indicou Apache Sling Permitir vazio.


## Tutorial {#tutorial}

1. **Criação de um novo projeto**

   1. Selecione o link do Adobe Experience Manager (parte superior esquerda) e o **Screens**. Como alternativa, você pode navegar diretamente para `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

   1. Clique em **Criar** para criar um novo projeto do Screens (consulte a figura abaixo).
   1. Select **Screens** from the **Create Screens Project** wizard and click **Next**.

   1. Enter the title as *Test_Project*  and click **Create**.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Depois que o projeto é criado, ele o traz de volta ao console do Screens Project. Agora, você pode selecionar seu projeto. Em um projeto, existem cinco tipos de pastas, **Aplicativos**, **Canais**, **Dispositivos**, **Locais** e **Agendamentos**, conforme mostrado na figura abaixo.

   >[!NOTE]
   >
   >Os agendamentos só estarão disponíveis se você tiver instalado o AEM 6.3 Sites Feature Pack 1. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   Consulte [Criar e gerenciar projetos](creating-a-screens-project.md) de telas para obter mais detalhes.

1. **Criação de um novo canal**

   Depois que o projeto estiver em andamento, será necessário criar um novo canal no qual você gerenciará o conteúdo.

   Siga as etapas abaixo para criar um novo canal para seu projeto:

   1. Navigate to the *Test_Project* you created and select the **Channels** folder.

   1. Click **Create** from the action bar (see the figure below). Um assistente será aberto.
   1. Choose the **Sequence Channel** and click **Next**.

   1. Enter the **Name** and **Title** as *TestChannel* and click **Create**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

   O *TestChannel* é criado e adicionado à pasta canais, como mostrado na figura abaixo.

   ![chlimage_1-7](assets/chlimage_1-7.png)

   Consulte Gerenciamento [de](managing-channels.md) Canais para obter mais detalhes sobre como criar e gerenciar canais.

1. **Adicionar conteúdo a um Canal**

   Depois que o canal estiver no lugar, você precisará adicionar conteúdo ao canal que o Reprodutor do Screens exibirá.

   Siga as etapas abaixo para adicionar conteúdo ao canal (*TestChannel*) em seu projeto:

   1. Navigate to the *Test_Project* you created and select the **Channels** folder.

   1. Click **Edit** from the action bar (see the figure below). The editor for the *TestChannel* opens.

   1. Clique no ícone que alterna o painel lateral no lado esquerdo da barra de ações para abrir os ativos e componentes.
   1. Arraste e solte os componentes que você deseja adicionar ao seu canal.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   Neste exemplo, o editor mostra uma imagem adicionada ao canal.

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. **Criação de uma nova localização**

   Depois que o canal estiver no lugar, é necessário criar o local.

   ***Os locais*** compartimentalizam suas várias experiências de sinalização digital e contêm as configurações dos monitores de acordo com onde estão as várias telas.

   Siga as etapas abaixo para criar um novo local para seu projeto:

   1. Navigate to the *Test_Project* you created and select the **Locations** folder.

   1. Clique em **Criar** ao lado do ícone de adição na barra de ação (consulte a figura abaixo). Um assistente será aberto.
   1. Select **Location** from the wizard and click **Next**.

   1. Enter the **Name** and **Title** for your location (enter the title as *TestLocation*) and click **Create**.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   O *TestLocation* é criado e adicionado à pasta **Locais** .

   ![chlimage_1-11](assets/chlimage_1-11.png)

1. **Criação de uma nova exibição para *TestLocation***

   Depois de criar um local, é necessário criar uma nova exibição para o seu local.

   ***As telas*** representam a experiência digital executada em uma ou várias telas.

   1. Navegue até o local onde deseja criar sua exibição (*Test_* Project —> **Locais** —> *TestLocation)* , conforme mostrado na figura acima, e selecione *TestLocation*.

   1. Clique em **Criar** na barra de ações.
   1. Select **Display** from the **Create** wizard and click **Next**.

   1. Insira **Nome** e **Título** para o local de exibição (insira o título como *TestDisplay*).

   1. Under the **Display** tab, choose the details of the Layout.

      1. Choose the **Resolution** as **Full HD**.

      1. Choose the **Number of Devices Horizontally** as 1.
      1. Choose the **Number of Devices Vertically** as 1.
   1. Clique em **Criar**.

   Uma nova tela (*TestDisplay*) é adicionada à sua localização *TestLocation)*, como mostrado na figura abaixo.

   ![chlimage_1-12](assets/chlimage_1-12.png)

1. **Adicionando um agendamento**

   No AEM Screens, o recurso *Agendamentos* permite organizar canais em grupos reutilizáveis, para que você não precise repetir a atribuição individualmente para cada exibição na qual deseja mostrar seu conteúdo.

   >[!NOTE]
   >
   >Esta funcionalidade do Screens só estará disponível se você tiver instalado o AEM 6.3 Sites Feature Pack 1. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

   1. Navegue até a pasta **Programações** de Test_Project —> **Programações**.

   1. Clique em **Criar** na barra de ações. Um assistente será aberto.
   1. Selecione **Agendar** na página do assistente **Criar** .

   1. Informe o **Nome** e o **Título** como *MorningSchedule* na página de propriedades.

   1. Clique em **Criar** e o agendamento será adicionado à pasta **Programações** , como mostrado na figura abaixo.

   ![chlimage_1-13](assets/chlimage_1-13.png)

   Além disso, selecione o agendamento (*MorningSchedule*) e clique em **Painel** na barra de ação para visualização do painel agendado. Você pode visualização/alterar as propriedades do agendamento, atribuir canais e visualização atribuída a exibições usando o painel.

   ![chlimage_1-14](assets/chlimage_1-14.png)

   Consulte [Criar e gerenciar programações](managing-schedules.md) para obter informações detalhadas sobre programações.

1. **Atribuição de um canal**

   1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

   1. Select *TestDisplay* and tap/click **Assign Channel **from the action bar, *Or*,

   1. Click **Dashboard** and select **+Assign Channel** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure below. **A caixa de diálogo Atribuição** do canal é aberta.

   1. Select **Reference Channel** by **path**

   1. Enter the **Channel Role** as *LiveStream*.

   1. Selecione o Caminho **do** Canal (*Test_Project* —> *Canais* —> *TestChannel* ) no **Canal**.

   1. Select the **Priority** for this channel as *1*.

   1. Choose the **Supported Events** as **Initial Load** and **Idle Screen**.

   1. Informe **Agendamento** e selecione as datas em **ativo** e **ativo até**.

   1. Clique em **Salvar**.

   O canal é criado e adicionado ao painel.

   ![chlimage_1-15](assets/chlimage_1-15.png)

   Para saber mais sobre a caixa de diálogo Atribuição de **Canais** e as propriedades associadas a ela, consulte [Atribuir Canais](channel-assignment.md).

1. **Adicionar programação a um Canal**

   1. Navigate to the display from *Test_Project* --> **Locations** --> *TestLocation* --> *TestDisplay*.

   1. Click **Dashboard** and select **+Assign Schedule** at the top right from **ASSIGNED CHANNELS &amp; SCHEDULES** panel, as shown in the figure above. **A caixa de diálogo Agendar atribuição** é aberta.

   1. Escolha o caminho onde você criou seu agendamento (aqui, *Test_Project* —> **Programações** —> *MorningSchedule*).

   1. Clique em **Salvar** para adicionar seu agendamento ao canal.

   ![chlimage_1-16](assets/chlimage_1-16.png)

1. **Registrando um dispositivo**

   Você precisa registrar seu dispositivo usando o painel AEM.

   >[!NOTE]
   >
   >Você pode abrir o Screens player usando o aplicativo AEM Screens que você baixou ou usando o navegador da Web.

   Para visualização do dispositivo pendente:

   1. Inicialize uma janela de navegador separada.
   1. Go to Screens player using the *web browser* `https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. Ao abrir o dispositivo, você perceberá o estado do dispositivo como não registrado.
   1. From the AEM dashboard, navigate to *Test_Project* --> **Devices**

   1. Click **Device Manager** from the action bar.
   1. Clique em **Device Registration (Registro** do dispositivo) e você verá os dispositivos pendentes, conforme mostrado na figura abaixo.

   ![chlimage_1-17](assets/chlimage_1-17.png)

   Select the device you want to register and click **Register Device**.

   ![chlimage_1-18](assets/chlimage_1-18.png)

   Você precisará validar o código verificando-o no navegador da web ou no player do AEM Screens.

   Click **Validate** to navigate to **Device Registration** screen.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   Enter **Title** and click **Register** and the device will be registered.

   Clique em **Concluir** para concluir a etapa de registro do dispositivo.

   ![chlimage_1-20](assets/chlimage_1-20.png)

   Clicar em **Concluir** retorna à página do dispositivo que exibe dispositivos não atribuídos e atribuídos.

   ![chlimage_1-21](assets/chlimage_1-21.png)

   >[!NOTE]
   >
   >O dispositivo adicionado é exibido como **Não atribuído** em Status **atribuído** .

1. **Atribuindo o dispositivo à exibição**

   Depois de registrar o dispositivo, é necessário atribuí-lo a uma tela.

   Siga as etapas abaixo para atribuir um dispositivo:

   1. Selecione o dispositivo que deseja atribuir.
   1. Click **Assign Device** from the action bar.
   1. Selecione o caminho de exibição para seu canal como `/content/screens/Test_Project/***Locations***/TestLocation/TestDisplay.`

   1. Click **Assign**.
   1. Click **Finish** to complete the process, and now the device is assigned.

   ![chlimage_1-22](assets/chlimage_1-22.png)

   O painel de exibição é aberto e você verá todas as informações relacionadas aos canais e programações atribuídos junto com os detalhes de configuração do dispositivo.

   ![screen_shot_2017-12-18at122041pm](assets/screen_shot_2017-12-18at122041pm.png)

### Viewing the content in Screens Player {#viewing-the-content-in-screens-player}

Depois que você tiver adicionado as configurações acima, o player deverá mostrar automaticamente o canal padrão para a exibição em seu dispositivo, por exemplo, uma imagem (nesse cenário, um canal de sequência e o conteúdo estará visível no Screens Player para o navegador da Web).

![chlimage_1-23](assets/chlimage_1-23.png)

Consulte [AEM Screens Player](working-with-screens-player.md) para obter informações mais detalhadas sobre o AEM Screens player.
