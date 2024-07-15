---
title: Canal de aquisição permanente
description: Saiba como criar um canal de Controle Permanente.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 1%

---

# Canal de aquisição permanente {#perpetual-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal TakeOver Permanente que é reproduzido continuamente por um dia e hora específicos.

## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume* do canal de reprodução normal para uma exibição ou grupo de exibições. A tomada de controle ocorre para um dia e hora específicos perpetuamente.
Por exemplo, há um canal de TakeOver Permanente que é reproduzido todas as sextas-feiras, das 9h às 10h. Durante esse tempo, nenhum outro canal deve ser reproduzido. O exemplo a seguir mostra a criação de um canal de aquisição permanente que permite que o conteúdo seja reproduzido todas as quartas-feiras por duas horas, das 14h às 16h.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e Gerenciar Canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e Gerenciar Agendamentos](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

**Configurando os Canais e a Exibição**

1. Crie um projeto do AEM Screens intitulado como **PerpetualTakeOver**, conforme mostrado abaixo.

   ![ativo](assets/p_usecase1.png)

1. Crie um **MainAdChannel** na pasta **Channels**.

   ![ativo](assets/p_usecase2.png)

1. Clique em **MainAdChannel** e em **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/p_usecase3.png)


   >[!NOTE]
   >O **MainAdChannel** deste exemplo demonstra um canal de sequência que reproduz o conteúdo continuamente.

1. Crie um canal **TakeOver** que controle o conteúdo no **MainAdChannel** e seja reproduzido toda quarta-feira das 14h às 16h.

1. Clique em **Assumir controle** e em **Editar** na barra de ações. Arraste e solte alguns ativos no seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/p_usecase4.png)

1. Configure um local e uma exibição para seus canais. Por exemplo, o seguinte local **MainLobby** e exibição **MainLobbyDisplay** estão configurados para este projeto.

   ![ativo](assets/p_usecase5.png)

**Atribuindo Canais a uma Exibição**

1. Clique na exibição **MainLobbyDisplay** da pasta **Locations**. Clique em **Atribuir canal** na barra de ações para que você possa abrir a caixa de diálogo **Atribuição de canal**.

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte **[Atribuição de canal](channel-assignment.md)**.

1. Preencha os campos (**Caminho do Canal**, **Prioridade** e **Eventos com Suporte**) da caixa de diálogo **Atribuição de Canal** e clique em **Salvar** para atribuir o **MainAdChannel** à sua exibição.

   * **Caminho do canal**: clique no caminho para o canal **MainAdChannel**
   * **Prioridade**: defina a prioridade deste canal como 1.
   * **Eventos com Suporte**: Clique em **Carregamento Inicial** e **Tela Inativa**.

   ![ativo](assets/p_usecase6.png)

1. Clique na exibição **TakeOver** da pasta **Locations**. Clique em **Atribuir canal** na barra de ações para poder atribuir o canal de tomada.

1. Atribuindo o canal **TakeOver** à exibição em um horário agendado. Em seguida, preencha os seguintes campos a partir da caixa de diálogo **Atribuição de canal** e selecione **Salvar**:

   * **Caminho do canal**: clique no caminho para o canal **TakeOver**
   * **Prioridade**: defina a prioridade deste canal como maior que **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
   * **Eventos com Suporte**: Clique em **Tela Inativa** e **Timer**.
   * **Agendar**: digite o texto do agendamento que você deseja que este canal execute na exibição. O texto na **Agenda** mencionada neste exemplo é *na quarta-feira depois das 14:00 e antes das 16:00*.

     >[!NOTE]
     >Para saber mais sobre as expressões que você pode adicionar ao **Cronograma**, consulte a seção [Expressões de Exemplo](#example-expressions) abaixo.
   * **ativo de**: data e hora de início.
   * **ativo até**: data e hora final.

     Por exemplo, o texto em **Agenda** e **ativa de** e **ativa até** data e hora aqui permite que o conteúdo seja reproduzido toda quarta-feira das 14h até às 16h.


     ![ativo](assets/p_usecase7.png)

     Navegue até a exibição em **TakeOver** > **Locations** > **MainLobby** > **MainLobbyDisplay**. Em seguida, clique em **Dashboard** na barra de ações para poder exibir os canais atribuídos com suas prioridades, conforme mostrado abaixo.

     >[!NOTE]
     >É obrigatório definir a prioridade do canal de aquisição como a mais alta.

     ![ativo](assets/p_usecase8.png)
Agora, o canal **TakeOver** assume o **MainAdChannel** às 14h, por duas horas até as 16h, todas as quartas-feiras, e reproduz o conteúdo de 9 de janeiro de 2020 a 31 de janeiro de 2020.

## Expressões de exemplo {#example-expressions}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8h | o canal é reproduzido diariamente antes das 8h |
| depois das 14h | o canal é reproduzido depois das 14h todos os dias |
| após 12:15 e antes de 12:45 | o canal é reproduzido diariamente após as 12h15 por 30 minutos |
| antes de 12:15 também depois de 12:45 | o canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45. |
| no primeiro dia de janeiro depois das 14h, também no segundo dia de janeiro e também no terceiro dia de janeiro antes das 3h. | o canal começa a tocar depois das 14h de 01 de janeiro, continua tocando o dia inteiro em 02 de janeiro até as 3h de 03 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o canal começa a ser reproduzido depois das 14h de 1 de janeiro, continua a ser reproduzido até às 3h de 2 de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3 de janeiro |

>[!NOTE]
>
>Você também pode usar a notação _tempo militar_ (14:00) em vez de *A.M./P.M.* (14:00).
