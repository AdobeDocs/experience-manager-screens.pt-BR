---
title: Guia de início rápido
description: Saiba como criar um projeto de demonstração do AEM Screens. Ele ajuda a criar uma experiência de sinalização digital começando pela instalação e configuração de um novo projeto para visualizar seu conteúdo no AEM Screens Player.
feature: Overview, Digital Signage
role: User
level: Beginner
exl-id: 9b7c7f50-2846-4727-a0ec-0220b4cd52c4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 2%

---

# Guia de início rápido {#kickstart-guide}

O início rápido do AEM Screens demonstra como configurar e executar um projeto do AEM Screens. Ele orienta você na configuração de uma experiência básica de sinalização digital e na adição de conteúdo, como ativos e/ou vídeos, a cada canal e na publicação adicional do conteúdo em um AEM Screens Player.

>[!NOTE]
>Antes de trabalhar nos detalhes do projeto, verifique se você instalou o Pacote de recursos mais recente do AEM Screens. Você pode baixar o Feature Pack mais recente do [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID.

## Pré-requisitos {#prerequisites}

Siga as etapas abaixo para criar um projeto de amostra para o AEM Screens e publicar conteúdo no Screens Player.

>[!NOTE]
>O tutorial a seguir mostra a reprodução do conteúdo de seu canal em um reprodutor de SO Chrome.

>[!IMPORTANT]
>**Configurações OSGi**
>&#x200B;>Você deve ativar o referenciador vazio para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade referenciador vazia estiver desativada, o dispositivo não poderá postar uma captura de tela. Atualmente, alguns desses recursos só estarão disponíveis se a opção `Apache Sling` Permitir Filtro de Referenciador Vazio estiver habilitada na Configuração OSGi. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.
>&#x200B;>Siga as etapas abaixo para habilitar a ***Permissão de Filtro Referenciador Apache Sling***:


## Permitir Solicitações de Referenciador Vazias {#allow-empty-referrer-requests}

1. Navegue até **Configuração do Console Web do Adobe Experience Manager** por meio da instância do AEM > ícone de martelo > **Operações** > **Console Web**.

   ![imagem](assets/config/empty-ref1.png)

1. **A Configuração do Console da Web do Adobe Experience Manager** é aberta. Pesquisar referenciador do sling.

   Para pesquisar a propriedade do referenciador do sling, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

1. Marque a opção **Permitir vazio**, conforme mostrado na figura abaixo.

   ![imagem](assets/config/empty-ref2.png)

1. Clique em **Salvar** para habilitar a Permissão de Filtro do Referenciador Apache Sling Vazia.

## Criação de uma experiência de sinalização digital em 5 minutos {#creating-a-digital-signage-experience-in-minutes}

### Criação de um projeto do AEM Screens {#creating-project}

A primeira etapa é criar um projeto do AEM Screens.

1. Navegue até a instância do Adobe Experience Manager (AEM) e clique em **Screens**. Como alternativa, você pode navegar diretamente de `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Clique em **Criar projeto do Screens** para criar um projeto do Screens.
1. Insira o título como **DemoScreens** e clique em **Salvar**.

   ![imagem](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Depois de criar o projeto, ele o traz de volta à página inicial do Projeto do AEM Screens. Agora você pode clicar no seu projeto. Em um projeto, há cinco pastas diferentes chamadas **Aplicativos**, **Canais**, **Dispositivos**, **Locais** e **Agendamentos**.

### Criação de um canal {#creating-channel}

Depois de criar o projeto do AEM Screens, crie um canal onde você gerencia o conteúdo.

Siga as etapas abaixo para criar um canal para seu projeto:

1. Depois de criar um projeto, clique no projeto **DemoScreens** e clique na pasta **Channels**, como mostrado na figura abaixo. Clique em **+ Criar** na barra de ações.

   ![imagem](assets/kickstart/demo-2.png)

1. Escolha o **Canal de Sequência** no assistente e clique em **Avançar**.
   ![imagem](assets/kickstart/demo-3.png)

1. Insira o **Title** como **TestChannel** e clique em **Criar**.

   ![imagem](assets/kickstart/demo-4.png)

   O **TestChannel** agora é adicionado à sua pasta de canais, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-5.png)

### Adicionar conteúdo a um canal {#adding-content}

Quando tiver seu canal em vigor, adicione ao seu canal o conteúdo que o AEM Screens Player pode exibir.

Siga as etapas abaixo para adicionar conteúdo ao canal (**TestChannel**) no seu projeto:

1. Navegue até o **DemoProject** criado e clique em **TestChannel** na pasta **Channels**.

1. Clique em **Editar** na barra de ações (veja a figura abaixo). O editor do **TestChannel** se abre.

   ![imagem](assets/kickstart/demo-6.png)

1. Clique no ícone que alterna o painel lateral no lado esquerdo da barra de ações para abrir os ativos e componentes.

1. Arraste e solte os componentes que deseja adicionar ao canal.

   ![imagem](assets/kickstart/demo-7.png)

### Criação de um local {#creating-location}

Quando tiver seu canal em vigor, crie um local.

>[!NOTE]
>Os ***Locais*** compartimentalizam suas várias experiências de sinalização digital e contêm as configurações das exibições de acordo com onde as várias telas estão.

Siga as etapas abaixo para criar uma localização para seu projeto:

1. Navegue até o **DemoProject** criado e clique na pasta **Locais**.
1. Clique em **+ Criar** na barra de ações.
1. Clique em **Local** no assistente e em **Avançar**.
1. Digite o **Nome** da sua localização (digite o título como **TestLocation**) e clique em **Criar**.

O **TestLocation** foi criado e adicionado à sua pasta **Locations**.


### Criação de uma Exibição para Local {#creating-display}

Depois de criar um local, crie uma exibição para o seu local.

>[!NOTE]
>***Exibição*** representa a experiência digital executada em uma ou várias telas.

1. Navegue até **TestLocation** e clique nele.
1. Clique em **Criar** na barra de ações.

   ![imagem](assets/kickstart/demo-disp1.png)

1. Clique em **Exibir** do assistente **Criar** e clique em **Avançar**.

   ![imagem](assets/kickstart/demo-disp2.png)

1. Insira o **Título** como **LobbyDisplay** e clique em **Criar**.

   ![imagem](assets/kickstart/demo-disp3.png)

   Uma nova exibição chamada **TestDisplay** agora é adicionada ao seu local **TestLocation**, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-disp4.png)

### Atribuição de um canal {#assigning-channel}

Quando a configuração do projeto for concluída, atribua o canal a uma exibição para visualizar o conteúdo.

1. Navegue até a exibição necessária de **DemoScreens** > **Locations** > **TestLocation** > **LobbyDisplay**.

1. Clique em **Atribuir canal** na barra de ações.

   ![imagem](assets/kickstart/demo-assign1.png)

   Ou,

   Clique em **Painel** na barra de ações e em **+Atribuir Canal** no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

   ![imagem](assets/kickstart/demo-assign2.png)

1. A caixa de diálogo **Atribuição de canal** é aberta.

1. Na opção **Configurações**, escolha o canal **por caminho** e **Eventos com Suporte**, como **Carregamento Inicial** e **Tela Ociosa**.

   >[!NOTE]
   >
   >Os **Métodos de Função de Canal**, **Prioridade** e **Interrupção** são preenchidos por padrão. Consulte a seção [Propriedades de Canal](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) para obter mais informações sobre propriedades de atribuição de canal.

   ![imagem](assets/kickstart/demo-assign3.png)

   Além disso, você pode clicar na **Janela de Ativação** e **Agenda de Recorrência**.

   >[!NOTE]
   >O *Cronograma de Recorrência* permite que você defina um cronograma recorrente para o seu canal. Você pode configurar vários agendamentos de recorrência para um canal.
   >Consulte [Agendamento de recorrência](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) para obter mais detalhes.

1. Clique em **Salvar** depois de configurar suas preferências.

### Registrando um dispositivo e atribuindo um dispositivo a uma exibição {#registering-device}

Registre seu dispositivo usando o painel do AEM.

>[!IMPORTANT]
>O Chrome OS player pode ser instalado como um plug-in de navegador Chrome no modo de desenvolvedor, sem exigir um dispositivo Chrome Player real. Para instalação, siga as etapas abaixo:
>
>1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
>1. Descompacte-o e salve-o no disco.
>1. Abra o navegador Chrome e clique em **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
>1. Ative o **Modo de desenvolvedor** no canto superior direito.
>1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
>1. Verifique o plug-in **AEM Screens Chrome Player** se ele estiver disponível na lista de extensões.
>1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
>1. Clique em Plug-in **AEM Screens** para iniciar o Chrome Player. Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **Esc** para sair do modo de tela cheia.

Depois que o reprodutor do sistema operacional Chrome estiver ativado, siga as etapas abaixo para registrar um dispositivo Chrome.

1. Acesse a pasta **Dispositivos** do seu projeto a partir da instância do AEM.

1. Clique no **Gerenciador de Dispositivos** na barra de ações.

   ![imagem](assets/kickstart/demo-register1.png)

1. Clique em **Device Registration** no canto superior direito.

1. Clique no dispositivo necessário e clique em **Registrar Dispositivo**.

   ![imagem](assets/kickstart/demo-register2.png)

1. Aguarde o dispositivo enviar o código de registro e verifique simultaneamente o **Código de Registro** do dispositivo Chrome.
   ![imagem](assets/kickstart/demo-register3.png)

1. Se o **Código de Registro** for o mesmo em ambos os computadores, clique em **Validar** no AEM.

1. Defina o nome desejado como **ChromeDeviceforDemo** para o dispositivo e clique em **Registrar**.

   ![imagem](assets/kickstart/demo-register4.png)

1. Clique em **Atribuir exibição** na caixa de diálogo **Registro de dispositivo bem-sucedido**.

   ![imagem](assets/kickstart/demo-register5.png)

1. Clique no caminho para exibição como **DemoScreens** > **Locations** > **TestLocation** > **LobbyDisplay** e clique em **Assign**.

   ![imagem](assets/kickstart/demo-device6.png)

1. Quando o dispositivo for atribuído com êxito, você verá a seguinte confirmação.

   ![imagem](assets/kickstart/demo-register8.png)

1. Clique em **Concluir** para concluir o processo de registro. Agora você pode exibir seu dispositivo registrado no painel de exibição.

   ![imagem](assets/kickstart/demo-register9.png)

### Visualização de conteúdo no Chrome Player {#viewing-content-output}

Todos os ativos em seu canal agora estão sendo reproduzidos no reprodutor de SO da Chrome.

Parabéns! Agora você está reproduzindo conteúdo em um canal do AEM Screens.

![imagem](assets/kickstart/demo-video-screens.gif)
