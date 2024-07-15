---
title: Atribuição de canal - FP mais recente
description: Saiba mais sobre Atribuição de canal e Divisão de dia.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 2%

---

# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>
>Esta seção destaca a Atribuição de canal e a programação de canais para o Pacote de recursos do Screens AEM 6.5.5 e posterior.

Ao configurar uma exibição, atribua um canal a uma exibição para visualizar seu conteúdo.

Esta página mostra como atribuir um canal à exibição, compreender as propriedades do canal e Dividir o dia.

>[!NOTE]
>
>É possível atribuir vários canais a uma exibição.


## Atribuição de um canal {#assign-a-channel-new-release}

Siga as seções abaixo para criar um projeto do AEM Screens e atribuir um canal a uma exibição.

### Criação de um projeto e canais do AEM Screens {#creating-project}

Siga as etapas abaixo para configurar um projeto e um canal:

1. Crie um projeto do AEM Screens intitulado como **DemoScreens**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Para saber como criar um projeto do AEM Screens, consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md).

1. Crie um canal de sequência chamado **Cafeteria** na pasta **Canais**.

1. Clique no canal e em **Editar** na barra de ações.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por exemplo, o canal **Cafeteria** agora exibe as seguintes imagens:

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crie um Local intitulado como **SanJose** e uma exibição como **Lobby**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Atribuição de canal a uma Exibição {#assigning-channel-to-display}

Quando a configuração do projeto for concluída, atribua o canal a uma exibição para visualizar o conteúdo.

1. Navegue até a exibição necessária, por exemplo, **DemoScreens** > **Locations** > **SanJose** > **Lobby**.

1. Clique em **Atribuir canal** na barra de ações.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Clique em **Painel** na barra de ações e em **+Atribuir Canal** no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. A caixa de diálogo **Atribuição de canal** é aberta.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Na opção **Configurações**, você pode escolher o canal **por caminho** ou **por nome**, inserir os **Função do Canal**, **Prioridade**, **Eventos com Suporte** e **Métodos de Interrupção**. Além disso, é possível ativar a dica de ferramenta de atração nessa caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Para saber mais sobre as propriedades de Atribuição de canal, consulte a seção [Propriedades de Canal](#channel-properties).

1. Na opção **Agendar**, clique em **Janela de Ativação** e **Agendamento de Recorrência**.
   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Para saber mais sobre as propriedades de Atribuição de canal, consulte a seção [Propriedades de Canal](#channel-properties).

1. Clique em **Salvar** depois de configurar suas preferências.

### Visualização de conteúdo no Chrome Player {#viewing-content-output}

Este exemplo mostra a saída em um Chrome Player. Depois de atribuir o canal à exibição, registre o dispositivo em um reprodutor.

Para saber como registrar um dispositivo em um AEM Screens Player, consulte [Registro de Dispositivo](device-registration.md).

Você pode exibir a seguinte saída ao escolher um reprodutor:

![novo1](assets/channel-assignment/channel-assign-output.gif)

## Exibição da linha do tempo {#timeline-view}

Ao atribuir um canal a uma exibição e configurar um Cronograma de Recorrência, você poderá ver a linha do tempo no painel **CANAIS &amp; AGENDAMENTOS ATRIBUÍDOS**.

Siga as etapas abaixo para navegar até a exibição da linha do tempo:

1. Navegue até a exibição necessária, por exemplo, **DemoScreens** > **Locations** > **SanJose** > **Lobby**.

1. Clique em **Atribuir canal** na barra de ações.

   Ou,

   Clique em **Painel** e em **Linha do tempo** no painel **CANAIS ATRIBUÍDOS e AGENDAMENTOS**.

   ![imagem](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Como entender as propriedades do canal na caixa de diálogo Atribuição de canal {#channel-properties}

As seguintes propriedades são definidas na opção **Configurações** da caixa de diálogo **Atribuição de canal**.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Selecionar um canal {#select-channel}

A seleção de um canal permite fornecer uma referência ao canal desejado, por nome de canal ou por caminho de canal.

* **Por caminho** - Você fornece uma referência explícita usando o caminho absoluto do canal.
* **Por nome** - Você insere o nome do canal que é resolvido para um canal real por contexto. Esse recurso permite criar uma versão local de um canal para que você possa resolver dinamicamente o conteúdo específico do local. Por exemplo, um canal com o nome *ofertas do dia*, em que o conteúdo real seria diferente em duas cidades, mas você ainda tem a função de canal seguro em todas as exibições.

### Função do canal {#role-channel}

A função do canal define o contexto da exibição. Várias ações direcionam a função. É independente do canal real que desempenha a função.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre tem prioridade sobre valores mais baixos. Por exemplo, se houver dois canais A e B. A tem uma prioridade 1 e B tem uma prioridade 2, então o canal B é exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>
>A prioridade de um canal é definida como um número (1 para o mínimo) na caixa de diálogo **Atribuição de canal**, conforme mencionado acima. Além disso, os canais atribuídos são classificados com base na prioridade decrescente.

### Eventos suportados {#supported-events-channel}

* **Carregamento inicial** - carrega o canal quando o reprodutor é iniciado. Ele pode ser atribuído a vários canais com um agendamento.
* **Tela Inativa** - Carrega quando a tela está inativa. Ele pode ser atribuído a vários canais com um agendamento.
* **Timer** - Deve ser definido quando um agendamento é fornecido.
* **Interação do usuário** - O reprodutor alterna para o canal especificado se houver uma interação do usuário na tela (toque) em um canal ocioso e é carregado quando a tela é tocada.

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
> Esta opção só está disponível com o <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4.

Como um Autor de conteúdo, você pode especificar quando um canal é interrompido. Com isso, você pode optar por cortar conteúdo não crítico. Mas também oferece a opção de permitir que conteúdo importante seja totalmente reproduzido antes de ser cortado por causa do agendamento.

Selecione uma das seguintes opções que estão disponíveis para definir o método de interrupção na caixa de diálogo **Atribuição de canal**:

* **Imediatamente** - Sempre que o agendamento for ativado ou uma atualização for recebida, você pode interromper a reprodução e atualizar ou reproduzir o novo conteúdo imediatamente
* **Fim do item atual** - Quando um novo agendamento é ativado ou uma atualização é recebida, você pode aguardar até que o item atual na sequência termine a reprodução. Em seguida, somente depois disso, será possível atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >Essa opção é selecionada por padrão.

* **No final da sequência** - Quando um novo agendamento é ativado ou uma atualização é recebida, você pode aguardar até que toda a sequência atinja seu final. Em seguida, logo antes da sequência desejada, você pode voltar para o primeiro elemento, atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >O uso da segunda ou da terceira opção pode fazer com que os horários de programação definidos na atribuição sejam ligeiramente adiados. O motivo é que o reprodutor aguarda o final do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso depende da duração da reprodução do item.

As seguintes propriedades são definidas na opção **Agendar** da caixa de diálogo **Atribuição de canal**.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Janela de ativação {#activation-window}

A Janela de Ativação permite selecionar uma **Data de início** e uma **Data de término** para exibir seu conteúdo.

### Programação de recorrência {#recurrence-schedule}

O Cronograma recorrente permite que você defina um cronograma recorrente para o seu conteúdo. Clique em **+ Adicionar Agendamento** para adicionar um Agendamento de Recorrência ao seu canal.

>[!NOTE]
>Você pode adicionar vários agendamentos recorrentes ao seu canal.
>Os Agendamentos de Recorrência apresentam *DayParting*. Você define um agendamento global com vários canais sendo executados em horários específicos do dia e reutiliza esse agendamento configurado para todas as suas exibições de uma só vez.

É possível definir as seguintes opções:

* **Nome** - Título de sua Agenda de Recorrência.
* **Repetir** - Escolha se o agendamento é executado **Diariamente**, **Semanalmente**, **Mensalmente** ou **Anualmente**.
* **Início** - A hora inicial da sua agenda.
* **Fim** - A hora de término de seu cronograma. Você pode defini-lo por tempo ou duração.
   * **Hora** - O agendamento termina em um horário especificado.
   * **Duração** - O agendamento é executado para uma duração de tempo específica em horas ou minutos.

### DayParting {#dayparting}

Divisão de dia refere-se à divisão de um dia em intervalos de tempo e à especificação de qual conteúdo é reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de DayParting em um dia, semana ou mês, de acordo com o requisito.

Os exemplos a seguir explicam o DayParting em canais em três cenários diferentes:

#### Reprodução de conteúdo em um único dia dividido em vários intervalos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa o DayParting para exibir seu menu de café da manhã, almoço e jantar todos os dias.

Aqui, cada dia é dividido em diferentes intervalos de tempo, para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia. Defina as seguintes propriedades do Cronograma de recorrência para que seu canal reproduza o conteúdo de acordo com este caso de uso.

| **Nome** | **Repetições** | **Início** | **Fim** |
|---|---|---|---|
| Café da manhã | Diariamente | 6:00 | 11:00 |
| Almoço | Diariamente | 11:00 | 15H |
| Jantar | Diariamente | 15H | 20:00 |

#### Reproduzir conteúdo em um dia da semana específico {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o DayParting implementado em um cassino em que o evento ao vivo ocorre todos os finais de semana das 20:00 às 22:00, e os especiais estão disponíveis para o menu de jantar entre as 22:00 e as 1:00.

| **Nome** | **Repetições** | **Início** | **Fim** |
|---|---|---|---|
| Fim de semana | Semanalmente: sábado e domingo | 20:00 | 22:00 |
| Especiais | Diariamente: de segunda a sexta-feira | 22:00 | 1:00 |

>[!NOTE]
>
>Além disso, você pode definir a ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e hora ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo de prioridade pode ser definido como 0.
