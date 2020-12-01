---
title: Guia de Início Rápido
seo-title: Guia de Início Rápido
description: Siga esta página para criar um projeto de demonstração do AEM Screens. Ajuda a criar uma experiência de assinatura digital começando pela instalação e configurando um novo projeto para exibir seu conteúdo no AEM Screens player.
translation-type: tm+mt
source-git-commit: 77c81b84631b090333db0095986f634fa99c8223
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 5%

---


# Guia Kickstart {#kickstart-guide}

O kickstart para AEM Screens demonstra como configurar e executar um projeto AEM Screens. Ele o orienta a configurar uma experiência básica de sinalização digital e adicionar conteúdo, como ativos e/ou vídeos, a cada canal e a publicar o conteúdo em um AEM Screens player.

>[!NOTE]
>Antes de start para trabalhar nos detalhes do projeto, certifique-se de ter instalado o Feature Pack mais recente para AEM Screens. Você pode baixar o pacote de recursos mais recente do [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando seu Adobe ID.

## Pré-requisitos {#prerequisites}

Siga as etapas abaixo para criar um projeto de amostra para o AEM Screens e publicar ainda mais o conteúdo no Screens player.

>[!NOTE]
>O tutorial a seguir mostra o conteúdo do seu canal no Chrome OS player.

>[!IMPORTANT]
>**Configurações do OSGi**
>Você deve ativar a quem indicou vazia para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade quem indicou vazia estiver desativada, o dispositivo não poderá postar uma captura de tela novamente. Atualmente, alguns desses recursos estão disponíveis somente se o Filtro de Quem indicou Apache Sling Permitir vazio estiver ativado na Configuração do OSGi. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.
>Siga as etapas abaixo para ativar o ***Filtro de Quem indicou Apache Sling Permitir vazio***:


## Permitir solicitações de Quem indicou vazias {#allow-empty-referrer-requests}

1. Navegue até **Configuração do Adobe Experience Manager Web Console** por AEM instância —> ícone de martelo —> **Operações** —> **Console Web**.

   ![imagem](assets/config/empty-ref1.png)

1. **A** configuração do Adobe Experience Manager Web Console é aberta. Procure por quem indicou de sling.

   Para pesquisar a propriedade de quem indicou sling, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

1. Marque a opção **Permitir vazio**, conforme mostrado na figura abaixo.

   ![imagem](assets/config/empty-ref2.png)

1. Clique em **Salvar** para ativar o Filtro de Quem indicou Apache Sling Permitir vazio.

## Criação de uma experiência de assinatura digital em 5 minutos {#creating-a-digital-signage-experience-in-minutes}

### Criando um projeto do AEM Screens {#creating-project}

A primeira etapa é criar um projeto da AEM Screens.

1. Navegue até a instância do Adobe Experience Manager (AEM) e clique em **Screens**. Como alternativa, você pode navegar diretamente de `https://localhost:4502/screens.html/content/screens](https://localhost:4502/screens.html/content/screens`.

1. Clique em **Criar projeto do Screens** para criar um novo projeto do Screens. Digite o título como **DemoScreens** e clique em **Salvar**.

   ![imagem](assets/kickstart/demo-1.png)

   >[!NOTE]
   >Depois que você cria o projeto, ele o traz de volta ao home page do Screens Project. Agora, você pode selecionar seu projeto. Em um projeto, há cinco pastas diferentes intituladas **Aplicativos**, **Canais**, **Dispositivos**, **Locais** e **Programações**.

### Criação de um canal {#creating-channel}

Depois de criar o projeto do AEM Screens, é necessário criar um novo canal no qual você gerencia o conteúdo.

Siga as etapas abaixo para criar um novo canal para seu projeto:

1. Depois de criar um projeto, selecione o projeto **DemoScreens** e selecione a pasta **Canais**, conforme mostrado na figura abaixo. Clique em **+ Criar** na barra de ações.

   ![imagem](assets/kickstart/demo-2.png)

1. Escolha **Canal de sequência** do assistente e clique em **Próximo**.
   ![imagem](assets/kickstart/demo-3.png)

1. Digite **Title** como **TestChannel** e clique em **Criar**.

   ![imagem](assets/kickstart/demo-4.png)

   O **TestChannel** agora é adicionado à sua pasta de canais, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-5.png)

### Adicionar conteúdo a um Canal {#adding-content}

Depois de colocar o canal no lugar, é necessário adicionar conteúdo ao canal que o AEM Screens player exibirá.

Siga as etapas abaixo para adicionar conteúdo ao canal (**TestChannel**) em seu projeto:

1. Navegue até **DemoProject** que você criou e selecione **TestChannel** na pasta **Canais**.

1. Clique em **Editar** na barra de ações (consulte a figura abaixo). O editor para o **TestChannel** é aberto.

   ![imagem](assets/kickstart/demo-6.png)

1. Clique no ícone que alterna o painel lateral no lado esquerdo da barra de ações para abrir os ativos e componentes.

1. Arraste e solte os componentes que você deseja adicionar ao seu canal.

   ![imagem](assets/kickstart/demo-7.png)

### Criação de uma localização {#creating-location}

Depois de colocar o canal no lugar, é necessário criar um local.

>[!NOTE]
>***Locais*** compartimentalizam suas várias experiências de sinalização digital e contêm as configurações dos monitores de acordo com onde estão as várias telas.

Siga as etapas abaixo para criar um novo local para seu projeto:

1. Navegue até **DemoProject** que você criou e selecione a pasta **Locais**.

1. Clique em **+ Criar** na barra de ações.

1. Selecione **Location** no assistente e clique em **Next**.

1. Digite o **Nome** para o seu local (insira o título como **TestLocation**) e clique em **Criar**.

