---
title: Guia de Início Rápido
seo-title: Guia de Início Rápido
description: Siga esta página para criar um projeto de demonstração do AEM Screens. Ajuda a criar uma experiência de assinatura digital começando pela instalação e configurando um novo projeto para exibir seu conteúdo no AEM Screens player.
translation-type: tm+mt
source-git-commit: 12d84eba2b9001600f783cd4f994af43d2c16739
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 5%

---


# Guia de Início Rápido {#kickstart-guide}

Esta seção é um kickstart para a AEM Screens e demonstra como configurar e executar um projeto da AEM Screens. Ele o orienta a configurar uma experiência básica de sinalização digital e adicionar conteúdo, como ativos e/ou vídeos, a cada canal e a publicar o conteúdo em um AEM Screens player.

>[!NOTE]
>Antes de start para trabalhar nos detalhes do projeto, certifique-se de ter instalado o Feature Pack mais recente. Você pode baixar o pacote de recursos mais recente para a versão AEM Screens 6.5.5 do Portal [de distribuição de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) software usando seu Adobe ID.

## Pré-requisitos {#prerequisites}

Siga as etapas abaixo para criar um projeto de amostra para o AEM Screens e publicar ainda mais o conteúdo no Screens player.

>[!NOTE]
>O tutorial a seguir mostra o conteúdo do seu canal no Chrome OS player.

>[!IMPORTANT]
>**Configurações do OSGi**
>É necessário ativar a quem indicou vazia para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade quem indicou vazia estiver desativada, o dispositivo não poderá postar uma captura de tela novamente. Atualmente, alguns desses recursos estão disponíveis somente se o Filtro de Quem indicou Apache Sling Permitir vazio estiver ativado na Configuração do OSGi. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.
>Siga as etapas abaixo para ativar o Filtro de Quem indicou Sling ***Apache Permitir vazio***:


## Permitir solicitações de Quem indicou vazias {#allow-empty-referrer-requests}

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por AEM instância —> ícone de martelo —> **Operações** —> Console **da** Web.

   ![imagem](assets/config/empty-ref1.png)

1. **A Configuração** do Adobe Experience Manager Web Console é aberta. Procure por quem indicou de sling.

   Para pesquisar a propriedade sling quem indicou, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

1. Marque a opção **Permitir vazio** , conforme mostrado na figura abaixo.

   ![imagem](assets/config/empty-ref2.png)

1. Clique em **Salvar** para ativar o Filtro de Quem indicou Apache Sling Permitir vazio.


## Criação de uma experiência com cartazes digitais em 5 minutos {#creating-a-digital-signage-experience-in-minutes}

### Creating an AEM Screens Project {#creating-project}

A primeira etapa é criar um novo projeto AEM Screens.

