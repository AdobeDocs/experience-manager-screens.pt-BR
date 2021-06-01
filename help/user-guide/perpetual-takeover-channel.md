---
title: Canal de Assumição Perpétua
seo-title: Canal de Assumição Perpétua
description: Siga este caso de uso para criar um Canal Tomada de Controle Perpétuo.
seo-description: Siga este caso de uso ao configurar um projeto que crie um canal de Retorno Perpétuo que será reproduzido por um dia e hora específicos continuamente.
contentOwner: jsyal
feature: Telas de criação
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---


# Canal de Tomada de Controle Perpétuo {#perpetual-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal de Retorno Perpétuo que é reproduzido continuamente por um dia e hora específicos.

## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* do canal de reprodução normal para uma exibição ou grupo de exibições. A tomada a cargo ocorrerá por um dia e hora específicos, perpetuamente.
Por exemplo, há um canal Tomada de conta permanente que é reproduzido todas as sextas-feiras de 9h às 10h. Durante esse tempo, nenhum outro canal deve ser reproduzido. O exemplo a seguir mostra a criação de um canal de aquisição perpétuo que é reproduzido e permite que o conteúdo seja reproduzido todas as quartas-feiras por 2 horas, das 14h às 16h.

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

1. Crie um Projeto do AEM Screens chamado de **PerpetualTakeOver**, conforme mostrado abaixo.

   ![ativo](assets/p_usecase1.png)

1. Crie um **MainAdChannel** na pasta **Channels**.

   ![ativo](assets/p_usecase2.png)

1. Selecione o **MainAdChannel** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/p_usecase3.png)


   >[!NOTE]
   >O **MainAdChannel** neste exemplo demonstra um canal de sequência que reproduz conteúdo continuamente.

1. Crie um canal **TakeOver** que assume o conteúdo em **MainAdChannel** e será reproduzido todas as quartas-feiras de 2:00 às 16:00.

1. Selecione o **TakeOver** e clique em **Edit** na barra de ações. Arraste e solte alguns ativos no seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/p_usecase4.png)

1. Configure um local e uma exibição para seus canais. Por exemplo, a seguinte localização **MainLobby** e exibição **MainLobbyDisplay** são configuradas para este projeto.

   ![ativo](assets/p_usecase5.png)

**Atribuição de canais a uma exibição**

1. Selecione a exibição **MainLobbyDisplay** da pasta **Localizações**. Clique em **Atribuir canal** na barra de ações para abrir a caixa de diálogo **Atribuição de canal**.

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte **[Atribuição de canal](channel-assignment.md)**.

1. Preencha os campos (**Caminho do Canal**, **Prioridade** e **Eventos Suportados**) da caixa de diálogo **Atribuição de Canal** e clique em **Salvar** para atribuir o **CanalPrincipalAd 1/> para sua tela.**

   * **Caminho** do canal: Selecione o caminho para o canal  **** MainAdChannelchannel
   * **Prioridade**: Defina a prioridade desse canal como 1.
   * **Eventos** compatíveis: Selecione o  **Initial** Loadand  **Idle Screen**.

   ![ativo](assets/p_usecase6.png)

1. Selecione a exibição **TakeOver** da pasta **Locations**. Clique em **Atribuir canal** na barra de ações para atribuir o canal de aquisição.

1. Para atribuir o canal **TakeOver** à exibição em um horário agendado e preencher os seguintes campos na caixa de diálogo **Atribuição de canal** e clique em **Salvar**:

   * **Caminho** do canal: Selecione o caminho para o  **** TakeOverchannel
   * **Prioridade**: Defina a prioridade deste canal maior que o  **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
   * **Eventos** compatíveis: Selecione a  **Tela inativa** e o  **Temporizador**.
   * **Programação**: Insira o texto para o agendamento no qual você deseja que este canal execute a exibição. O texto no **Schedule** mencionado neste exemplo é *na quarta-feira depois das 14:00 e antes das 16:00*.

      >[!NOTE]
      >Para saber mais sobre as expressões que podem ser adicionadas a **Schedule**, consulte a seção [Example Expressions](#example-expressions) abaixo.
   * **ativo de**: Data e hora de início.
   * **ativo até**: Data e hora de término.

      Por exemplo, o texto em **Schedule** e **ative from** e **ative até** data e hora aqui permite que o conteúdo seja reproduzido todas as quartas-feiras, das 14 horas às 16 horas.


      ![ativo](assets/p_usecase7.png)

      Navegue até a exibição de **TakeOver** —> **Locations** —> **MainLobby** —> **MainLobbyDisplay** e clique em **Dashboard** na barra de ações para exibir os canais atribuídos com suas prioridades, conforme mostrado abaixo.

      >[!NOTE]
      >É obrigatório definir a prioridade do canal de aquisição como a mais alta.

      ![](assets/p_usecase8.png)
assetNow, o  **** TakeOverchannel assumirá o  **** MainAdChannelat 14h por duas horas até às 16h todas as quartas-feiras e reproduzirá seu conteúdo de 09 de janeiro de 2020 a 31 de janeiro de 2020.

## Exemplo de expressões {#example-expressions}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o canal é reproduzido antes das 8:00 AM todos os dias |
| depois das 14:00 | o canal é reproduzido depois das 14h todos os dias |
| depois das 12:15 e antes das 12:45 | o canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 3:00 | o canal começa a reproduzir depois das 2:00 PM no dia 1º de janeiro, continua reproduzindo o dia inteiro no dia 2 de janeiro até as 3:00 AM no dia 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 3:00 | o canal inicia o player depois das 14:00 PM no dia 1º de janeiro, continua reproduzindo até as 3:00 AM no dia 2 de janeiro, depois começa novamente no dia 2 de janeiro às 14:00 e continua reproduzindo até as 3:00 AM no dia 3 de janeiro |

>[!NOTE]
>
>Você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).
