---
title: Criação e gerenciamento de canais
seo-title: Gerenciamento de canais
description: Siga esta página para saber como criar e gerenciar canais. Ela também explica as funções do painel Canal e como editar o conteúdo de um canal.
seo-description: Siga esta página para saber como criar e gerenciar canais. Ela também explica as funções do painel Canal e como editar o conteúdo de um canal.
uuid: cdf09ced-9089-4249-ba51-471d6fa0e507
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a8006686-8ee5-4971-ab79-0c7b01f108f2
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Criação e gerenciamento de canais {#creating-and-managing-channels}

Um Canal exibe uma sequência de conteúdo e imagens e vídeos de exibição, mas também pode exibir um site ou um aplicativo de página única.

Esta página mostra o processo de criar e gerenciar canais para o Screens.

**Pré-requisitos**:

* [Configuração e implantação do Screens](configuring-screens-introduction.md)
* [Criar e gerenciar projetos de telas](creating-a-screens-project.md)

## Criação de um novo canal {#creating-a-new-channel}

Depois de criar seu projeto para o Screens, siga as etapas abaixo para criar um novo Canal para um projeto do Screens:

1. Selecione o link do Adobe Experience Manager (canto superior esquerdo) e, em seguida, o Screens. Alternatively, you can ﻿go directly to: `https://localhost:4502/screens.html/content/screens`.
1. Navegue até o projeto do Screens e clique em **Canais**.
1. Click **Create** next to the plus icon in the action bar. Um assistente será aberto (*consulte Tipos de canais para obter mais informações*).

1. Select the template from the wizard and click **Next**.
1. Enter the properties for **Title and Tags**, **More Titles and Description**, **On/Off Time**, and **Vanity URL**.

1. Clique em **Criar**. O canal é criado e adicionado à sua pasta de canais.

### Tipos de canais {#channel-types}

As seguintes opções de modelo estão disponíveis ao usar o assistente, entre elas:

| **Opção de modelo** | **Descrição** |
|---|---|
| Pasta de canais | Permite criar uma pasta para armazenar uma coleção de canais. |
| Canal de sequência | Permite criar um canal que reproduz os componentes sequencialmente (um por um em uma apresentação de slides). |
| Canal do aplicativo | Permite mostrar seu aplicativo web personalizado no player do Screens. |
| Canal de tela dividida 1x1 | Permite exibir o componente em uma única zona. |
| Canal de tela dividida 1x2 | Permite exibir os ativos em duas zonas (divididas horizontalmente). |
| Canal de tela dividida 2X1 | Permite exibir os ativos em duas zonas (divididas verticalmente). |
| Canal de tela dividida 2x2 | Permite exibir os ativos em quatro zonas (divididas horizontal e verticalmente em uma matriz). |
| Canal de 2 a 3 telas divididas | Permite exibir os ativos em duas zonas (divididas horizontalmente) com uma das zonas maior que a outra. |
| Canal de tela dividida da barra L esquerda ou direita | Permite que os autores de conteúdo visualizem tipos diferentes de ativos em zonas de tamanho apropriado. |

>[!NOTE]
>
>Os canais de tela dividida dividem a exibição em várias zonas para que você possa reproduzir várias experiências ao mesmo tempo, lado a lado. As experiências podem ser ativos/texto estáticos ou sequências incorporadas.

The following example shows the creation of a Sequence Channel (C *hannelOne*) for a Screens project (*DemoProject*).

![demochannel](assets/demochannel.gif)

>[!NOTE]
>
>Você pode criar diferentes zonas usando opções de modelo, como os canais de tela dividida 1x2 e 2x2 ou o canal de 2 a 3 telas divididas mencionados acima.

***Importante***:

Depois de criar e adicionar conteúdo ao seu canal, o próximo passo é criar uma localização seguida pela criação de uma exibição. Além disso, você precisa atribuir esse canal a uma exibição. Consulte os recursos abaixo no final da seção para saber mais.

## Trabalhar com canais {#working-with-channels}

Você pode editar, exibir propriedades e o painel, copiar, visualizar e excluir um canal.

>[!NOTE]
>
>Clique no ícone à esquerda para selecionar um item. Por exemplo, clique no ícone do canal e realize as seguintes ações, conforme mostrado na figura abaixo.

![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Adição/edição de conteúdo em um canal {#adding-editing-content-to-a-channel}

Para adicionar ou editar conteúdo em um canal, siga as etapas abaixo:

1. Clique no Canal que deseja editar (conforme mostrado na figura acima).
1. Click **Edit** from the top left corner of the action bar to edit the channel properties. O editor é aberto e permite adicionar ativos/componentes ao canal que você deseja publicar.

>[!NOTE]
>
>Você pode adicionar componentes ao seu canal. Consulte **[Adicionar componentes a um canal](adding-components-to-a-channel.md)** para obter mais detalhes.

![demochannel1](assets/demochannel1.gif)

**Carregando vídeos no canal** Siga as etapas abaixo para fazer upload de vídeos para seu canal:

1. Selecione o canal onde você deseja fazer upload do vídeo.
1. Clique em **Editar** na barra de ações para abrir o editor.
1. Selecione **Vídeos** em Ativos e arraste e solte os vídeos necessários.

>[!NOTE]
>
>If you encounter issues uploading videos in your channel, see [Troubleshooting Videos](troubleshoot-videos.md).

### Exibição de propriedades {#viewing-properties}

Para exibir ou editar as propriedades de um canal, siga as etapas abaixo:

1. Clique no Canal que deseja editar.
1. Click **Properties** from the action bar to view/edit the channel properties. As guias a seguir permitem que você altere as opções.

![propriedades](assets/properties.gif)

### Visualização do painel {#viewing-dashboard}

Para visualizar o painel de um canal, siga as etapas abaixo:

1. Clique no Canal que deseja editar.
1. Click **Dashboard** from the action bar to view the dashobard. The **CHANNEL INFORMATION**,**ASSIGNED DISPLAYS**, and **PENDING LAUNCHES** panel opens, as shown in the figure below:

![painel](assets/dashboard.gif)

### Informações do canal {#channel-information}

O painel Informações do canal descreve as propriedades do canal, juntamente com a visualização do canal. Além disso, informa se o canal está offline ou online.

Clique nas reticências (**...**) na barra de ações **Informações do canal** para exibir propriedades, editar o conteúdo ou atualizar o cache (conteúdo offline) do canal.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

### Canais online e offline {#online-and-offline-channels}

>[!NOTE]
>
>Por padrão, quando você cria um canal, ele fica offline.

Quando você cria um canal, ele pode ser definido como online ou offline.

An ***Online Channel***, will show the updated content in the real time environment whereas an ***Offline Channel***, shows the cached content.

Siga as etapas abaixo para tornar o canal online:

1. Navegue até o canal como **TestProject** --&gt; **Canais** --&gt; **TestChannel**.

   Selecione o canal.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Click **Dashboard** from the action bar to view the status of the player. O painel **INFORMAÇÕES DO CANAL **fornece informações sobre se o canal está online ou offline.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Clique em **Propriedades** na barra de ações e navegue até a guia **Canal**, conforme mostrado abaixo:

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Verifique o **modo Desenvolvedor** (force o canal a ficar on-line) **** para tornar o canal on-line.

   Clique em **Salvar e fechar** para salvar sua opção.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Navigate back to the channel dashboard and now the **CHANNEL INFORMATION** panel shows the online status of the player.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>
>Se você quiser configurar seu canal novamente como offline, desmarque a opção de modo Desenvolvedor na guia **Propriedades** (como mostrado na etapa 3) e, no painel INFORMAÇÕES **** DO CANAL, clique em **Atualizar conteúdo** offline, como mostrado na figura abaixo.

![dashboard2](assets/dashboard2.gif)

#### Atualizações automáticas versus atualizações manuais no painel Dispositivos {#automatic-versus-manual-updates-from-the-device-dashboard}

A tabela a seguir resume os eventos associados às atualizações automáticas e manuais do painel Dispositivos.

<table>
 <tbody>
  <tr>
   <td><strong>Evento</strong></td>
   <td><strong>Atualização automática do dispositivo</strong></td>
   <td><strong>Atualização manual do dispositivo</strong></td>
  </tr>
  <tr>
   <td>Mudança no canal online</td>
   <td>Conteúdo atualizado automaticamente</td>
   <td><p>Conteúdo atualizado em "Dispositivo: Push Config"</p> <p>Ou,</p> <p>Conteúdo atualizado no <strong><i>dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
  <tr>
   <td>Alteração no canal offline, mas o canal "Conteúdo de push" NÃO é acionado (nenhuma recriação de pacote offline)</td>
   <td>Nenhuma atualização de conteúdo</td>
   <td>Nenhuma atualização de conteúdo</td>
  </tr>
  <tr>
   <td>A alteração no Canal offline e no Canal "Conteúdo de push" é acionada (novo pacote offline)</td>
   <td>Conteúdo atualizado automaticamente</td>
   <td><p>Conteúdo atualizado no <strong><i>dispositivo: Configuração de push</i></strong></p> <p>Ou,</p> <p>Conteúdo atualizado no <strong><i>dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Alteração na configuração</p>
    <ul>
     <li>Exibir (canal forçado)</li>
     <li>Device</li>
     <li>Atribuições de canal (novo canal, canal removido)</li>
     <li>Atribuição de canal (função, evento, agendamento)</li>
    </ul> </td>
   <td>Configuração atualizada automaticamente</td>
   <td><p>Configuração atualizada no <strong><i>dispositivo: Configuração de push</i></strong></p> <p>Ou,</p> <p>Configuração atualizada no <strong><i>dispositivo: Reiniciar</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Exibições atribuídas {#assigned-displays}

O painel Exibições atribuídas mostra a exibição associada ao canal. Ele fornece um instantâneo da exibição atribuída junto com a resolução.

As exibições associadas serão listadas no painel **Exibições atribuídas**, conforme mostrado abaixo:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>
>Para saber mais sobre como criar uma exibição em um local, consulte:
>
>* [Criar e gerenciar locais](managing-locations.md)
>* [Criar e gerenciar exibições](managing-displays.md)
>



Além disso, clique na exibição do painel **EXIBIÇÕES ATRIBUÍDAS** para visualizar as informações de exibição, conforme mostrado abaixo:

![chlimage_1-28](assets/chlimage_1-28.png)

### Próximas etapas {#the-next-steps}

O próximo passo depois de criar um canal e adicionar/editar conteúdo nele é aprender a criar uma localização e uma exibição. Além disso, atribua um canal a essa exibição.

Veja os seguintes recursos para conhecer as próximas etapas:

* [Criar e gerenciar canais](managing-channels.md)
* [Criar e gerenciar locais](managing-locations.md)
* [Criar e gerenciar exibições](managing-displays.md)
