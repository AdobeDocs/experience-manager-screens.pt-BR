---
title: Canal Take-Over de Uso Único
seo-title: Canal Take-Over de Uso Único
description: Siga este caso de uso para criar um Canal de uso único Take-Over.
seo-description: Siga este caso de uso para criar um Canal de uso único Take-Over.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---


# Canal Take-Over de Uso Único {#single-use-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal de tomada única que é reproduzido apenas uma vez por um período específico.


## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* o controle do canal normalmente reproduzido para um monitor ou grupo de monitores. A tomada a cargo só ocorrerá de uma vez por outra.
Por exemplo, há um canal de tomada única que é reproduzido na sexta-feira das 9h às 10h. Durante esse tempo, nenhum outro canal deveria jogar. Antes e depois desse tempo, o canal de Uso Único não será reproduzido. O exemplo a seguir mostra a criação de um único canal de aquisição que é reproduzido e permite que o conteúdo seja reproduzido por 2 minutos antes das 12:00 da manhã de 31 de dezembro até as 12:01 da manhã.

### Condições prévias {#preconditions}

Antes de start deste caso de uso, certifique-se de saber como:

* **[Criar e gerenciar Canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar programações](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

**Configurar os Canais e o monitor**

1. Crie um projeto de AEM Screens chamado **SingleUseTakeOver**, como mostrado abaixo.

   ![ativo](assets/single-takeover1.png)

1. Crie um **MainAdChannel** na pasta **Canais** .

   ![ativo](assets/single-takeover2.png)

1. Selecione o **MainAdChannel** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/single-takeover2.png)


   >[!NOTE]
   >O **MainAdChannel** neste exemplo demonstra um canal de sequência que reproduz o conteúdo continuamente.

   ![ativo](assets/single-takeover3.png)

1. Crie um **canal TakeOver** que assuma o conteúdo no **MainAdChannel** e será reproduzido somente por um dia e hora específicos.

1. Selecione a opção **Assumir** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos em seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/single-takeover4.png)

1. Configure um local e exiba seus canais. Por exemplo, a seguinte localização **Salão** e exibição **MainLobbyDisplay** está configurada para este projeto.

   ![ativo](assets/single-takeover5.png)

**Atribuindo Canais a uma exibição**

1. Selecione a exibição **MainLobbyDisplay** na pasta **Locais** . Clique em **Atribuir Canal** na barra de ações.

   ![ativo](assets/single-takeover6.png)

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte Atribuição de **[Canais](channel-assignment.md)**.

1. Preencha os campos (Caminho **do** Canal, **Prioridade** e Eventos **** suportados) da caixa de diálogo Atribuição **do** Canal e clique em **Salvar**. Agora você atribuiu o **MainAdChannel** à sua exibição.

   ![ativo](assets/single-takeover7.png)

1. Selecione a exibição **Assumir** da pasta **Locais** . Clique em **Atribuir Canal** na barra de ação para atribuir o canal de aquisição de uso único.

1. Para atribuir o canal **TakeOver** à exibição em um horário agendado, preencha os seguintes campos na caixa de diálogo Atribuição **de** Canal e clique em **Salvar**:

   * **Caminho** do Canal: Selecione o caminho para o canal TakeOver
   * **Prioridade**: Defina a prioridade deste canal maior que o **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
      >[!NOTE]
      >[!NOTE]

   * **Prioridade pode ser qualquer valor maior que o valor de prioridade do canal que está sendo reproduzido normalmente.**********
   * **Eventos** suportados: Selecione Tela **** inativa e **Temporizador**.

      **Agendamento**: Insira o texto para o agendamento no qual você deseja que este canal execute a exibição. Por exemplo, o texto aqui permite que o conteúdo seja reproduzido 2 minutos antes das 12:00 da manhã de 31 de dezembro até as 12:01 da manhã.
O texto da **Agenda** mencionada neste exemplo é *no dia 31 de dezembro depois das 23:58 e também no dia 1 de janeiro antes das 00:01*.

      ![ativo](assets/single-takeover8.png)****************

      >Navegue até a exibição de **SingleUseTakeOver** —> **Locations** —> **Lobby** —> **MainLobbyDisplay** e clique no **Painel** da barra de ação para visualização dos canais atribuídos com suas prioridades, como mostrado abaixo.      >[!NOTE]


      ![É obrigatório definir a prioridade mais elevada do canal de aquisição.](assets/single-takeover9.png)

>[!NOTE]
>
>![ativo](assets/single-takeover9.png)
