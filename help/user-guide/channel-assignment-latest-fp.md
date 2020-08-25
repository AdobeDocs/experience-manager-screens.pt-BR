---
title: Atribuição de canais - FP mais recente
seo-title: Atribuição de canais - FP mais recente
description: Siga esta página para saber mais sobre Atribuição de Canais e Programação de anúncios.
translation-type: tm+mt
source-git-commit: 0300af2ef44756dddbb27f3da15c52bc877b93ea
workflow-type: tm+mt
source-wordcount: '1548'
ht-degree: 26%

---


# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a atribuição de canais e o agendamento de canais para o AEM 6.5.5 Screens Feature Pack e posterior.

Depois de configurar uma exibição, é necessário atribuir um canal a uma exibição para visualização do conteúdo.

Esta página mostra como atribuir um canal à sua exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.


## Assigning a Channel {#assign-a-channel-new-release}

Siga as seções abaixo para criar um projeto AEM Screens e atribuir um canal a uma tela.

### Criação de um projeto e Canais da AEM Screens {#creating-project}

Siga as etapas abaixo para configurar um projeto e um canal:

1. Crie um projeto da AEM Screens intitulado como **DemoScreens**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para saber como criar um projeto da AEM Screens.

1. Crie um canal de sequência chamado **Cafeteria** na pasta **Canais** .

