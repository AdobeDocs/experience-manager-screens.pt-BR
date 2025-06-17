---
title: Ativação no nível do canal - Reprodução de evento único
description: Saiba mais sobre a ativação no nível do canal usando a reprodução de evento único.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1791'
ht-degree: 1%

---

# Ativação em Nível de Canal {#channel-level-activation-single-event-playback}

Esta página descreve a ativação no nível do canal para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Utilização da Ativação no nível do canal como uma reprodução de evento único
* Manipulação de recorrência do Assets em um canal
   * DayParting
   * WeekParting
   * MonthParting
   * Combinação de Peças
* Utilização da Ativação no nível do canal como uma reprodução de evento único

## Visão geral {#overview}

A ***Ativação no Nível de Canal*** permite que os canais alternem após um cronograma definido específico. O canal de evento único substitui o canal principal após um agendamento definido e é reproduzido por um tempo específico, até que o canal principal reproduza seu conteúdo novamente.

O exemplo a seguir fornece uma solução com foco nos seguintes termos principais:

* um ***canal de sequência principal*** para a sequência global
* um ***único canal de evento*** que é executado apenas uma vez em um horário definido
* um ***definir agenda e prioridade*** para o evento de reprodução único que ocorre dentro do canal da sequência principal

## Janela de ativação {#using-channel-level-activation}

A seção a seguir explica a criação de uma única reprodução de evento em um canal para um projeto do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem os seguintes pré-requisitos prontos para começar a implementar a ativação no nível do canal:

* Crie um projeto AEM Screens, neste exemplo, **Ativação no Nível de Canal**.

* Crie um canal como **MainAdChannel** na pasta **Channels**.

* Crie outro canal como **TargetedSinglePlay** na pasta **Channels**.

* Adicione ativos relevantes a ambos os canais.

A imagem a seguir mostra o projeto **Ativação no Nível de Canal** com os canais **MainAdChannel** e **TargetedSinglePlay** na pasta **Channels**.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e criar um canal de sequência, consulte os seguintes recursos:
>
>* [Criação e gerenciamento de projetos](creating-a-screens-project.md)
>
>* [Gerenciando um Canal](managing-channels.md)
>

### Implementação {#implementation}

A implementação da Ativação no nível do canal em um projeto do AEM Screens envolve três tarefas principais:

1. **Configurando a taxonomia do projeto, incluindo Canais, Locais e Exibições**
1. **Atribuindo canais para exibição**
1. **Configurando um Agendamento e uma Prioridade**

Siga as etapas abaixo para implementar a funcionalidade:

1. **Criar um Local**

   Navegue até a pasta **Locais** do projeto do AEM Screens e crie um local como **Região**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para saber como criar um local, consulte **[Criação e Gerenciamento de Locais](managing-locations.md)**.

1. **Criar Exibição no Local**

   1. Navegue até **Ativação no Nível de Canal** > **Locais** > **Região**.
   1. Clique em **Região** e em **+ Criar** na barra de ações.
   1. Clique em **Exibir** no assistente e crie uma exibição chamada **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Atribuir canais para exibição**

   Para **MainAdChannel:**

   1. Navegue até **Ativação no Nível de Canal** > **Locais** > **Região** > **RegionDisplay** e clique em **Atribuir Canal** na barra de ações.
   1. Na caixa de diálogo **Atribuição de canal**, clique em **Canal de Referência** por caminho.
   1. Clique no **Caminho do Canal** e em **Ativação no Nível do Canal** > ***Canais*** > ***MainAdChannel***.
   1. A **Função de Canal** está populada como **mainadchannel**.
   1. Clique em **Prioridade** e defina como **1**.
   1. Clique nos **Eventos com Suporte**, como **Carregamento Inicial** e **Tela Inativa**.
   1. Clique em **Salvar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Você também pode atribuir o canal no painel de exibição. Navegue até **Ativação no Nível de Canal** > **Locais** > **Região** > **RegionDisplay**. Na barra de ações, selecione **Painel**. No painel **CANAIS ATRIBUÍDOS E AGENDAMENTOS**, clique em **+ Atribuir canal**.

   Da mesma forma, atribua o canal **TargetedSinglePlay** para exibição**:

   1. Navegue até **Ativação no Nível de Canal** > **Locais** > **Região** > **RegionDisplay** e clique em **Atribuir Canal** na barra de ações.
   1. Na caixa de diálogo **Atribuição de canal**, clique em **Canal de Referência** por caminho.
   1. Clique no **Caminho do Canal** e em **Ativação no Nível do Canal** > ***Canais*** > ***TargetedSinglePlay***.
   1. A **Função de Canal** está preenchida como **targetedsingleplay**.
   1. Defina a **Prioridade** como **2**.
   1. Clique em **Eventos com Suporte** e defina **Carregamento Inicial**, **Tela Inativa** e **Timer**, conforme mostrado na figura abaixo.
   1. No **ativo de**, definido como 27 de novembro de 2018, às 23h59, e no **ativo até**, definido como 28 de novembro de 2018, às 12h05.
   1. Clique em **Salvar**.

   >[!CAUTION]
   >
   >Defina a prioridade do canal **TargetedSinglePlay** como superior ao canal **MainAdSegment**.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Para escolher o mesmo dia, clique no dia seguinte e edite manualmente a data para o mesmo dia, mas para uma hora posterior. Isso restringe o usuário de selecionar uma data passada. Consulte o exemplo a seguir:

   ![novo1](assets/new1.gif)

## Exibir os resultados {#viewing-the-results}

Quando a configuração dos canais e a exibição estiverem concluídas, inicie o AEM Screens Player para visualizar o conteúdo.

O player exibe o conteúdo do **MainAdChannel** e exatamente às 23h59 (conforme definido no agendamento), o canal **TargetedSinglePlay** exibe seu conteúdo até às 12h05 e, em seguida, o **MainAdChannel** retoma a reprodução do conteúdo novamente.

>[!NOTE]
>
>Para saber mais sobre o AEM Screen Player, consulte os seguintes recursos:
>>[Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
>>[Trabalhando com o AEM Screens Player](working-with-screens-player.md)


## Manipulação de recorrência do Assets em um canal {#handling-recurrence-in-assets}

Você pode agendar ativos em um canal para recorrência em determinados intervalos diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseja exibir o conteúdo de um canal somente nas sextas-feiras, de 13h até 22h. Você pode usar a guia **Ativação** para definir o intervalo recorrente desejado para seu ativo.

### Divisão de dia {#day-parting}

1. Clique no canal e, em seguida, clique em **Painel** na barra de ações.

1. Depois de inserir a data/hora inicial e a data/hora final na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo até** e adicionar a expressão ao campo Agendamentos, de acordo com sua necessidade.

1. Insira a expressão no **Agendamento** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de Exemplo para Divisão de Dia {#example-one}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8h | o ativo no canal é reproduzido antes das 8h diariamente |
| depois das 14h | o ativo no canal é reproduzido depois das 14h todos os dias |
| após 12:15 e antes de 12:45 | o ativo no canal é reproduzido diariamente após as 12h15 por 30 minutos |
| antes de 12:15 também depois de 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45. |
| Seg, Ter, Qua ou Seg-Qua | o ativo é reproduzido no ativo no canal de segunda a quarta-feira |
| no primeiro dia de janeiro depois das 14h, também no segundo dia de janeiro e também no terceiro dia de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia de 2 de janeiro até as 3h de 3 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua a ser reproduzido até às 3h de 2º de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3º de janeiro |

>[!NOTE]
>
>Você também pode usar a notação _tempo militar_ (14:00) em vez de *A.M./P.M.* (14:00).

### WeekParting {#week-parting}

1. Clique no canal e, em seguida, clique em **Painel** na barra de ações.

1. Depois de inserir a data/hora inicial e a data/hora final na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo até** e adicionar a expressão ao campo Agendamentos, de acordo com sua necessidade.

1. Insira a expressão no **Agendamento** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para WeekParting {#example-two}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Seg, Ter, Qua ou Seg-Qua | o ativo é reproduzido no ativo no canal de segunda a quarta-feira |
| antes das 8h | o ativo no canal é reproduzido antes das 8h diariamente |
| depois das 14h | o ativo no canal é reproduzido depois das 14h todos os dias |
| após 12:15 e antes de 12:45 | o ativo no canal é reproduzido diariamente após as 12h15 por 30 minutos |
| antes de 12:15 também depois de 12:45 | o canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45. |

>[!NOTE]
>
>Você também pode usar a notação _tempo militar_ (14:00) em vez de *A.M./P.M.* (14:00).


### MonthParting {#month-parting}

1. Clique no canal e, em seguida, clique em **Painel** na barra de ações.

1. Depois de inserir a data/hora inicial e a data/hora final na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo até** e adicionar a expressão ao campo Agendamentos, de acordo com sua necessidade.

1. Insira a expressão no **Agendamento** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para MonthParting {#example-three}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de `February,May,August,November` | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |

>[!NOTE]
>
>Ao definir dias da semana e meses, você pode usar as notações abreviadas e de nome completo, como Seg/Segunda-feira e Jan/Janeiro.

>[!NOTE]
>
>Você também pode usar a notação _tempo militar_ (14:00) em vez de *A.M./P.M.* (14:00).

### Combinação de Peças {#combined-parting}

1. Clique no canal e, em seguida, clique em **Painel** na barra de ações.

1. Depois de inserir a data/hora inicial e a data/hora final na caixa de diálogo **Atribuição de canal**, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo até** e adicionar a expressão ao campo Agendamentos, de acordo com sua necessidade.

1. Insira a expressão no **Agendamento** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de Exemplo para Combinação de Parcelas {#example-four}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00 na segunda-feira, quarta-feira de janeiro-mar | o ativo é reproduzido no canal entre 6h e 18h, nas segundas e quartas-feiras de janeiro até o final de março |
| no primeiro dia de janeiro depois das 14h, também no segundo dia de janeiro e também no terceiro dia de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia de 2 de janeiro até as 3h de 3 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua a ser reproduzido até às 3h de 2º de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3º de janeiro |

>[!NOTE]
>
>Ao definir dias da semana e meses, você pode usar as notações abreviadas e de nome completo, como Seg/Segunda-feira e Jan/Janeiro. Além disso, você também pode usar a notação _tempo militar_ (14:00) em vez de *A.M./P.M.* (14:00).
