---
title: Canal de Tomada a cargo de Uso Único
seo-title: Canal de Tomada a cargo de Uso Único
description: Siga este caso de uso para criar um Canal de tomada de decisão de uso único.
seo-description: Siga este caso de uso para criar um Canal de tomada de decisão de uso único.
contentOwner: jsyal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---


# Canal de aquisição de uso único {#single-use-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal de Retorno Único que é reproduzido apenas uma vez por um tempo específico.


## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* do canal de reprodução normal para uma exibição ou grupo de exibições. A tomada a cargo só ocorrerá de uma vez por todas durante um período específico.
Por exemplo, há um canal de Tomada única que é reproduzido na sexta-feira das 9h às 10h. Durante esse tempo, nenhum outro canal deve ser reproduzido. Antes e depois deste tempo, o canal de OPA de Uso Único não será reproduzido. O exemplo a seguir mostra a criação de um único canal de aquisição que é reproduzido e permite que o conteúdo seja reproduzido por 2 minutos antes das 12:00 da manhã do dia 31 de dezembro até as 12:01 da manhã.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, certifique-se de entender como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar agendamentos](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores Primários {#primary-actors}

Autores de conteúdo

## Configurando o projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

**Configuração dos canais e exibição**

1. Crie um Projeto do AEM Screens chamado de **SingleUseTakeOver**, conforme mostrado abaixo.

   ![ativo](assets/single-takeover1.png)

1. Crie um **MainAdChannel** na pasta **Channels**.

   ![ativo](assets/single-takeover2.png)

1. Selecione o **MainAdChannel** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/single-takeover2.png)


   >[!NOTE]
   >O **MainAdChannel** neste exemplo demonstra um canal de sequência que reproduz conteúdo continuamente.

   ![ativo](assets/single-takeover3.png)

1. Crie um canal **TakeOver** que assume o conteúdo em **MainAdChannel** e será reproduzido somente por um dia e hora específicos.

1. Selecione o **TakeOver** e clique em **Edit** na barra de ações. Arraste e solte alguns ativos no seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/single-takeover4.png)

1. Configure um local e uma exibição para seus canais. Por exemplo, a seguinte localização **Lobby** e exibição **MainLobbyDisplay** são configuradas para este projeto.

   ![ativo](assets/single-takeover5.png)

**Atribuição de canais a uma exibição**

1. Selecione a exibição **MainLobbyDisplay** da pasta **Localizações**. Clique em **Atribuir canal** na barra de ações.

   ![ativo](assets/single-takeover6.png)

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte **[Atribuição de canal](channel-assignment.md)**.

1. Preencha os campos (**Caminho do Canal**, **Prioridade** e **Eventos Suportados**) da caixa de diálogo **Atribuição de Canal** e clique em **Salvar**. Agora você atribuiu o **MainAdChannel** à sua exibição.

   ![ativo](assets/single-takeover7.png)

1. Selecione a exibição **TakeOver** da pasta **Locations**. Clique em **Atribuir canal** na barra de ações para atribuir o canal de aquisição de uso único.

1. Para atribuir o canal **TakeOver** à exibição em um horário agendado e preencher os seguintes campos na caixa de diálogo **Atribuição de canal** e clique em **Salvar**:

   * **Caminho** do canal: Selecione o caminho para o canal TakeOver
   * **Prioridade**: Defina a prioridade deste canal maior que o  **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.

      >[!NOTE]
      >Prioridade pode ser qualquer valor maior que o valor de prioridade do canal que está sendo reproduzido normalmente.
   * **Eventos** compatíveis: Selecione a  **Tela inativa** e o  **Temporizador**.
   * **Programação**: Insira o texto para o agendamento no qual você deseja que este canal execute a exibição. Por exemplo, o texto aqui permite que o conteúdo seja reproduzido 2 minutos antes das 12:00 em 31 de dezembro até 12:01.
O texto no **Schedule** mencionado neste exemplo é *no dia 31 de dezembro depois de 23:58 e também no dia 1 de janeiro antes de 00.01*.

      ![ativo](assets/single-takeover8.png)

      Navegue até a exibição de **SingleUseTakeOver** —> **Locations** —> **Lobby** —> **MainLobbyDisplay** e clique em **Painel** na barra de ações para exibir os canais atribuídos com suas prioridades, conforme mostrado abaixo.

      >[!NOTE]
      >É obrigatório definir a prioridade do canal de aquisição como a mais alta.

      ![ativo](assets/single-takeover9.png)

>[!NOTE]
>
>É uma prática recomendada excluir o canal de Retorno de Uso Único, uma vez reproduzido.