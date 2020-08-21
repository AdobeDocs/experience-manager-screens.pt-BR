---
title: Reconhecimento de voz no AEM Screens
description: A página descreve o recurso de reconhecimento de voz no AEM Screens.
translation-type: tm+mt
source-git-commit: c46cd26f5067468aadf80a822fffce1d5f0b5d9a
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# Reconhecimento de voz no AEM Screens {#voice-recognition}

## Visão geral {#overview}

O recurso de Reconhecimento de voz permite a alteração do conteúdo em um canal AEM Screens orientada pela interação de voz.

Um autor de conteúdo pode configurar uma exibição para ser habilitada para voz. Isso permite que todos os jogadores registrados na tela entendam o discurso. Você deve ativar o reconhecimento de voz para a Exibição e associar cada canal a uma tag exclusiva para acionar uma transição de canal.

>[!NOTE]
>O hardware do player deve suportar a entrada de voz, como um microfone.

>[!IMPORTANT]
> O recurso Reconhecimento de voz está disponível somente nos players Chrome e Eletron.

## Implementação do reconhecimento de voz {#implementing}

A seção a seguir descreve como você pode ativar e usar o recurso Reconhecimento de voz em um projeto da AEM Screens.

### Configuração do projeto {#setting-up}

Antes de usar o recurso Reconhecimento de voz, verifique se você tem um projeto e um canal com conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **VoiceDemo** e três canais de sequência **Main**, **ColdBeinks** e **HotDrinks**, como mostrado na figura abaixo.

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criação e gerenciamento de Canais](/help/user-guide/managing-channels.md)

1. Navegue até cada canal e adicione conteúdo. Por exemplo, navegue até **VoiceDemo** —> **Canais** —> **Principal** e selecione o canal. Clique em **Editar** na barra de ações para abrir o editor e adicionar conteúdo (imagens/vídeos) conforme necessário. Da mesma forma, adicione conteúdo a **ColdDrinks** e ao canal **HotDrinks** .

   Os canais agora contêm o seguinte conteúdo, como mostrado nas figuras abaixo.

   **Principal**:

   **Bebidas frias**:

   **HotBeinks**:

### Configuração de tags para Canais {#setting-tags}

Depois de adicionar o conteúdo aos canais, é necessário navegar até cada um dos canais e adicionar as tags apropriadas que acionariam o reconhecimento de voz.

Siga as etapas abaixo para adicionar tags ao seu canal:

1. Navegue até cada canal e adicione conteúdo. Por exemplo, navegue até **VoiceDemo** —> **Canais** —> **Principal** e selecione o canal.

1. Click **Properties** from the action bar.

1. Navegue até a guia **Noções básicas** e selecione uma tag já existente no campo **Tags** ou crie uma nova.

1. Clique em **Salvar e fechar** quando terminar.


### Atribuindo Canal a uma exibição {#channel-assignment}

1. Crie uma exibição na pasta **Locais** , como mostrado na figura abaixo.

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criar e gerenciar exibições](/help/user-guide/managing-displays.md).

1. Atribua os canais **Principal**, **ColdBeinks** e **HotDrinks** ao seu **LobbyDisplay**.


1. Defina as seguintes propriedades para cada um dos canais.

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criar e gerenciar exibições](/help/user-guide/managing-displays.md).

1. Depois de atribuir canais a uma exibição, navegue até **Sala de espera** e selecione a exibição. Na barra de ações, selecione **Propriedades** .

1. Navegue até a guia **Exibir** e ative a opção **Voz ativada** em **Conteúdo**.

   >[!NOTE]
   >É obrigatório ativar o recurso de reconhecimento de voz da tela.

## Visualização do conteúdo no Chrome Player {#viewing-content}

Quando as etapas anteriores estiverem concluídas, você poderá registrar seu dispositivo de cromo e visualização a saída.

Siga as etapas abaixo:

1. Navegue até a pasta **Dispositivos** e clique em Gerenciador **de** dispositivos na barra de ações para registrar os dispositivos.