1. Navegue até a instância do Adobe Experience Manager (AEM) e clique em **Telas**. Como alternativa, você pode navegar diretamente de `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Click **Create Screens Project** to create a new Screens project. Enter the title as **DemoScreens** and click **Save**.

   ![imagem](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Depois que você cria o projeto, ele o traz de volta ao home page do Screens Project. Agora, você pode selecionar seu projeto. Em um projeto, há cinco pastas diferentes intituladas **Aplicativos**, **Canais**, **Dispositivos**, **Locais** e **Agendamentos**.


### Criação de um canal {#creating-channel}

Depois que o projeto estiver em andamento, será necessário criar um novo canal no qual você gerenciará o conteúdo.

Siga as etapas abaixo para criar um novo canal para seu projeto:

1. Depois de criar um projeto, selecione o projeto **DemoScreens** e selecione a pasta **** Canais, como mostrado na figura abaixo. Click **+ Create** from the action bar.

   ![imagem](assets/kickstart/demo-2.png)

1. Escolha o Canal **de** sequência no assistente e clique em **Avançar**.
   ![imagem](assets/kickstart/demo-3.png)

1. Enter the **Title** as *TestChannel* and click **Create**.

   ![imagem](assets/kickstart/demo-4.png)

   O *TestChannel* é criado e adicionado à pasta canais, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-5.png)

### Adding Content to a Channel {#adding-content}

Depois que o canal estiver no lugar, você precisará adicionar conteúdo ao canal que o Reprodutor do Screens exibirá.

Siga as etapas abaixo para adicionar conteúdo ao canal (*TestChannel*) em seu projeto:

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Edit** from the action bar (see the figure below). The editor for the **TestChannel** opens.

   ![imagem](assets/kickstart/demo-6.png)

1. Clique no ícone que alterna o painel lateral no lado esquerdo da barra de ações para abrir os ativos e componentes.

1. Arraste e solte os componentes que você deseja adicionar ao seu canal.

   ![imagem](assets/kickstart/demo-7.png)

### Criação de uma localização {#creating-location}

Depois de colocar o canal no lugar, é necessário criar um local.

>[!NOTE]
>***Os locais*** compartimentalizam suas várias experiências de sinalização digital e contêm as configurações dos monitores de acordo com onde estão as várias telas.

Siga as etapas abaixo para criar um novo local para seu projeto:

1. Navigate to the **DemoProject** you created and select the **Locations** folder.

1. Click **+ Create** from the action bar.

1. Select **Location** from the wizard and click **Next**.

1. Enter the **Name** for your location (enter the title as *TestLocation*) and click **Create**.

O **TestLocation** é criado e adicionado à pasta **Locais** .


### Criação de uma exibição para localização {#creating-display}

Depois de criar um local, é necessário criar uma nova exibição para o seu local.

>[!NOTE]
>***As telas*** representam a experiência digital executada em uma ou várias telas.

1. Navegue até **TestLocation** e selecione-o.

1. Clique em **Criar** na barra de ações.

   ![imagem](assets/kickstart/demo-disp1.png)

1. Select **Display** from the **Create** wizard and click **Next**.

   ![imagem](assets/kickstart/demo-disp2.png)

1. Enter the **Title** as **LobbyDisplay** and click **Create**.

   ![imagem](assets/kickstart/demo-disp3.png)

   Uma nova tela chamada **TestDisplay** agora é adicionada à sua localização **TestLocation**, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-disp4.png)

### Assigning a Channel {#assigning-channel}

Quando a configuração do projeto for concluída, você deverá atribuir o canal a uma exibição para visualização do conteúdo.

1. Navegue até a exibição necessária de **DemoScreens** —> **Locais** —> **TestLocation** —> **LobbyDisplay**.

1. Tap/click **Assign Channel** from the action bar.

   ![imagem](assets/kickstart/demo-assign1.png)

   Ou,

   Toque/clique em **Painel** na barra de ações e clique em **+Atribuir Canal** do painel CANAIS e AGENDAMENTOS **** ATRIBUÍDOS.

   ![imagem](assets/kickstart/demo-assign2.png)

1. The **Channel Assignment** dialog box opens.

1. Na opção **Configurações** , escolha o canal **por caminho** e Eventos **** suportados como **Carregamento** inicial e Tela **** inativa.

   >[!NOTE]
   >
   >Por padrão, a função **do** Canal, a **prioridade** e os métodos **de** interrupção são preenchidos. Consulte a seção Propriedades [do](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) Canal para saber mais sobre as propriedades de atribuição do canal.

   ![imagem](assets/kickstart/demo-assign3.png)

   Além disso, você também pode selecionar a Janela **de** Ativação e a Programação **de** recorrência.

   >[!NOTE]
   >A Programação *de* recorrência permite definir uma programação recorrente para o seu canal. Você configura várias programações de recorrência para um canal.
   >Consulte Agendamento de [recorrência](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) para obter mais detalhes.

1. Clique em **Salvar** depois de configurar suas preferências.

### Registrando um dispositivo e atribuindo um dispositivo a um monitor {#registering-device}

Você precisa registrar seu dispositivo usando o painel AEM.

>[!IMPORTANT]
>O ChromeOS player pode ser instalado como plug-in do Chrome Browser no modo de desenvolvedor, sem a necessidade de um dispositivo de player de cromo. Para a instalação, siga as etapas abaixo:
>
>1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
>1. Descompacte e salve no disco.
>1. Abra o navegador Chrome e selecione **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
>1. Ligue o modo **Desenvolvedor** no canto superior direito.
>1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
>1. Verifique se o plug-in do **AEM Screens Chrome Player** está disponível na lista de extensões.
>1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
>1. Clique em **AEM Screens** Plugin para iniciar o Chrome Player. Por padrão, o player é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.


Quando o player do ChromeOS estiver ativado, siga as etapas abaixo para registrar um dispositivo Chrome.

1. Navegue até a pasta **Dispositivos** do seu projeto a partir da instância AEM.

1. Tap/click the **Device Manager** from the action bar.

   ![imagem](assets/kickstart/demo-register1.png)

1. Toque/clique em **Device Registration (Registro** do dispositivo) na parte superior direita.

1. Selecione o dispositivo desejado e toque/clique em **Registrar dispositivo**.

   ![imagem](assets/kickstart/demo-register2.png)

1. Aguarde o dispositivo enviar o código de registro e, simultaneamente, verifique o Código **de** registro do dispositivo Chrome.
   ![imagem](assets/kickstart/demo-register3.png)

1. Se o Código **** de registro for o mesmo em ambos os computadores, toque/clique em **Validar** no AEM.

1. Defina o nome desejado como **ChromeDeviceforDemo** para o dispositivo e clique em **Registrar**.

   ![imagem](assets/kickstart/demo-register4.png)

1. Clique em **Atribuir exibição** na caixa de diálogo Registro de **dispositivo bem-sucedido** .

   ![imagem](assets/kickstart/demo-register5.png)

1. Selecione o caminho para sua exibição como **DemoScreens** —> **Locais** —> **TestLocation** —> **LobbyDisplay** e clique em **Atribuir**.

   ![imagem](assets/kickstart/demo-device6.png)

1. Depois que o dispositivo for atribuído com êxito, você verá a seguinte confirmação.

   ![imagem](assets/kickstart/demo-register8.png)

1. Tap/click **Finish** to complete the registration process.

1. Você deve ser capaz de visualização seu dispositivo registrado do painel de exibição.

   ![imagem](assets/kickstart/demo-register9.png)

### Exibição do conteúdo no Chrome Player {#viewing-content-output}

Todos os ativos em seu canal agora estão sendo reproduzidos em seu dispositivo Chrome.

Parabéns por você estar reproduzindo conteúdo em um canal AEM Screens!

![imagem](assets/kickstart/demo-video-screens.gif)