1. Selecione o canal e clique em **Editar** na barra de ações para adicionar conteúdo ao seu canal.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por exemplo, o canal **Cafeteria** agora exibe as seguintes imagens:

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crie um local chamado **SanJose** e uma tela como **Sala de espera**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Atribuindo Canal a uma exibição {#assigning-channel-to-display}

Depois que a configuração do projeto for concluída, será necessário atribuir o canal a uma exibição para visualização do conteúdo.

1. Navegue até a exibição desejada, por exemplo, **DemoScreens** —> **Locais** —> **SanJose** —> **Sala de espera**.

1. Tap/click **Assign Channel** from the action bar.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Toque/clique em **Painel** e clique em **+Atribuir Canal** no painel CANAIS **ATRIBUÍDOS e AGENDAMENTOS** .

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Na opção **Configurações** , você pode escolher o canal por caminho ou nome, digitar a Função **do** Canal, **Prioridade**, Eventos **** suportados e Métodos **de** interrupção. Além disso, você pode ativar a dica de ferramenta **Atração** nessa caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Consulte a seção Propriedades [do](#channel-properties) Canal para saber mais sobre as propriedades de atribuição do canal.

1. Na opção **Programações** , selecione o Fuso horário **de** referência, a Janela **de** Ativação e a Programação **de**recorrência.
   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Consulte a seção Propriedades [do](#channel-properties) Canal para saber mais sobre as propriedades de atribuição do canal.

1. Clique em **Salvar** depois de configurar suas preferências.

### Exibição do conteúdo no Chrome Player {#viewing-content-output}

Este exemplo mostra a saída em um Chrome Player. Depois de atribuir o canal ao seu monitor, você deve registrar o dispositivo em um player.

Consulte Registro [do](device-registration.md) dispositivo para saber como registrar um dispositivo em um player AEM Screens.

Você visualização a seguinte saída na sua escolha do player:

![new1](assets/channel-assignment/channel-assign-output.gif)

### Noções Gerais das Propriedades do Canal na Caixa de Diálogo Atribuição do Canal {#channel-properties}

As seguintes propriedades são definidas na opção **Configurações** na caixa de diálogo Atribuição **de** Canais.

![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

#### Selecionar um canal {#select-channel}

Selecionar um canal permite fornecer uma referência ao canal desejado, seja por nome de canal ou por caminho de canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **pelo nome**: Insira o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite que você crie a versão local de um canal para resolver dinamicamente o conteúdo específico da localização. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

#### Função de canal {#role-channel}

A função de canal define o contexto da exibição. A função é o alvo de várias ações e não depende do canal real que a atende.

#### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições, no caso de várias delas corresponderem aos critérios de reprodução. A atribuição com o valor mais alto sempre terá precedência sobre aquelas com valores mais baixos. Por exemplo, se houver dois canais, A e B, em que A tem uma prioridade de 1 e B tem uma prioridade de 2, o canal B será exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>A prioridade de um canal é definida como um número (1 para o valor mínimo) na caixa de diálogo **Atribuição de canal**, conforme mencionado acima. Além disso, os canais atribuídos são classificados com base em uma prioridade decrescente.

#### Eventos compatíveis {#supported-events-channel}

* **Carga inicial**: carrega o canal quando o player é iniciado. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Tela inativa**: carregado quando a tela está inativa. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Temporizador**: precisa ser definido quando um agendamento é fornecido
* **Interação do usuário**: o player mudará para o canal especificado se houver uma interação de usuário na tela (toque) em um canal inativo e será carregado quando a tela for tocada

#### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
>
> Esta opção só está disponível com AEM 6.4 Feature Pack 8 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido para que possa optar por interromper o conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja reproduzido totalmente antes de interromper a reprodução devido ao agendamento.

Selecione uma das seguintes opções disponíveis para definir o método de interrupção na caixa de diálogo Atribuição **de** Canais:

* **Imediatamente**: sempre que o agendamento é ativado ou uma atualização é recebida, você pode interromper a reprodução e atualizar ou reproduzir imediatamente o novo conteúdo
* **No final do ponto** atual: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar que o item atual na sequência termine a reprodução e somente depois disso você atualiza ou reproduz o novo conteúdo
   >[!NOTE]
   >Esta opção está selecionada por padrão.
* **No final da sequência**: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de esperar que a sequência inteira atinja sua extremidade, e logo antes da sequência desejada, você volta ao primeiro elemento, atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >Usar a segunda ou a terceira opção pode resultar em tempos de programação definidos na atribuição ligeiramente adiados, já que o player aguardará o fim do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.


As seguintes propriedades são definidas na opção **Agendar** na caixa de diálogo Atribuição **de** Canais.

#### Fuso horário de referência {#reference-timezone}

O fuso horário de referência permite selecionar o fuso horário para a exibição do conteúdo.

#### Janela de ativação {#activation-window}

A janela Ativação permite selecionar uma data **de** Start e uma data **de** término para exibir seu conteúdo.

#### Programação de recorrência {#recurrence-schedule}

A Programação de recorrência permite definir uma programação recorrente para o seu conteúdo. Clique em **+ Adicionar agendamento** para adicionar um agendamento de recorrência ao seu canal.

>[!NOTE]
>Você pode adicionar várias programações recorrentes ao seu canal.
>Recurrence Schedules introduces *DayParting*, that allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

É possível definir as seguintes opções:

* **Nome**: Título do seu agendamento de recorrência.
* **Repetir**: Escolha se a programação é executada **Diariamente**, **Semanalmente**, **Mensalmente** ou **Anualmente**.
* **Start**: A hora do start para o seu horário.
* **Fim**: A hora de término do seu agendamento. Você pode defini-lo por:
* **Hora**: O agendamento terminará em um horário especificado.
* **Duração**: O agendamento é executado por uma duração específica em horas ou minutos.

### DayParting {#dayparting}

A Segmentação de dia refere-se ao processo de dividir um dia em períodos de tempo e especificar qual conteúdo é reproduzido no horário desejado. A AEM Screens permite que você programe canais em termos de DayParting em um dia, semana ou mês de acordo com a necessidade.

Os exemplos a seguir explicam DayParting em canais em três cenários diferentes:

#### Reprodução do conteúdo em um único dia, dividido em vários períodos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um Restaurante usa o DayParting para mostrar seu café da manhã, almoço e menu de jantar todos os dias.

Aqui, dividiremos cada dia em intervalos de tempo diferentes, para que o conteúdo do canal seja reproduzido conforme a hora especificada do dia. Defina as seguintes propriedades da Programação de recorrência para reproduzir o conteúdo conforme esse caso de uso.

| **Nome** | **Repetir** | **Início** | **End** |
|---|---|---|---|
| Café da manhã | Diariamente | 06:00 | 11:00 |
| Almoço | Diariamente | 11:02 | 15:00 |
| Jantar | Diariamente | 15:01 | 20:00 |

#### Reprodução do conteúdo em um determinado dia da semana {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o DayParting implementado em um casino onde o evento ao vivo ocorre todo fim de semana, das 20h às 22h e os especiais estão disponíveis para o menu do jantar depois das 22h até às 13h.

| **Nome** | **Repetir** | **Início** | **End** |
|---|---|---|---|
| Final de semana | Semanalmente | 20:00 | 22:00 |
| Especial | Diariamente | 22:00 | 01:00 |

**Final de semana**


**Especial**

#### Reprodução do conteúdo para um ou mais meses específicos {#playing-content-for-a-particular-month-months}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de verão dos meses de junho a agosto e a coleção de outono de setembro até o final de outubro.

Aqui, você criará DayParting como por mês, para que o conteúdo do canal seja reproduzido conforme os meses especificados do ano.


>[!NOTE]
>
>Além disso, você pode definir uma ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e horário ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo para a prioridade pode ser definido como 0.

#### Reprodução do conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de inverno com a mesma programação no mês de dezembro. Porém, como o Canal B tem a prioridade definida como 2, na semana em questão, ele reproduzirá seu conteúdo no lugar do Canal A.

## Timeline View {#timeline-view}

Depois de atribuir um canal a uma exibição e configurar um agendamento de recorrência, você pode visualização a linha do tempo do painel CANAIS **ATRIBUÍDOS e AGENDAMENTOS** .

Siga as etapas abaixo para navegar até a visualização da linha do tempo:



