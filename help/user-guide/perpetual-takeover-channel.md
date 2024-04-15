---
title: Canal de aquisição permanente
description: Siga este caso de uso para criar um canal de aquisição permanente.
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 5d112f33-a7cf-415e-9ea7-dc18a0356a8d
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 1%

---

# Canal de aquisição permanente {#perpetual-takeover-channel}

A página a seguir mostra um caso de uso que enfatiza a configuração de um projeto sobre como criar um canal TakeOver Permanente que é reproduzido continuamente por um dia e hora específicos.

## Descrição do caso de uso {#use-case-description}

Este caso de uso explica como criar um canal que *assume o controle* do canal de reprodução normal para uma exibição ou grupo de exibições. A tomada de controle ocorre para um dia e hora específicos perpetuamente.
Por exemplo, há um canal de TakeOver Permanente que é reproduzido todas as sextas-feiras, das 9h às 10h. Durante esse tempo, nenhum outro canal deve ser reproduzido. O exemplo a seguir mostra a criação de um canal de aquisição permanente que é reproduzido, permitindo que o conteúdo seja reproduzido todas as quartas-feiras por duas horas, das 14h às 16h.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e gerenciar cronogramas](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

**Configuração de canais e exibição**

1. Crie um projeto do AEM Screens intitulado como **AssunçãoPerpétua**, conforme mostrado abaixo.

   ![ativo](assets/p_usecase1.png)

1. Criar um **MainAdChannel** no **Canais** pasta.

   ![ativo](assets/p_usecase2.png)

1. Selecione o **MainAdChannel** e selecione **Editar** na barra de ações. Arraste e solte alguns ativos (imagens, vídeos, sequências incorporadas) no seu canal.

   ![ativo](assets/p_usecase3.png)


   >[!NOTE]
   >A variável **MainAdChannel** neste exemplo, demonstra um canal de sequência que reproduz conteúdo continuamente.

1. Criar um **AssumirControle** canal que assume o conteúdo no **MainAdChannel** e é executada toda quarta-feira, das 14h às 16h.

1. Selecione o **AssumirControle** e selecione **Editar** na barra de ações. Arraste e solte alguns ativos no seu canal. O exemplo a seguir mostra uma única imagem de zona adicionada a esse canal.

   ![ativo](assets/p_usecase4.png)

1. Configure um local e uma exibição para seus canais. Por exemplo, o seguinte local **LobbyPrincipal** e exibição **MainLobbyDisplay** estão configurados para este projeto.

   ![ativo](assets/p_usecase5.png)

**Atribuição de Canais a uma Exibição**

1. Selecionar a exibição **MainLobbyDisplay** do **Localizações** pasta. Selecionar **Atribuir canal** na barra de ações, para que você possa abrir a variável **Atribuição de canal** caixa de diálogo.

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte **[Atribuição de canal](channel-assignment.md)**.

1. Preencha os campos (**Caminho do canal**, **Prioridade**, e **Eventos suportados**) do **Atribuição de canal** e selecione **Salvar** para atribuir o **MainAdChannel** para sua exibição.

   * **Caminho do canal**: selecione o caminho para o **MainAdChannel** channel
   * **Prioridade**: Defina a prioridade deste canal como 1.
   * **Eventos suportados**: selecione a variável **Carga inicial** e **Tela inativa**.

   ![ativo](assets/p_usecase6.png)

1. Selecionar a exibição **AssumirControle** do **Localizações** pasta. Selecionar **Atribuir canal** na barra de ações, para que seja possível atribuir o canal de tomada.

1. Atribuir a **AssumirControle** canal para exibir em um horário agendado e preencher os seguintes campos do **Atribuição de canal** caixa de diálogo e seleção **Salvar**:

   * **Caminho do canal**: selecione o caminho para o **AssumirControle** channel
   * **Prioridade**: Defina a prioridade deste canal como maior que a **MainAdChannel**. Por exemplo, a prioridade definida neste exemplo é 8.
   * **Eventos suportados**: selecione a variável **Tela inativa** e **Temporizador**.
   * **Agendar**: Insira o texto do agendamento para o qual você deseja que este canal execute a exibição. O texto no campo **Agendar** mencionado neste exemplo é *na quarta-feira depois das 14:00 e antes das 16:00*.

     >[!NOTE]
     >Para saber mais sobre as expressões que podem ser adicionadas à variável **Agendar**, consulte o [Expressões de exemplo](#example-expressions) abaixo.
   * **ativo desde**: Data e hora de início.
   * **ativo até**: data e hora de término.

     Por exemplo, o texto em **Agendar** e **ativo desde** e **ativo até** A data e a hora aqui permitem que o conteúdo seja reproduzido todas as quartas-feiras, das 14h às 16h.


     ![ativo](assets/p_usecase7.png)

     Navegar para a exibição a partir de **AssumirControle** > **Localizações** > **LobbyPrincipal** > **MainLobbyDisplay** e selecione **Painel** na barra de ações para que você possa visualizar os canais atribuídos com suas prioridades, conforme mostrado abaixo.

     >[!NOTE]
     >É obrigatório definir a prioridade do canal de aquisição como a mais alta.

     ![ativo](assets/p_usecase8.png)
Agora, a variável **AssumirControle** o canal assume o controle do **MainAdChannel** às 14h, por duas horas, até às 16h, de quarta-feira, e reproduz o conteúdo de 9 de janeiro de 2020 a 31 de janeiro de 2020.

## Expressões de exemplo {#example-expressions}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8h | o canal é reproduzido diariamente antes das 8h |
| depois das 14h | o canal é reproduzido depois das 14h todos os dias |
| após 12:15 e antes de 12:45 | o canal é reproduzido diariamente após as 12h15 por 30 minutos |
| antes de 12:15 também depois de 12:45 | o canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45. |
| no primeiro dia de janeiro depois das 14h também no segundo dia de janeiro também no terceiro dia de janeiro antes das 3h. | o canal começa a tocar depois das 14h de 1º de janeiro, continua tocando o dia todo em 2 de janeiro até as 3h de 3 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o canal inicia o player depois das 14h em 1º de janeiro, continua jogando até as 3h em 2 de janeiro, depois começa novamente em 2 de janeiro às 14h e continua tocando até as 3h em 3 de janeiro |

>[!NOTE]
>
>Também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).
