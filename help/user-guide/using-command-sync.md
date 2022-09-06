---
title: Usando a sincronização de comandos
seo-title: Using Command Sync
description: Siga esta página para saber mais sobre como usar a Sincronização de comandos.
seo-description: Follow this page to learn about how to use Command Sync.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
source-git-commit: 43ac19cf7ef63ec17611cf19ca357f791dca6e87
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 2%

---

# Sincronização de comandos {#command-sync}

A página a seguir descreve como usar a Sincronização de comandos. A Sincronização de comandos permite a reprodução sincronizada em diferentes reprodutores. Os players podem reproduzir conteúdo diferente, mas cada ativo precisa ter a mesma duração.

>[!IMPORTANT]
>
>Esse recurso não é compatível com Sequências incorporadas, Sequências incorporadas dinâmicas, Canais de aplicativo ou Transições.

## Visão geral {#overview}

As soluções de sinalização digital precisam suportar murais de vídeo e reprodução sincronizada para suportar cenários como contagem regressiva de Ano Novo ou vídeo grande fatiado para ser reproduzido em várias telas e é aqui que a Sincronização de Comando entra em ação.

Para usar a Sincronização de comandos, um reprodutor atua como um *principal* e envia o comando e todos os outros players atuam como *clientes* e reproduzir quando receberem o comando.

O *principal* envia um comando para todos os clientes registrados quando está prestes a iniciar a reprodução de um item. A carga disso pode ser o índice do item a ser reproduzido e/ou o html externo do elemento a ser reproduzido.

## Implementando sincronização de comandos {#using-command-sync}

A seção a seguir descreve como usar a Sincronização de comandos em um projeto do AEM Screens.

>[!NOTE]
>
>Para reprodução sincronizada, é necessário que todos os dispositivos de hardware tenham as mesmas especificações de hardware e, de preferência, o mesmo sistema operacional. Não é recomendável sincronizar entre diferentes hardware e sistemas operacionais.

### Configuração do projeto {#setting-up}

Antes de usar o recurso de Sincronização de comandos, verifique se você tem um projeto e um canal com o conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **CommandSyncDemo** e um canal de sequência **ChannelLobby**.

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criação e gerenciamento de canais](/help/user-guide/managing-channels.md)

   O canal contém o seguinte conteúdo, como mostrado na figura abaixo.

   ![image1](assets/command-sync/command-sync2-1.png)

1. Criar um local **Lobby** e, posteriormente, uma exibição com o título como **LobbyDisplay** no **Localizações** , conforme mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync3-1.png)

1. Atribuir o canal, **ChannelLobby** para **LobbyDisplay**. Agora é possível exibir o canal atribuído à exibição no painel de exibição.
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criação e gerenciamento de exibições](/help/user-guide/managing-displays.md).

1. Navegar para **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações para registrar os dispositivos.

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >Para saber como registrar um dispositivo, consulte [Registro do dispositivo](/help/user-guide/device-registration.md)

1. Para fins de demonstração, este exemplo mostra um dispositivo chrome e um windows player como dois dispositivos separados. Ambos os dispositivos apontam para a mesma tela.
   ![image1](assets/command-sync6.png)

### Atualização das configurações de canal

1. Navegar para **ChannelLobby** e clique em **Editar** na barra de ações para atualizar as configurações do canal.

1. Selecione o canal inteiro como mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync7-1.png)

1. Clique no ícone da chave de fenda para abrir o **Página** caixa de diálogo.
   ![image1](assets/command-sync/command-sync8-1.png)

1. Insira o *sincronizado* palavra-chave na **Estratégia** campo.

   ![image1](assets/command-sync/command-sync9-1.png)


### Configurar um {#setting-up-primary}

1. Navegue até o painel de exibição a partir de **CommandSyncDemo** —> **Localizações**  —> **Lobby** —> **LobbyDisplay** e clique em **Painel** na barra de ações.
Você verá os dois dispositivos (chrome e windows player) em **DISPOSITIVOS** , conforme mostrado na figura abaixo.
   ![image1](assets/command-sync/command-sync10-1.png)

1. No **DISPOSITIVOS** selecione o dispositivo que deseja definir como primário. O exemplo a seguir demonstra como configurar o dispositivo Chrome como o principal. Clique em **Definir como dispositivo principal**.

   ![image1](assets/command-sync/command-sync11-1.png)

1. Insira o endereço IP em **Definir como dispositivo principal** e clique em **Salvar**.

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>Você pode configurar vários dispositivos como primários.

### Sincronização com Primário {#sync-up-primary}

1. Depois de definir o dispositivo Chrome como primário, você pode sincronizar o outro dispositivo (neste caso, o windows player) para sincronizar com o primário.
Selecione o outro dispositivo (neste caso, o windows player) no **DISPOSITIVOS** e clique em **Sincronizar com o dispositivo principal**, conforme mostrado na figura abaixo.

   ![image1](assets/command-sync/command-sync13-1.png)

1. Selecione o dispositivo na lista e clique em **Salvar**.

   >[OBSERVAÇÃO:]
   > O **Sincronizar com o dispositivo principal** mostrará a lista de dispositivos primários. Você pode selecionar a preferência desejada.

1. Depois que o dispositivo (Windows player) é sincronizado com o primário (Chrome player), você verá o dispositivo sincronizado no **DISPOSITIVOS** painel.

   ![image1](assets/command-sync/command-sync14-1.png)

### Cancelamento de sincronização com o principal {#desync-up-primary}

Depois de sincronizar um dispositivo ou dispositivos a um principal, você pode cancelar a sincronização da atribuição desse dispositivo.

>[!NOTE]
>
>Se você cancelar a sincronização de um dispositivo principal, ele também desvinculará todos os dispositivos clientes associados a esse dispositivo principal.

Para remover a sincronização do dispositivo principal, siga as etapas abaixo:

1. Navegue até o **DISPOSITIVOS** e selecione o dispositivo.

1. Clique em **Dispositivo(s) de dessincronização** para cancelar a sincronização do cliente a partir do dispositivo principal.

   ![image1](assets/command-sync/command-sync15-1.png)

1. Clique em **Confirmar** para cancelar a sincronização do dispositivo selecionado no primário.

   >[OBSERVAÇÃO:]
   > Se você selecionar o dispositivo principal e usar a opção de dessincronização, todos os dispositivos conectados ao primário serão dessincronizados em uma etapa.
