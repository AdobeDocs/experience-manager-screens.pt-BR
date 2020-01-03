---
title: Canal de Assumição Perpétua
seo-title: Canal de Assumição Perpétua
description: Siga este caso de uso para criar um Canal de assumpção perpétua.
seo-description: Siga este caso de uso para criar o Canal de assumpção perpétua.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: d64eb2ca3efc4d15be119c9b8efd9ff2b8f8daf4

---


# Canal de Assumição Perpétua {#perpetual-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal de Tomada Perpétua que é reproduzido continuamente por um dia e hora específicos.

## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* o controle do canal de reprodução normal para um monitor ou grupo de monitores. A aquisição ocorrerá por um dia e hora específicos, perpetuamente.
Por exemplo, há um canal de TakeOver Perpetual que é reproduzido todas as sextas-feiras das 9h às 10h. Durante esse tempo, nenhum outro canal deve ser reproduzido. O exemplo a seguir mostra a criação de um canal de aquisição perpétuo que é reproduzido permite que o conteúdo seja reproduzido toda quarta-feira por 2 horas, das 17h às 19h.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de saber como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar programações](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

**Configuração dos canais e do monitor**

1. Crie um projeto do AEM Screens intitulado como **PerpetualTakeOver**, como mostrado abaixo.

   ![ativo](assets/single-takeover1.png)

1. Crie um **MainAdChannel** na pasta **Canais** .

   ![ativo](assets/single-takeover2.png)

1. Selecione **MainAdChannel** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/single-takeover2.png)


   >[!NOTE]
   >O **MainAdChannel** neste exemplo demonstra um canal de sequência que reproduz conteúdo continuamente.

   ![ativo](assets/single-takeover3.png)

1. Crie um canal **TakeOver** que assuma o conteúdo no **MainAdChannel** e será reproduzido somente por um dia e hora específicos.

1. Selecione a opção **Assumir** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos em seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a este canal.

   ![ativo](assets/single-takeover4.png)

1. Configure um local e exibição para seus canais. Por exemplo, a seguinte localização **Salão** e exibição **MainLobbyDisplay** está configurada para este projeto.

   ![ativo](assets/single-takeover5.png)

**Atribuindo canais a uma exibição**

1. Selecione a exibição **MainLobbyDisplay** na pasta **Locais** . Clique em **Atribuir canal** na barra de ações.

   ![ativo](assets/single-takeover6.png)

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte Atribuição **[de](channel-assignment.md)**canal.

1. Preencha os campos (Caminho **do** canal, **Prioridade** e Eventos **** suportados) da caixa de diálogo Atribuição **de** canal e clique em **Salvar**. Agora você atribuiu o **MainAdChannel** à sua exibição.

   ![ativo](assets/single-takeover7.png)

1. Selecione a exibição **Assumir** da pasta **Locais** . Clique em **Atribuir canal** na barra de ação para atribuir o canal de aquisição de uso único.

1. Para atribuir o canal **TakeOver** à exibição em um horário agendado, preencha os seguintes campos na caixa de diálogo Atribuição **de** canal e clique em **Salvar**:

   * **Caminho** do canal: Selecione o caminho para o canal TakeOver
   * **Prioridade**: Defina a prioridade deste canal maior que o **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
   * **Eventos** suportados: Selecione Tela **** inativa e **Temporizador**.
   * **Agendamento**: Insira o texto para o agendamento no qual você deseja que este canal execute a exibição. Por exemplo, o texto aqui permite que o conteúdo seja reproduzido 2 minutos antes das 12:00 da manhã de 31 de dezembro até as 12:01 da manhã.
O texto da **Agenda** mencionada neste exemplo é *no dia 31 de dezembro depois das 23:58 e também no dia 1 de janeiro antes das 00:01*.

      ![ativo](assets/single-takeover8.png)

      Navegue até a exibição de **SingleUseTakeOver** —> **Locations** —> **Lobby** —> **Main Lobby Display** e clique em **Dashboard** na barra de ações para exibir os canais atribuídos com suas prioridades, como mostrado abaixo.

      >[!NOTE]
      >É obrigatório definir a prioridade mais elevada do canal de aquisição.

      ![ativo](assets/single-takeover9.png)

