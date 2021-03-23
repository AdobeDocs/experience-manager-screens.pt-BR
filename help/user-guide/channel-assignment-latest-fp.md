---
title: Atribuição de canal - FP mais recente
seo-title: Atribuição de canal - FP mais recente
description: Siga esta página para saber mais sobre Atribuição de canal e DayParting.
feature: Telas de criação, atribuição de canal
role: Administrador, Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1478'
ht-degree: 23%

---


# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>
>Esta seção destaca a atribuição de canal e o agendamento de canais para AEM 6.5.5 Screens Feature Pack e posterior.

Depois de configurar uma exibição, é necessário atribuir um canal a uma exibição para visualizar o conteúdo.

Esta página mostra a atribuição de um canal a sua exibição, as propriedades do canal e o DayParting.

>[!NOTE]
>
>Você pode atribuir vários canais a uma exibição.


## Atribuindo um Canal {#assign-a-channel-new-release}

Siga as seções abaixo para criar um projeto do AEM Screens e atribuir um canal a uma exibição.

### Criação de um projeto e canais do AEM Screens {#creating-project}

Siga as etapas abaixo para configurar um projeto e um canal:

1. Crie um projeto do AEM Screens chamado **DemoScreens**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para saber como criar um projeto do AEM Screens.

1. Crie um canal de sequência chamado **Cafeteria** na pasta **Channels**.

