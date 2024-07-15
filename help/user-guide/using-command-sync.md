---
title: Usando a sincronização de comandos
description: Saiba mais sobre como usar a Sincronização de comando no AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# Sincronização de comando {#command-sync}

A página a seguir descreve como usar a Sincronização de Comando. A sincronização de comandos permite a reprodução sincronizada em diferentes reprodutores. Os reprodutores podem reproduzir conteúdo diferente, mas cada ativo deve ter a mesma duração.

>[!IMPORTANT]
>
>Este recurso não oferece suporte a Sequências Incorporadas, Sequências Incorporadas Dinâmicas, Canais de Aplicativos ou Transições.

## Visão geral {#overview}

As soluções de sinalização digital devem suportar paredes de vídeo e reprodução sincronizada. Este cenário é verdadeiro se você estiver tentando suportar cenários como contagens regressivas de Ano Novo ou grandes vídeos fatiados para serem reproduzidos em várias telas. Esses cenários são onde a sincronização de comandos entra em ação.

Para usar a Sincronização de Comandos, um player atua como *principal* e envia o comando, e todos os outros players agem como *clientes* e são reproduzidos quando recebem o comando.

O *principal* envia um comando para todos os clientes registrados quando está prestes a iniciar a reprodução de um item. A carga útil dessa ação pode ser o índice do item a ser reproduzido, o html externo do elemento a ser reproduzido ou ambos.

## Implementando a sincronização de comandos {#using-command-sync}

A seção a seguir descreve como você pode usar a sincronização de comandos em um projeto do AEM Screens.

>[!NOTE]
>
>Para a reprodução sincronizada, é necessário que todos os dispositivos de hardware tenham as mesmas especificações de hardware e, de preferência, o mesmo sistema operacional. A sincronização entre hardware e sistemas operacionais diferentes não é recomendada.

### Configuração do projeto {#setting-up}

Antes de usar o recurso de sincronização de comandos, verifique se você tem um projeto e um canal com conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **CommandSyncDemo** e um canal de sequência **ChannelLobby**.

   ![imagem1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criação e Gerenciamento de Canais](/help/user-guide/managing-channels.md)

   O canal inclui o conteúdo a seguir, como mostrado na figura abaixo.

   ![imagem1](assets/command-sync/command-sync2-1.png)

1. Crie um local **Lobby** e, em seguida, uma exibição denominada **LobbyDisplay** na pasta **Locations**, conforme mostrado na figura abaixo.
   ![imagem1](assets/command-sync/command-sync3-1.png)

1. Atribua o canal **ChannelLobby** à sua **LobbyDisplay**. Agora é possível exibir o canal atribuído à exibição no painel de exibição.
   ![imagem1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criação e Gerenciamento de Exibições](/help/user-guide/managing-displays.md).

1. Navegue até a pasta **Dispositivos**.
1. Clique em **Gerenciador de dispositivos** na barra de ações.

   ![imagem1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para saber como registrar um dispositivo, consulte [Registro de Dispositivo](/help/user-guide/device-registration.md)

1. Para fins de demonstração, este exemplo mostra um dispositivo Chrome e um Windows Player como dois dispositivos separados. Ambos os dispositivos apontam para a mesma tela.
   ![imagem1](assets/command-sync6.png)

### Atualização das configurações de canal

1. Navegue até **ChannelLobby**.
1. Clique em **Editar** na barra de ações.
1. Clique no canal inteiro como mostrado na figura abaixo.
   ![imagem1](assets/command-sync/command-sync7-1.png)

1. Clique na chave inglesa.
   ![imagem1](assets/command-sync/command-sync8-1.png)

1. Na caixa de diálogo **Página**, digite a palavra-chave *sincronizada* no campo **Estratégia**.
   ![imagem1](assets/command-sync/command-sync9-1.png)


### Configurar um principal {#setting-up-primary}

1. Navegue até o painel de exibição em **CommandSyncDemo** > **Locations** > **Lobby** > **LobbyDisplay**. Em seguida, clique em **Painel** na barra de ações.
Observe os dois dispositivos (Chrome e Windows Player) no painel **DISPOSITIVOS**, como mostrado a seguir:
   ![imagem1](assets/command-sync/command-sync10-1.png)

1. No painel **DISPOSITIVOS**, clique no dispositivo que você deseja definir como principal. O exemplo a seguir demonstra como configurar o dispositivo Chrome como o dispositivo principal. Clique em **Definir como dispositivo primário**.

   ![imagem1](assets/command-sync/command-sync11-1.png)

1. Insira o endereço IP em **Definir como dispositivo primário** e clique em **Salvar**.

   ![imagem1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Você pode configurar vários dispositivos como dispositivos primários.

### Sincronização com o Principal {#sync-up-primary}

1. Depois de definir o dispositivo Chrome como principal, sincronize o outro dispositivo (neste caso, o Windows Player) com o principal.
Clique no outro dispositivo (neste caso, Windows Player) no painel **DISPOSITIVOS** e clique em **Sincronizar com o dispositivo principal**.

   ![imagem1](assets/command-sync/command-sync13-1.png)

1. Clique no dispositivo na lista e clique em **Salvar**.

   >[OBSERVAÇÃO:]
   > A caixa de diálogo **Sincronizar com o dispositivo primário** mostra a lista de dispositivos primários. Selecione o preferido.

1. Quando o dispositivo (Windows Player) é sincronizado com o dispositivo principal (Chrome Player), você pode ver o dispositivo sincronizado no painel **DISPOSITIVOS**.

   ![imagem1](assets/command-sync/command-sync14-1.png)

### Dessincronização com o principal {#desync-up-primary}

Depois de sincronizar um dispositivo ou dispositivos com um dispositivo principal, você pode dessincronizar a atribuição desse dispositivo.

>[!NOTE]
>
>Se você cancelar a sincronização de um dispositivo principal, ele também desvinculará todos os dispositivos clientes associados a esse dispositivo principal.

Para remover a sincronização do dispositivo principal, siga as etapas abaixo:

1. Navegue até o painel **DISPOSITIVOS** e clique no dispositivo.

1. Clique em **Dessincronizar dispositivos** para dessincronizar o cliente do dispositivo principal.

   ![imagem1](assets/command-sync/command-sync15-1.png)

1. Clique em **Confirmar** para cancelar a sincronização do dispositivo selecionado no dispositivo principal.

   >[OBSERVAÇÃO:]
   > Se você clicar no dispositivo principal e usar a opção de dessincronização, todos os dispositivos conectados ao principal serão dessincronizados em uma etapa.
