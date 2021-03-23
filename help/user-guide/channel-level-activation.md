---
title: Ativação no nível do canal - Reprodução de evento único
seo-title: Ativação no nível do canal - Reprodução de evento único
description: Siga este guia para entender a ativação no nível do canal usando a reprodução de um único evento.
seo-description: Siga este guia para entender a ativação no nível do canal usando a reprodução de um único evento.
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
feature: Telas de criação, Ativação no nível do canal
role: Administrador, Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 0%

---


# Ativação no nível do canal {#channel-level-activation-single-event-playback}

Esta página descreve a ativação no nível do canal para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Usar a ativação de nível de canal como uma reprodução de evento único
* Lidar com a recorrência de ativos em um canal
   * DayParting
   * Divisão de semana
   * MonthParting
   * Combinação de peças
* Usar a ativação de nível de canal como uma reprodução de evento único

## Visão geral {#overview}

***A*** Ativação de nível de canal permite que os canais alternem após um cronograma de conjunto específico. O canal de evento único substitui o canal principal após um agendamento definido e é reproduzido por um tempo específico, até que o canal principal reproduza seu conteúdo novamente.

O exemplo a seguir fornece uma solução com foco nos seguintes termos principais:

* um ***canal de sequência principal*** para a sequência global
* um ***canal de evento único*** que é executado apenas uma vez em um horário definido
* um ***defina o agendamento e a prioridade*** para o evento de reprodução única que ocorre no canal de sequência principal

## Janela de ativação {#using-channel-level-activation}

A seção a seguir explica a criação de uma única reprodução de evento dentro de um canal para um projeto do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de implementar essa funcionalidade, verifique se você tem os seguintes pré-requisitos prontos para começar a implementar a ativação no nível do canal:

* Crie um projeto do AEM Screens, neste exemplo, **Ativação no nível de canal**

* Crie um canal como **MainAdChannel** na pasta **Canais**

* Crie outro canal como **TargetedSinglePlay** na pasta **Canais**

* Adicionar ativos relevantes aos dois canais

A imagem a seguir mostra o projeto **Channel Level Ativation** com os canais **MainAdChannel** e **TargetedSinglePlay** na pasta **Channels**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e como criar um canal de sequência, consulte os recursos abaixo:
>
>* [Criação e gerenciamento de projetos](creating-a-screens-project.md)
   >
   >
* [Gerenciamento de um canal](managing-channels.md)

>



### Implementação {#implementation}

A implementação da Ativação no nível do canal em um projeto do AEM Screens envolve três tarefas principais:

1. **Configurar a taxonomia do projeto, incluindo canais, locais e exibições**
1. **Atribuição de Canais à Exibição**
1. **Configuração de um agendamento e prioridade**

Siga as etapas abaixo para implementar a funcionalidade:

1. **Criar uma localização**

   Navegue até a pasta **Localizações** no seu projeto do AEM Screens e crie um local como **Região**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para saber como criar uma localização, consulte **[Criação e gerenciamento de localizações](managing-locations.md)**.

1. **Criar exibição em Localização**

   1. Navegue até **Ativação no nível do canal** > **Localizações** > **Região**.
   1. Selecione **Região** e clique em **+ Criar** na barra de ações.
   1. Selecione **Display** do assistente e crie uma exibição denominada **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Atribuir canais à exibição**

   Para **MainAdChannel:**

   1. Navegue até **Ativação no nível do canal** > **Localizações** > **Região** > **RegionDisplay** e clique em **Atribuir canal** na barra de ações.
   1. **A caixa de diálogo** Atribuição de canal é aberta.
   1. Selecione **Fazer referência ao canal**... por caminho.
   1. Selecione o **Caminho do Canal** como **Ativação no Nível do Canal** —> ***Canais*** —> ***MainAdChannel***.
   1. A **Função do Canal** é preenchida como **canal principal**.
   1. Selecione a **Prioridade** como **1**.
   1. Selecione **Eventos Suportados** como **Carga Inicial** e **Tela Inativa**.
   1. Clique em **Salvar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Você também pode atribuir canal no painel de exibição navegando até **Ativação no nível do canal** —> **Localizações** —> **Região** —> **RegionDisplay** e clicando em **Painel** na barra de ações. Clique em **+ Atribuir canal** no painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**.

   Da mesma forma, atribua o canal **TargetedSinglePlay** para exibição**:

   1. Navegue até **Ativação no nível do canal** —> **Localizações** —> **Região** —> **RegionDisplay** e clique em **Atribuir canal** na barra de ações.
   1. **A caixa de diálogo** Atribuição de canal é aberta.
   1. Selecione **Fazer referência ao canal**... por caminho.
   1. Selecione o **Caminho do Canal** como **Ativação no Nível do Canal*** —> ***Canais*** —> ***TargetedSinglePlay***.
   1. A **Função do Canal** é preenchida como **targetedsingleplay**.
   1. Defina a **Prioridade** como **2**.
   1. Selecione **Eventos Suportados** como **Carga Inicial**, **Tela Inativa** e **Temporizador**, *conforme mostrado na figura abaixo.
   1. Escolha a data em **ative from** como 27 de novembro de 2018 11:59 pm e em **ative até** como 28 de novembro de 2018 12:05 AM.
   1. Clique em **Salvar**.

   >[!CAUTION]
   Você deve definir a prioridade para o canal **TargetedSinglePlay** maior que o canal **MainAdSegment**.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Para escolher o mesmo dia, é necessário selecionar o dia seguinte e editar manualmente a data para o mesmo dia, mas para um horário posterior. Isso impede que o usuário selecione uma data anterior. Consulte o exemplo abaixo:

   ![new1](assets/new1.gif)