1. Selecione o canal e clique em **Editar** na barra de ações para adicionar conteúdo ao seu canal.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por exemplo, o canal **Cafeteria** agora exibe as seguintes imagens:

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crie um Local chamado **SanJose** e uma exibição como **Lobby**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Atribuindo canal a um monitor {#assigning-channel-to-display}

Quando a configuração do projeto for concluída, você deverá atribuir o canal a uma exibição para visualizar o conteúdo.

1. Navegue até a exibição desejada, por exemplo, **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Toque/clique em **Atribuir canal** na barra de ações.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Toque/clique em **Painel** na barra de ações e clique em **+Atribuir canal** no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. A caixa de diálogo **Atribuição de canal** é aberta.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Na opção **Settings**, você pode escolher o canal **por caminho** ou **por nome**, inserir o **Função do canal**, **Prioridade**, **Eventos suportados** e &lt;a1 2/>Métodos de interrupção **.** Além disso, é possível ativar a dica de ferramenta de atração nessa caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Consulte a seção [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades de atribuição de canal.

1. Na opção **Schedule** selecione a **Janela de Ativação** e **Recurrence Schedule**.
   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Consulte a seção [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades de atribuição de canal.

1. Clique em **Salvar** após configurar suas preferências.

### Visualização do conteúdo no Chrome Player {#viewing-content-output}

Este exemplo mostra a saída em um Player do Chrome. Depois de atribuir o canal à exibição, registre o dispositivo em um player.

Consulte [Device Registration](device-registration.md) para saber como registrar um dispositivo em um player do AEM Screens.

Você visualizará a seguinte saída na sua escolha do reprodutor:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Exibição da linha do tempo {#timeline-view}

Depois de atribuir um canal a uma exibição e configurar um agendamento de recorrência, você pode visualizar a linha do tempo no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

Siga as etapas abaixo para navegar até a exibição de linha do tempo:

1. Navegue até a exibição desejada, por exemplo, **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Toque/clique em **Atribuir canal** na barra de ações.

   Ou,

   Toque/clique em **Painel** e clique em **Linha do tempo** no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

   ![imagem](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Noções Gerais das Propriedades do Canal na Caixa de Diálogo Atribuição de Canal {#channel-properties}

As seguintes propriedades são definidas na opção **Settings** na caixa de diálogo **Atribuição de canal**.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Selecionar um canal {#select-channel}

Selecionar um canal permite fornecer uma referência ao canal desejado, seja por nome de canal ou por caminho de canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome**: Você insere o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite que você crie a versão local de um canal para resolver dinamicamente o conteúdo específico da localização. Por exemplo, um canal com o nome *ofertas do dia*, em que o conteúdo real seria diferente em duas cidades, mas você ainda tem a mesma função de canal em todas as exibições.

### Função de canal {#role-channel}

A função de canal define o contexto da exibição. A função é o alvo de várias ações e não depende do canal real que a atende.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições, no caso de várias delas corresponderem aos critérios de reprodução. A atribuição com o valor mais alto sempre terá precedência sobre aquelas com valores mais baixos. Por exemplo, se houver dois canais, A e B, em que A tem uma prioridade de 1 e B tem uma prioridade de 2, o canal B será exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>
>A prioridade de um canal é definida como um número (1 para o valor mínimo) na caixa de diálogo **Atribuição de canal**, conforme mencionado acima. Além disso, os canais atribuídos são classificados com base em uma prioridade decrescente.

### Eventos compatíveis {#supported-events-channel}

* **Carga inicial**: carrega o canal quando o player é iniciado. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Tela inativa**: carregado quando a tela está inativa. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Temporizador**: precisa ser definido quando um agendamento é fornecido
* **Interação do usuário**: o player mudará para o canal especificado se houver uma interação de usuário na tela (toque) em um canal inativo e será carregado quando a tela for tocada

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
> Essa opção só está disponível com o AEM 6.4 Feature Pack 8 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido, para que possa optar por cortar conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja totalmente reproduzido antes de interromper a reprodução devido ao agendamento.

Selecione uma das seguintes opções disponíveis para definir o método de interrupção na caixa de diálogo **Atribuição de canal**:

* **Imediatamente**: sempre que o cronograma é ativado ou uma atualização é recebida, você pode interromper a reprodução e atualizar imediatamente ou reproduzir o novo conteúdo
* **No final do item** atual: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de aguardar a conclusão da reprodução do item atual na sequência e somente depois disso você atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >Esta opção está selecionada por padrão.

* **No final da sequência**: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de esperar que toda a sequência atinja seu fim e, logo antes da sequência desejada, você faz o loop de volta para o primeiro elemento, atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >O uso da segunda ou terceira opção pode resultar no agendamento de tempos definido na atribuição a serem ligeiramente adiados, pois o reprodutor aguardará o fim do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.

As seguintes propriedades são definidas na opção **Schedule** na caixa de diálogo **Atribuição de canal**.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Janela de ativação {#activation-window}

A Janela de Ativação permite selecionar uma **Start date** e uma **End date** para exibir seu conteúdo.

### Programação de recorrência {#recurrence-schedule}

O Agendamento de recorrência permite definir um agendamento recorrente para o seu conteúdo. Clique em **+ Adicionar Programação** para adicionar um agendamento de recorrência ao seu canal.

>[!NOTE]
>Você pode adicionar várias programações recorrentes ao seu canal.
>Os Agendamentos de recorrência apresentam *DayParting*, que permite definir um agendamento global com vários canais em execução em horários específicos do dia e reutilizar essa configuração para todas as suas exibições de uma só vez.

Você pode definir as seguintes opções:

* **Nome**: Título do seu agendamento de recorrência.
* **Repita**: Escolha se a programação é  **Diária**,  **Semanal**,  **Mensal** ou  **Anual**.
* **Início**: A hora de início da sua programação.
* **Fim**: A hora de término da sua programação. Você pode defini-lo por tempo ou duração.
   * **Hora**: O agendamento terminará em um horário especificado.
   * **Duração**: O agendamento é executado por uma duração específica em horas ou minutos.

### DayParting {#dayparting}

DayParting refere-se à divisão de um dia em períodos de tempo e à especificação de qual conteúdo será reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de DayParting em um dia, semana ou mês, de acordo com a necessidade.

Os exemplos a seguir explicam DayParting em canais em três cenários diferentes:

#### Reprodução do conteúdo em um único dia, dividido em vários períodos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa o DayParting para mostrar seu menu de café da manhã, almoço e jantar todos os dias.

Aqui, dividiremos cada dia em intervalos de tempo diferentes, para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia. Defina as seguintes propriedades do Agendamento de recorrência para seu canal para reproduzir o conteúdo de acordo com este caso de uso.

| **Nome** | **Repetições** | **Início** | **End** |
|---|---|---|---|
| Café da manhã | Diariamente | 6:00 | 11:00 |
| Almoço | Diariamente | 11:00 | 15:00 |
| Jantar | Diariamente | 15:00 | 20:00 |

#### Reprodução do conteúdo em um determinado dia da semana {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra a DayParting implementada em um casino onde o evento ao vivo ocorre todos os finais de semana, das 20h às 22h, e os especiais estão disponíveis para o menu do jantar depois das 22h até às 13h.

| **Nome** | **Repetições** | **Início** | **End** |
|---|---|---|---|
| Fim de semana | Semanalmente: Sábado,Domingo | 20:00 | 22:00 |
| Especiais | Diariamente: Segunda-feira-Sexta-feira | 22:00 | 01:00 |

>[!NOTE]
>
>Além disso, você pode definir uma ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e horário ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo para a prioridade pode ser definido como 0.
