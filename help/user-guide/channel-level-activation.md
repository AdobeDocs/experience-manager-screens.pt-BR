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
translation-type: tm+mt
source-git-commit: d6006c553b53dc7dfb52a03cfeb1a50e8e8de792

---


# Ativação de nível de canal {#channel-level-activation-single-event-playback}

Esta página descreve a ativação no nível do canal para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Usando a ativação de nível de canal como uma reprodução de evento único
* Tratamento de recorrência para ativos em um canal
   * Partilha de Dia
   * Semana de Partida
   * Mês de separação
   * Combinação de peças
* Usando a ativação de nível de canal como uma reprodução de evento único

## Visão geral {#overview}

***A Ativação*** de nível de canal permite que os canais mudem após uma programação definida específica. O canal de evento único substitui o canal principal após um agendamento definido e é reproduzido por um determinado tempo, até que o canal principal reproduza seu conteúdo novamente.

O exemplo a seguir fornece uma solução focando nos seguintes termos principais:

* um canal ***de sequência*** principal para a sequência global
* um canal ***de evento*** único que é executado somente uma vez em um horário definido
* um agendamento ***definido e prioridade*** para o evento de reprodução única que ocorre dentro do canal da sequência principal

## Janela de ativação {#using-channel-level-activation}

A seção a seguir explica a criação de uma única reprodução de evento dentro de um canal para um projeto do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, certifique-se de que você tenha os seguintes pré-requisitos prontos para iniciar a implementação da ativação no nível do canal:

* Criar um projeto do AEM Screens, neste exemplo, Ativação de nível de **canal**

* Criar um canal como **MainAdChannel** na pasta **Canais**

* Criar outro canal como **TargetedSinglePlay** na pasta **Canais**

* Adicionar ativos relevantes a ambos os canais

A imagem a seguir mostra o projeto de ativação **de nível de** canal com canais **MainAdChannel** e **TargetedSinglePlay** na pasta **Canais** .

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e como criar um canal de sequência, consulte os recursos a seguir:
>
>* [Criação e gerenciamento de projetos](creating-a-screens-project.md)
   >
   >
* [Gerenciamento de um canal](managing-channels.md)
>



### Implementação {#implementation}

A implementação da ativação de nível de canal em um projeto do AEM Screens envolve três tarefas principais:

1. **Configuração da taxonomia do projeto incluindo Canais, Locais e Exibições**
1. **Atribuindo Canais à Exibição**
1. **Configuração de um agendamento e prioridade**

Siga as etapas abaixo para implementar a funcionalidade:

1. **Criar um local**

   Navegue até a pasta **Locais** no projeto do AEM Screens e crie um local como **Região**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para saber como criar um local, consulte **[Criação e gerenciamento de locais](managing-locations.md)**.

1. **Criar exibição em Localização**

   1. Navegue até Ativação **de nível de** canal > **Locais** > **Região**.
   1. Selecione **Região** e clique em **+ Criar** na barra de ações.
   1. Selecione **Exibir** no assistente e crie uma exibição chamada **RegionDisplay.**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Atribuir canais à exibição**

   Para **MainAdChannel:**

   1. Navegue até Ativação **de nível de** canal > **Locais** > **Região** > **Exibição** de região e clique em **Atribuir canal** na barra de ações.
   1. **A caixa de diálogo Atribuição** de canal é aberta.
   1. Select **Reference Channel**.. by path.
   1. Selecione o Caminho **do** canal como Ativação **de nível de** canal —> ***Canais*** —> ***MainAdChannel***.
   1. A Função **de** canal é preenchida como **canal principal**.
   1. Selecione a **Prioridade** como **1**.
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. Clique em **Salvar**.
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Você também pode atribuir canal do painel de exibição navegando até **Channel Level Ativation** —> **Locations** —> **Region** —> **RegionDisplay** e clicando em **Dashboard** na barra de ação. Clique em **+ Atribuir canal** no painel CANAIS E PROGRAMAS **ATRIBUÍDOS** .

   Da mesma forma, atribua channel **TargetedSinglePlay** para display**:

   1. Navegue até **Channel Level Ativation** —> **Locations** —> **Region** —> **RegionDisplay** e clique em **Atribuir canal** na barra de ações.
   1. **A caixa de diálogo Atribuição** de canal é aberta.
   1. Select **Reference Channel**.. by path.
   1. Selecione o Caminho **do** canal como Ativação **de nível de** canal* —> ***Canais*** —> ***TargetedSinglePlay***.
   1. A Função **de** canal é preenchida como **targetedsingleplay**.
   1. Defina a **Prioridade** como **2**.
   1. Selecione os eventos **** suportados como carga **** inicial, tela **** inativa e **temporizador**, *conforme mostrado na figura abaixo.
   1. Escolha a data em **atividade a partir** de 27 de novembro de 2018 11:59 e em **atividade até** 28 de novembro de 2018 12:05.
   1. Clique em **Salvar**.
   >[!CAUTION]
   É necessário definir a prioridade para o canal **TargetedSinglePlay** superior ao canal **MainAdSegment** .

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   Para escolher o mesmo dia, é necessário selecionar o dia seguinte e editar a data manualmente para o mesmo dia, mas para uma hora posterior. Isso impede que o usuário selecione uma data anterior. Consulte o exemplo abaixo:

   ![new1](assets/new1.gif)

## Exibição dos resultados {#viewing-the-results}

Depois de configurar os canais e exibir a conclusão, inicie o AEM Screens player para exibir o conteúdo.

O player exibe o conteúdo do **MainAdChannel** e exatamente às 23:59 horas (conforme definido no agendamento), o canal **TargetedSinglePlay** exibirá seu conteúdo até as 12:05 e o **MainAdChannel** retomará a reprodução do conteúdo novamente.

>[!NOTE]
Para saber mais sobre o AEM Screen Player, consulte os seguintes recursos:
* [Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
* [Trabalhar com o AEM Screens Player](working-with-screens-player.md)



## Tratamento de recorrência para ativos em um canal{#handling-recurrence-in-assets}

Você pode programar ativos em um canal para recorrência em determinados intervalos, diariamente, semanalmente ou mensalmente, de acordo com suas necessidades.

Suponha que você queira exibir o conteúdo de um canal somente às sextas-feiras das 13:00 às 10:00 horas. Você pode usar a guia **Ativação** para definir o intervalo recorrente desejado para o ativo.

### Partilha de Dia {#day-parting}

1. Selecione o canal e clique em **Painel** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo Atribuição **de** canal, você pode usar uma expressão ou uma versão de texto natural para especificar sua programação de recorrência.

   >[!NOTE]
Você pode ignorar ou incluir os campos **Ativo de e** Ativo Até **** e adicionar a expressão ao campo Programações, de acordo com sua necessidade.

1. Informe a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para programação de anúncios {#example-one}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 da manhã todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 horas todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |
| Seg,Ter,Qua ou Mon-Qua | o ativo é reproduzido no ativo no canal de segunda a quarta |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 15:00 | o ativo no canal começa a ser reproduzido depois das 14:00 horas do dia 1º de janeiro, continua sendo reproduzido durante todo o dia do dia 2 de janeiro até as 15:00 da manhã do dia 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 15:00 | o ativo no canal inicia o player depois das 14:00 horas de 1º de janeiro, continua reproduzindo até as 15:00 da manhã de 2º de janeiro, e começa novamente em 2º de janeiro às 14:00 e continua reproduzindo até as 15:00 da manhã de 3 de janeiro |

>[!NOTE]
Você também pode usar a notação _militar do tempo_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

### Semana de Partida {#week-parting}

1. Selecione o canal e clique em **Painel** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo Atribuição **de** canal, você pode usar uma expressão ou uma versão de texto natural para especificar sua programação de recorrência.

   >[!NOTE]
Você pode ignorar ou incluir os campos **Ativo de e** Ativo Até **** e adicionar a expressão ao campo Programações, de acordo com sua necessidade.

1. Informe a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para programação de semana {#example-two}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Seg,Ter,Qua ou Mon-Qua | o ativo é reproduzido no ativo no canal de segunda a quarta |
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 da manhã todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 horas todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |

>[!NOTE]
Você também pode usar a notação _militar do tempo_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).


### Mês de separação {#month-parting}

1. Selecione o canal e clique em **Painel** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo Atribuição **de** canal, você pode usar uma expressão ou uma versão de texto natural para especificar sua programação de recorrência.

   >[!NOTE]
Você pode ignorar ou incluir os campos **Ativo de e** Ativo Até **** e adicionar a expressão ao campo Programações, de acordo com sua necessidade.

1. Informe a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para a separação mensal {#example-three}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de fevereiro,maio,agosto,novembro | o ativo é reproduzido no canal em fevereiro, maio, agosto, novembro |

>[!NOTE]
Ao definir dias da semana e meses, você pode usar as notas de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.

>[!NOTE]
Você também pode usar a notação _militar do tempo_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

### Combinação de peças {#combined-parting}

1. Selecione o canal e clique em **Painel** na barra de ações para abrir o painel do canal.

1. Depois de inserir a data/hora de início e a hora de término/data na caixa de diálogo Atribuição **de** canal, você pode usar uma expressão ou uma versão de texto natural para especificar sua programação de recorrência.

   >[!NOTE]
Você pode ignorar ou incluir os campos **Ativo de e** Ativo Até **** e adicionar a expressão ao campo Programações, de acordo com sua necessidade.

1. Informe a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para combinação de partições {#example-four}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00 em Lua,Qua de Jan-Mar | o ativo é reproduzido no canal entre as 18h e as 18h de segunda e quarta, de janeiro a fim de março |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 15:00 | o ativo no canal começa a ser reproduzido depois das 14:00 horas do dia 1º de janeiro, continua sendo reproduzido durante todo o dia do dia 2 de janeiro até as 15:00 da manhã do dia 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 15:00 | o ativo no canal inicia o player depois das 14:00 horas de 1º de janeiro, continua reproduzindo até as 15:00 da manhã de 2º de janeiro, e começa novamente em 2º de janeiro às 14:00 e continua reproduzindo até as 15:00 da manhã de 3 de janeiro |

>[!NOTE]
Ao definir dias da semana e meses, você pode usar as notas de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.  Além disso, você também pode usar a notação de tempo __ militar (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