## Visualização dos resultados {#viewing-the-results}

Depois de configurar os canais e exibir, inicie o reprodutor do AEM Screens para exibir o conteúdo.

O reprodutor exibe o conteúdo de **MainAdChannel** e exatamente às 23:59 pm (conforme definido no cronograma), o canal **TargetedSinglePlay** exibirá seu conteúdo até às 12:05 e então o **MainAdChannel** retomará seu conteúdo novamente.

>[!NOTE]
Para saber mais sobre AEM reprodutor de tela, consulte os seguintes recursos:
[Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
[Trabalhar com o AEM Screens Player](working-with-screens-player.md)


## Lidar com a recorrência de ativos em um canal {#handling-recurrence-in-assets}

Você pode programar ativos em um canal para recorrência em determinados intervalos, diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseja exibir o conteúdo de um canal somente nas sextas-feiras, das 13:00 às 22:00. Você pode usar a guia **Ativation** para definir o intervalo recorrente desejado para o ativo.

### Divisão de dia {#day-parting}

1. Selecione o canal e clique em **Dashboard** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para divisão de dia {#example-one}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 AM todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |
| Lua,Tonalidade,Qua ou Mão | o ativo é reproduzido no ativo no canal de segunda a quarta-feira |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 3:00 | o ativo no canal começa a ser reproduzido depois das 14:00 em 1º de janeiro, continua reproduzindo o dia inteiro em 2 de janeiro até as 3:00 em 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 3:00 | o ativo no canal inicia o reprodutor depois das 14:00 PM no dia 1º de janeiro, continua reproduzindo até as 3:00 AM no dia 2 de janeiro, depois começa novamente no dia 2 de janeiro às 14:00 e continua reproduzindo até as 3:00 AM no dia 3 de janeiro |

>[!NOTE]
Você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

### Divisão de semana {#week-parting}

1. Selecione o canal e clique em **Dashboard** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para WeekParting {#example-two}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Lua,Tonalidade,Qua ou Mão | o ativo é reproduzido no ativo no canal de segunda a quarta-feira |
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 AM todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |

>[!NOTE]
Você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).


### MonthParting {#month-parting}

1. Selecione o canal e clique em **Dashboard** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para MonthParting {#example-three}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de fevereiro,maio,agosto,novembro | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |

>[!NOTE]
Ao definir dias da semana e meses, você pode usar as notações de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.

>[!NOTE]
Você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

### Combinação de peças {#combined-parting}

1. Selecione o canal e clique em **Dashboard** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para combinação de partes {#example-four}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00, em Mon,Fim de Jan-Mar | o ativo é reproduzido no canal entre as 6h e as 18h das segundas e quartas-feiras, de janeiro a fim de março |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 3:00 | o ativo no canal começa a ser reproduzido depois das 14:00 em 1º de janeiro, continua reproduzindo o dia inteiro em 2 de janeiro até as 3:00 em 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 3:00 | o ativo no canal inicia o reprodutor depois das 14:00 PM no dia 1º de janeiro, continua reproduzindo até as 3:00 AM no dia 2 de janeiro, depois começa novamente no dia 2 de janeiro às 14:00 e continua reproduzindo até as 3:00 AM no dia 3 de janeiro |

>[!NOTE]
Ao definir dias da semana e meses, você pode usar as notações de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.  Além disso, você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