O **TestLocation** é criado e adicionado à pasta **Locais**.


### Criação de uma exibição para o local {#creating-display}

Depois de criar um local, é necessário criar uma nova exibição para o seu local.

>[!NOTE]
>***Display*** representa a experiência digital executada em uma ou várias telas.

1. Navegue até **TestLocation** e selecione-o.

1. Clique em **Criar** na barra de ações.

   ![imagem](assets/kickstart/demo-disp1.png)

1. Selecione **Display** no assistente **Create** e clique em **Next**.

   ![imagem](assets/kickstart/demo-disp2.png)

1. Digite **Title** como **LobbyDisplay** e clique em **Criar**.

   ![imagem](assets/kickstart/demo-disp3.png)

   Uma nova tela chamada **TestDisplay** agora é adicionada à sua localização **TestLocation**, como mostrado na figura abaixo.

   ![imagem](assets/kickstart/demo-disp4.png)

### Atribuindo um Canal {#assigning-channel}

Quando a configuração do projeto for concluída, você deverá atribuir o canal a uma exibição para visualização do conteúdo.

1. Navegue até a exibição necessária de **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay**.

1. Toque/clique em **Atribuir Canal** na barra de ações.

   ![imagem](assets/kickstart/demo-assign1.png)

   Ou,

   Toque/clique em **Painel** na barra de ações e clique em **+Atribuir Canal** no painel **CANAIS ATRIBUÍDOS e AGENDAMENTOS**.

   ![imagem](assets/kickstart/demo-assign2.png)

1. A caixa de diálogo **Atribuição de Canal** é aberta.

1. Na opção **Settings**, escolha o canal **by path** e **Eventos suportados** como **Carregamento inicial** e **Ecrã inativo**.

   >[!NOTE]
   >
   >As **Função de Canal**, **Prioridade** e **Métodos de Interrupção** são preenchidas por padrão. Consulte a seção [Propriedades do Canal](/help/user-guide/channel-assignment-latest-fp.md#channel-properties) para saber mais sobre as propriedades de atribuição do canal.

   ![imagem](assets/kickstart/demo-assign3.png)

   Além disso, você também pode selecionar **Janela de Ativação** e **Programação de recorrência**.

   >[!NOTE]
   >O *Agendamento de recorrência* permite que você defina uma programação recorrente para o seu canal. Você configura várias programações de recorrência para um canal.
   >Consulte [Agendamento de recorrência](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) para obter mais detalhes.

1. Clique em **Salvar** depois de configurar suas preferências.

### Registrando um dispositivo e atribuindo um dispositivo a um monitor {#registering-device}

Você precisa registrar seu dispositivo usando o painel AEM.

>[!IMPORTANT]
>O Chrome OS player pode ser instalado como plug-in do Chrome Browser no modo de desenvolvedor, sem a necessidade de um dispositivo de player de cromo. Para a instalação, siga as etapas abaixo:
>
>1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Chrome Player mais recente.
>1. Descompacte e salve no disco.
>1. Abra o navegador Chrome e selecione **Extensões** no menu ou navegue diretamente para ***chrome://extensions***.
>1. Ative o **modo Desenvolvedor** a partir do canto superior direito.
>1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.
>1. Verifique o plug-in **AEM Screens Chrome Player** se estiver disponível na lista de extensões.
>1. Abra uma nova guia e clique no ícone **Aplicativos** no canto superior esquerdo ou navegue diretamente para ***chrome://apps***.
>1. Clique em **AEM Screens** Plug-in para iniciar o Chrome Player. Por padrão, o player é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.


Quando o player do Chrome OS estiver ativado, siga as etapas abaixo para registrar um dispositivo Chrome.

1. Navegue até a pasta **Devices** do seu projeto a partir da sua instância AEM.

1. Toque/clique em **Gerenciador de dispositivos** na barra de ações.

   ![imagem](assets/kickstart/demo-register1.png)

1. Toque/clique em **Device Registration** no canto superior direito.

1. Selecione o dispositivo desejado e toque/clique em **Registrar dispositivo**.

   ![imagem](assets/kickstart/demo-register2.png)

1. Aguarde o dispositivo enviar seu código de registro e verifique simultaneamente o **Código de Registro** do dispositivo Chrome.
   ![imagem](assets/kickstart/demo-register3.png)

1. Se **Código de Registro** for o mesmo em ambas as máquinas, toque/clique em **Validar** no AEM.

1. Defina o nome desejado como **ChromeDeviceforDemo** para o dispositivo e clique em **Register**.

   ![imagem](assets/kickstart/demo-register4.png)

1. Clique em **Atribuir vídeo** na caixa de diálogo **Registro de dispositivo bem-sucedido**.

   ![imagem](assets/kickstart/demo-register5.png)

1. Selecione o caminho para sua exibição como **DemoScreens** —> **Locations** —> **TestLocation** —> **LobbyDisplay** e clique em **Atribuir**.

   ![imagem](assets/kickstart/demo-device6.png)

1. Depois que o dispositivo for atribuído com êxito, você verá a seguinte confirmação.

   ![imagem](assets/kickstart/demo-register8.png)

1. Toque/clique em **Finish** para concluir o processo de registro. Você deve ser capaz de visualização seu dispositivo registrado do painel de exibição.

   ![imagem](assets/kickstart/demo-register9.png)

### Visualização do conteúdo no Chrome Player {#viewing-content-output}

Todos os ativos em seu canal agora estão sendo reproduzidos no player do Chrome OS.

Parabéns por você estar reproduzindo conteúdo em um canal AEM Screens!

![imagem](assets/kickstart/demo-video-screens.gif)
