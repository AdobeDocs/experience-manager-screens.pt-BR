---
title: Atribuição de canal - FP mais recente
seo-title: Channel Assignment - Latest FP
description: Siga esta página para saber mais sobre Atribuição de canal e Divisão de dia.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1467'
ht-degree: 3%

---

# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>
>Esta seção destaca a atribuição e a programação de canais para o Pacote de recursos do Telas AEM 6.5.5 e posteriores.

Depois de configurar uma exibição, você deve atribuir um canal a uma exibição para visualizar seu conteúdo.

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
   >Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para saber como criar um projeto do AEM Screens.

1. Criar um canal de sequência com o título **Cafeteria** no **Canais** pasta.

1. Selecione o canal e clique em **Editar** na barra de ações para adicionar conteúdo ao seu canal.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por exemplo, a variável **Cafeteria** o channel agora exibe as seguintes imagens:

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Criar um local intitulado como **San Jose** e uma exibição como **Lobby**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Atribuição de canal a uma Exibição {#assigning-channel-to-display}

Quando a configuração do projeto for concluída, você deve atribuir o canal a uma exibição para visualizar o conteúdo.

1. Navegue até a exibição necessária, por exemplo, **DemoScreens** —> **Localizações** —> **San Jose** —> **Lobby**.

1. Toque/clique **Atribuir canal** na barra de ações.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Toque/clique **Painel** na barra de ações e clique em **+Atribuir canal** do **CANAIS ATRIBUÍDOS E AGENDAMENTOS** painel.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. A variável **Atribuição de canal** é aberta.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. No **Configurações** opção, você pode escolher o canal **por caminho** ou **por nome**, insira o **Função do canal**, **Prioridade**, **Eventos suportados**, e **Métodos de interrupção**. Além disso, você pode ativar a dica de ferramenta de atração nessa caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Consulte [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades de atribuição do canal.

1. No **Agendar** opção selecione a variável **Janela de ativação** e **Agendamento recorrente**.
   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consulte [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades de atribuição do canal.

1. Clique em **Salvar** após configurar suas preferências.

### Exibição de conteúdo no Chrome Player {#viewing-content-output}

Este exemplo mostra a saída em um Chrome Player. Depois de atribuir o canal ao vídeo, você deve registrar o dispositivo em um reprodutor.

Consulte [Registro do dispositivo](device-registration.md) para saber como registrar um dispositivo em um AEM Screens player.

Você visualizará a seguinte saída ao escolher um reprodutor:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Exibição da linha do tempo {#timeline-view}

Depois de atribuir um canal a uma exibição e configurar um cronograma recorrente, você pode visualizar a linha do tempo na **CANAIS ATRIBUÍDOS E AGENDAMENTOS** painel.

Siga as etapas abaixo para navegar até a exibição da linha do tempo:

1. Navegue até a exibição necessária, por exemplo, **DemoScreens** —> **Localizações** —> **San Jose** —> **Lobby**.

1. Toque/clique **Atribuir canal** na barra de ações.

   Ou,

   Toque/clique **Painel** e clique em **Linha do tempo** do **CANAIS ATRIBUÍDOS E AGENDAMENTOS** painel.

   ![imagem](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Como entender as propriedades do canal na caixa de diálogo Atribuição de canal {#channel-properties}

As seguintes propriedades são definidas no **Configurações** opção no **Atribuição de canal** caixa de diálogo.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Selecionar um canal {#select-channel}

A seleção de um canal permite fornecer uma referência ao canal desejado, por nome de canal ou por caminho de canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome**: digite o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite criar a versão local de um canal para resolver dinamicamente o conteúdo específico do local. Por exemplo, um canal com nome *ofertas do dia*, onde o conteúdo real seria diferente em duas cidades, mas você ainda tem a função de canal segura em todas as exibições.

### Função do canal {#role-channel}

A função do canal define o contexto da exibição. A função é direcionada por várias ações e é independente do canal real que desempenha a função.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre terá precedência sobre os valores mais baixos. Por exemplo, se houver dois canais A e B. A tem uma prioridade 1 e B tem uma prioridade 2, então o canal B é exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>
>A prioridade de um canal é definida como um número (1 para o mínimo) na variável **Atribuição de canal** como mencionado acima. Além disso, os canais atribuídos são classificados com base na prioridade decrescente.

### Eventos suportados {#supported-events-channel}

* **Carga inicial**: carrega o canal quando o reprodutor é iniciado. Ele pode ser atribuído a vários canais em combinação com o agendamento
* **Tela inativa**: carrega quando a tela está ociosa. Ele pode ser atribuído a vários canais em combinação com o agendamento
* **Temporizador**: precisa ser definido quando uma agenda for fornecida
* **Interação do usuário**: o reprodutor alternará para o canal especificado, se houver uma interação do usuário na tela (toque) em um canal ocioso e será carregado quando a tela for tocada

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
> Essa opção só está disponível com o Feature Pack 8 para AEM 6.4 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido para que possa optar por cortar conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja totalmente reproduzido antes de interromper a reprodução por causa do agendamento.

Selecione uma das seguintes opções que estão disponíveis para definir o método de interrupção no **Atribuição de canal** caixa de diálogo:

* **Imediatamente**: sempre que a programação for ativada ou uma atualização for recebida, você poderá interromper a reprodução e atualizar ou reproduzir o novo conteúdo imediatamente
* **No fim do item atual**: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar até que o item atual na sequência termine a reprodução e, somente depois disso, atualizar ou reproduzir o novo conteúdo

   >[!NOTE]
   >Essa opção é selecionada por padrão.

* **No final da sequência**: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar até que toda a sequência atinja seu fim e, logo antes da sequência desejada, você volta para o primeiro elemento, atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >Usar a segunda ou terceira opção pode fazer com que os tempos de agendamento definidos na atribuição sejam ligeiramente adiados, pois o reprodutor aguardará o final do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.

As seguintes propriedades são definidas no **Agendar** opção no **Atribuição de canal** caixa de diálogo.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Janela de ativação {#activation-window}

A janela Ativation permite selecionar um **Data inicial** e uma **Data final** para exibir seu conteúdo.

### Programação de recorrência {#recurrence-schedule}

O Cronograma recorrente permite que você defina um cronograma recorrente para o seu conteúdo. Clique em **+ Adicionar programação** para adicionar uma agenda de recorrência ao seu canal.

>[!NOTE]
>Você pode adicionar vários agendamentos recorrentes ao seu canal.
>Os Cronogramas de recorrência apresentam *DayParting*, que permite definir um agendamento global com vários canais sendo executados em horários específicos do dia e reutilizar essa configuração para todas as exibições de uma só vez.

É possível definir as seguintes opções:

* **Nome**: Título do cronograma recorrente.
* **Repetir**: escolha se a programação é executada **Diariamente**, **Semanalmente**, **Mensal** ou **Anual**.
* **Início**: a hora de início da sua programação.
* **Fim**: a hora de término do cronograma. Você pode defini-lo por tempo ou duração.
   * **Hora**: A programação será encerrada em um horário especificado.
   * **Duração**: A programação é executada por uma duração de tempo específica em horas ou minutos.

### DayParting {#dayparting}

DayParting refere-se à divisão de um dia em intervalos de tempo e à especificação de qual conteúdo é reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de DayParting em um dia, semana ou mês, de acordo com o requisito.

Os exemplos a seguir explicam o DayParting em canais em três cenários diferentes:

#### Reprodução de conteúdo em um único dia dividido em vários intervalos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa o DayParting para exibir seu menu de café da manhã, almoço e jantar todos os dias.

Aqui, dividiremos cada dia em diferentes intervalos de tempo, para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia. Defina as seguintes propriedades do Cronograma de recorrência para que seu canal reproduza o conteúdo de acordo com este caso de uso.

| **Nome** | **Repetições** | **Início** | **Fim** |
|---|---|---|---|
| Café da manhã | Diariamente | 18h AM | 11:00 h |
| Almoço | Diariamente | 11:00 h | 15:00 h |
| Jantar | Diariamente | 15:00 h | 20:00 h |

#### Reproduzir conteúdo em um dia da semana específico {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o DayParting implementado em um cassino em que o evento ao vivo ocorre todos os finais de semana das 20h às 22h e os especiais estão disponíveis para o menu de jantar após as 22h até às 13h.

| **Nome** | **Repetições** | **Início** | **Fim** |
|---|---|---|---|
| Fim de semana | Semanalmente: sábado, domingo | 20:00 h | 22:00 h |
| Especiais | Diariamente: de segunda a sexta-feira | 22:00 h | 1h AM |

>[!NOTE]
>
>Além disso, você pode definir ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e hora ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo de prioridade pode ser definido como 0.
