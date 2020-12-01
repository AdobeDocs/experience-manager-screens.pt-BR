---
title: Canal de Assumir Perpétua
seo-title: Canal de Assumir Perpétua
description: Siga este caso de uso para criar um Canal de aquisição perpétuo.
seo-description: Siga este caso de uso ao configurar um projeto que cria um canal de Retorno Perpétuo que é reproduzido para um dia e hora específicos continuamente.
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---


# Canal de Retorno Perpétuo {#perpetual-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal TakeOver Perpetual que é reproduzido continuamente por um dia e hora específicos.

## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* do canal normalmente reproduzido para um monitor ou grupo de monitores. A aquisição ocorrerá por um dia e hora específicos, perpetuamente.
Por exemplo, há um canal Perpetual TakeOver que é reproduzido todas as sextas-feiras das 9h às 10h. Durante esse tempo, nenhum outro canal deveria jogar. O exemplo a seguir mostra a criação de um canal de aquisição perpétuo que é reproduzido permite que o conteúdo seja reproduzido toda quarta-feira por 2 horas, das 14:00 às 16:00.

### Pré-condições {#preconditions}

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

1. Crie um projeto AEM Screens chamado **PerpetualTakeOver**, como mostrado abaixo.

   ![ativo](assets/p_usecase1.png)

1. Crie um **MainAdChannel** na pasta **Canais**.

   ![ativo](assets/p_usecase2.png)

1. Selecione **MainAdChannel** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/p_usecase3.png)


   >[!NOTE]
   >O **MainAdChannel** neste exemplo demonstra um canal de sequência que reproduz o conteúdo continuamente.

1. Crie um canal **TakeOver** que assuma o conteúdo em **MainAdChannel** e será reproduzido todas as quartas-feiras das 14:00 às 16:00 horas.

1. Selecione **Assumir** e clique em **Editar** na barra de ações. Arraste e solte alguns ativos em seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/p_usecase4.png)

1. Configure um local e exiba seus canais. Por exemplo, o seguinte local **MainLobby** e a exibição **MainLobbyDisplay** estão configurados para este projeto.

   ![ativo](assets/p_usecase5.png)

**Atribuindo Canais a uma exibição**

1. Selecione a exibição **MainLobbyDisplay** da pasta **Locations**. Clique em **Atribuir Canal** na barra de ações para abrir a caixa de diálogo **Atribuição de Canais**.

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte **[Atribuição de Canal](channel-assignment.md)**.

1. Preencha os campos (**Caminho do Canal**, **Prioridade** e **Eventos suportados**) da caixa de diálogo **Atribuição do Canal** e clique em **Guardar** para atribuir o **CanalAnúncioPrincipal 11/> à sua tela.**

   * **Caminho** do canal: Selecione o caminho para  **** MainAdChannelchannel
   * **Prioridade**: Defina a prioridade desse canal como 1.
   * **Eventos** suportados: Selecione a tela  **Inicial** Loadand  **Idle**.

   ![ativo](assets/p_usecase6.png)

1. Selecione a exibição **TakeOver** da pasta **Locations**. Clique em **Atribuir Canal** na barra de ações para atribuir o canal de aquisição.

1. Para atribuir o canal **TakeOver** à exibição em um horário agendado e preencher os seguintes campos da caixa de diálogo **Atribuição de Canal** e clique em **Salvar**:

   * **Caminho** do canal: Selecione o caminho para o  **** TakeOverchannel
   * **Prioridade**: Defina a prioridade deste canal maior que o  **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
   * **Eventos** suportados: Selecione a  **Tela** inativa e o  **Temporizador**.
   * **Agendamento**: Insira o texto para o agendamento no qual você deseja que este canal execute a exibição. O texto em **Schedule** mencionado neste exemplo é *na quarta-feira depois das 14:00 e antes das 16:00*.

      >[!NOTE]
      >Para saber mais sobre as expressões que você pode adicionar à **Programação**, consulte a seção [Exemplo de Expressões](#example-expressions) abaixo.
   * **ativo** de: Data e hora do start.
   * **ativo até**: Data e hora de término.

      Por exemplo, o texto em **Schedule** e **ativo de** e **ativo até** data e hora permite que o conteúdo seja reproduzido todas as quartas-feiras, das 14:00 às 16:00 horas.


      ![ativo](assets/p_usecase7.png)

      Navegue até a exibição de **TakeOver** —> **Locations** —> **MainLobby** —> **MainLobbyDisplay** e clique em **Painel** da barra de ações para visualização dos canais atribuídos com suas prioridades, conforme mostrado abaixo.

      >[!NOTE]
      >É obrigatório definir a prioridade mais elevada do canal de aquisição.

      ![](assets/p_usecase8.png)
assetNow, o  **** TakeOverchannel assumirá o  **** MainAdChannelat 14:00 horas por duas horas até as 16:00 horas toda quarta-feira e reproduzirá seu conteúdo de Jan 09 de janeiro de 2020 a 31 de janeiro de 2020.

## Expressões de exemplo {#example-expressions}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o canal é reproduzido antes das 8:00 da manhã todos os dias |
| depois das 14:00 | o canal é reproduzido depois das 14:00 horas todos os dias |
| depois das 12:15 e antes das 12:45 | o canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 15:00 | os start do canal tocando depois das 14:00 horas de 1º de janeiro, continua jogando o dia inteiro em 2º de janeiro até as 15:00 da manhã de 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 15:00 | o jogador de start do canal depois das 14:00 horas de 1º de janeiro, continua reproduzindo até as 15:00 da manhã de 2º de janeiro, depois start novamente em 2º de janeiro às 14:00 e continua reproduzindo até as 15:00 da manhã de 3 de janeiro |

>[!NOTE]
>
>Você também pode usar a notação _militar_ (isto é, 14:00) em vez da notação *am/pm* (isto é, 14:00 horas).
