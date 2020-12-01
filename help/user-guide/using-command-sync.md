---
title: Usando sincronização de comandos
seo-title: Usando sincronização de comandos
description: Siga esta página para saber mais sobre como usar a Sincronização de comandos.
seo-description: Siga esta página para saber mais sobre como usar a Sincronização de comandos.
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 2%

---


# Sincronização de comandos {#command-sync}

A página a seguir descreve como usar a Sincronização de comandos. A Sincronização de comandos permite a reprodução sincronizada em diferentes players. Os players podem reproduzir conteúdo diferente, mas cada ativo precisa ter a mesma duração.

>[!IMPORTANT]
>
>Esse recurso não oferece suporte para Sequências incorporadas, Sequências incorporadas dinâmicas, Canais de aplicativos ou Transições.

## Visão geral {#overview}

As soluções de sinalização digital precisam suportar paredes de vídeo e reprodução sincronizada para suportar cenários como contagens de Ano Novo ou vídeos grandes fatiados para serem reproduzidos em várias telas e é aqui que a Sincronização de Comando entra em ação.

Para usar a Sincronização de comandos, um player atua como *principal* e envia o comando e todos os outros players atuam como *clientes* e são reproduzidos quando recebem o comando.

O *principal* envia um comando para todos os clientes registrados quando está prestes a start da reprodução de um item. A carga desse elemento pode ser o índice do item a ser reproduzido e/ou o html externo do elemento a ser reproduzido.

## Implementação da sincronização de comandos {#using-command-sync}

A seção a seguir descreve como você pode usar a Sincronização de comandos em um projeto do AEM Screens.

>[!NOTE]
>
>Para a reprodução sincronizada, é necessário que todos os dispositivos de hardware tenham as mesmas especificações de hardware e, de preferência, o mesmo sistema operacional. Não é recomendado sincronizar entre hardware e sistemas operacionais diferentes.

### Configuração do projeto {#setting-up}

Antes de usar o recurso de Sincronização de comandos, verifique se você tem um projeto e um canal com o conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **CommandSyncDemo** e um canal de sequência **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criar e gerenciar Canais](/help/user-guide/managing-channels.md)

   O canal contém o seguinte conteúdo, como mostrado na figura abaixo.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Crie uma exibição na pasta **Locations**, conforme mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Atribua o canal, **ChannelLobby** ao seu **LobbyDisplay**.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criar e gerenciar exibições](/help/user-guide/managing-displays.md).

1. Navegue até a pasta **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações para registrar os dispositivos.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criação e gerenciamento de vídeos](/help/user-guide/managing-displays.md)

1. Para fins de demonstração, este exemplo mostra um dispositivo de cromo e um Windows player como dois dispositivos separados. Ambos os dispositivos apontam para a mesma tela.
   ![image1](assets/command-sync6.png)

### Atualização das configurações do Canal

1. Navegue até **ChannelLobby** e clique em **Editar** na barra de ações para atualizar as configurações do canal.

1. Selecione o canal inteiro como mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Clique no ícone de chave para abrir a caixa de diálogo **Página**.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Digite a palavra-chave *sincronizada* no campo **Estratégia**.

   ![image1](assets/command-sync/command-sync9-1.png)


### Configuração de um {#setting-up-master} principal

1. Navegue até o painel de exibição de **CommandSyncDemo** —> **Locations** —> **Lobby** —> **LobbyDisplay** e clique em **Painel** na barra de ação.
Você verá os dois dispositivos (chrome e windows player) no painel **DISPOSITIVOS**, conforme mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync10-1.png)

1. No painel **DISPOSITIVOS**, selecione o dispositivo que deseja definir como principal. O exemplo a seguir demonstra como configurar o dispositivo Chrome como o principal. Clique em **Definir como dispositivo principal**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Digite o endereço IP em **Definir como dispositivo principal** e clique em **Salvar**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Você pode configurar vários dispositivos como principais.

### Sincronização com {#sync-up-master} Principal

1. Depois de definir o dispositivo Chrome como principal, você pode sincronizar o outro dispositivo (neste caso, o Windows player) para sincronizar com o principal.
Selecione o outro dispositivo (neste caso, o Windows player) no painel **DISPOSITIVOS** e clique em **Sincronizar com o dispositivo principal**, conforme mostrado na figura abaixo.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Selecione o dispositivo na lista e clique em **Salvar**.

   >[OBSERVAÇÃO:]
   > A caixa de diálogo **Sincronizar com dispositivo principal** mostrará a lista de dispositivos principais. Você pode selecionar a preferência desejada.

1. Depois que o dispositivo (Windows player) for sincronizado com o principal (Chrome player), você verá o dispositivo sincronizado no painel **DISPOSITIVOS**.

   ![image1](assets/command-sync/command-sync14-1.png)

### Cancelamento de sincronização com o {#desync-up-master} Principal

Depois de sincronizar um dispositivo ou dispositivos com um principal, você pode dessincronizar a atribuição desse dispositivo.

>[!NOTE]
>
>Se você dessincronizar um dispositivo principal, ele também desvinculará todos os dispositivos cliente associados a esse dispositivo principal.

Para remover a sincronização do dispositivo principal, siga as etapas abaixo:

1. Navegue até o painel **DISPOSITIVOS** e selecione o dispositivo.

1. Clique em **Dessincronizar dispositivos** para dessincronizar o cliente do dispositivo principal.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Clique em **Confirmar** para dessincronizar o dispositivo selecionado do principal.

   >[OBSERVAÇÃO:]
   > Se você selecionar o dispositivo principal e usar a opção de dessincronização, todos os dispositivos conectados ao principal serão dessincronizados em uma etapa.
