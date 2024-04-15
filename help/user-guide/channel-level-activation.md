---
title: Ativação no nível do canal - Reprodução de evento único
description: Saiba mais sobre a ativação no nível do canal usando a reprodução de evento único.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 1%

---

# Ativação em Nível de Canal {#channel-level-activation-single-event-playback}

Esta página descreve a ativação no nível do canal para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Utilização da Ativação no nível do canal como uma reprodução de evento único
* Lidar com a recorrência de ativos em um canal
   * DayParting
   * WeekParting
   * MonthParting
   * Combinação de Peças
* Utilização da Ativação no nível do canal como uma reprodução de evento único

## Visão geral {#overview}

***Ativação em Nível de Canal*** permite que os canais mudem após um cronograma definido específico. O canal de evento único substitui o canal principal após um agendamento definido e é reproduzido por um tempo específico, até que o canal principal reproduza seu conteúdo novamente.

O exemplo a seguir fornece uma solução com foco nos seguintes termos principais:

* a ***canal da sequência principal*** para a sequência global
* a ***canal de evento único*** que é executado apenas uma vez em um horário definido
* a ***definir cronograma e prioridade*** para o evento de reprodução única que ocorre dentro do canal da sequência principal

## Janela de ativação {#using-channel-level-activation}

A seção a seguir explica a criação de uma única reprodução de evento em um canal para um projeto do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem os seguintes pré-requisitos prontos para começar a implementar a ativação no nível do canal:

* Crie um projeto do AEM Screens, neste exemplo, **Ativação em Nível de Canal**

* Criar um canal como **MainAdChannel** em **Canais** pasta

* Criar outro canal como **TargetedSinglePlay** em **Canais** pasta

* Adicionar ativos relevantes a ambos os canais

A imagem a seguir mostra o **Ativação em Nível de Canal** projeto com **MainAdChannel** e **TargetedSinglePlay** canais em **Canais** pasta.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e criar um canal de sequência, consulte os seguintes recursos:
>
>* [Criação e gerenciamento de projetos](creating-a-screens-project.md)
>
>* [Gerenciamento de um canal](managing-channels.md)
>

### Implementação {#implementation}

A implementação da Ativação no nível do canal em um projeto do AEM Screens envolve três tarefas principais:

1. **Configurando a taxonomia do projeto incluindo canais, locais e exibições**
1. **Atribuição de canais para exibição**
1. **Configurando um Cronograma e Prioridade**

Siga as etapas abaixo para implementar a funcionalidade:

1. **Criar um local**

   Navegue até o **Localizações** pasta no projeto do AEM Screens e criar um local como **Região**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Para saber como criar um local, consulte **[Criação e Gerenciamento de Locais](managing-locations.md)**.

1. **Criar Exibição em Local**

   1. Navegue até **Ativação em Nível de Canal** > **Localizações** > **Região**.
   1. Selecionar **Região** e selecione **+ Criar** na barra de ações.
   1. Selecionar **Exibir** do assistente e crie uma exibição chamada de **Exibição de região.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Atribuir canais para exibição**

   Para **MainAdChannel:**

   1. Navegue até **Ativação em Nível de Canal** > **Localizações** > **Região** > **ExibiçãoRegião** e selecione **Atribuir canal** na barra de ações.
   1. **Atribuição de canal** é aberta.
   1. Selecionar **Canal de referência** por caminho.
   1. Selecione o **Caminho do canal** as **Ativação em Nível de Canal** > ***Canais*** > ***MainAdChannel***.
   1. A variável **Função do canal** é preenchido como **mainadchannel**.
   1. Selecione o **Prioridade** as **1**.
   1. Selecione o **Eventos suportados** as **Carga inicial** e **Tela inativa**.
   1. Selecione **Salvar**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Você também pode atribuir um canal no painel de exibição navegando até **Ativação em Nível de Canal** > **Localizações** > **Região** > **ExibiçãoRegião** e seleção **Painel** na barra de ações. Selecionar **+ Atribuir canal** do **CANAIS ATRIBUÍDOS E AGENDAMENTOS** painel.

   Da mesma forma, atribuir canal **TargetedSinglePlay** para exibição**:

   1. Navegue até **Ativação em Nível de Canal** > **Localizações** > **Região** > **ExibiçãoRegião** e selecione **Atribuir canal** na barra de ações.
   1. **Atribuição de canal** é aberta.
   1. Selecionar **Canal de referência** por caminho.
   1. Selecione o **Caminho do canal** as **Ativação em Nível de Canal*** > ***Canais*** > ***TargetedSinglePlay***.
   1. A variável **Função do canal** é preenchido como **targetedsingleplay**.
   1. Defina o **Prioridade** as **2**.
   1. Selecione o **Eventos suportados** as **Carga inicial**, **Tela inativa**, e **Temporizador**, conforme mostrado na figura abaixo.
   1. Escolha a data em **ativo desde** em 27 de novembro de 2018 às 23:59 e em **ativo até** em 28 de novembro de 2018 às 12h05
   1. Selecione **Salvar**.

   >[!CAUTION]
   >
   >Definir a prioridade de **TargetedSinglePlay** canal superior ao **SegmentoAnúncioPrincipal** canal.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Para escolher o mesmo dia, selecione o dia seguinte e edite manualmente a data para o mesmo dia, mas para uma hora posterior. Isso restringe o usuário de selecionar uma data passada. Consulte o exemplo a seguir:

   ![novo1](assets/new1.gif)

## Exibir os resultados {#viewing-the-results}

Quando a configuração dos canais e a exibição estiverem concluídas, inicie o reprodutor do AEM Screens para exibir o conteúdo.

O reprodutor exibe o conteúdo de **MainAdChannel** e exatamente às 23h59 (conforme definido no cronograma), o **TargetedSinglePlay** O canal exibe o conteúdo até 00:05 e depois o **MainAdChannel** O reinicia a reprodução do conteúdo novamente.

>[!NOTE]
>
>Para saber mais sobre o reprodutor de tela AEM, consulte os seguintes recursos:
>[Downloads do AEM Screens Player](https://download.macromedia.com/screens/)
>[Trabalhar com o AEM Screens Player](working-with-screens-player.md)


## Lidar com a recorrência de ativos em um canal {#handling-recurrence-in-assets}

Você pode agendar ativos em um canal para recorrência em determinados intervalos diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseja exibir o conteúdo de um canal somente nas sextas-feiras, de 13h até 22h. Você pode usar o **Ativação** para definir o intervalo recorrente desejado para o ativo.

### Divisão de dia {#day-parting}

1. Selecione o canal e **Painel** na barra de ações.

1. Após inserir a data/hora inicial e a data/hora final da **Atribuição de canal** você pode usar uma expressão ou uma versão de texto natural para especificar o cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

#### Expressões de Exemplo para Divisão de Dia {#example-one}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8h | o ativo no canal é reproduzido antes das 8h diariamente |
| depois das 14h | o ativo no canal é reproduzido depois das 14h todos os dias |
| após 12:15 e antes de 12:45 | o ativo no canal é reproduzido diariamente após as 12h15 por 30 minutos |
| antes de 12:15 também depois de 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45. |
| Seg, Ter, Qua ou Seg-Qua | o ativo é reproduzido no ativo no canal de segunda a quarta-feira |
| no primeiro dia de janeiro depois das 14h também no segundo dia de janeiro também no terceiro dia de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia de 2 de janeiro até as 3h de 3 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua a ser reproduzido até às 3h de 2º de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3º de janeiro |

>[!NOTE]
>
>Também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).

### WeekParting {#week-parting}

1. Selecione o canal e **Painel** na barra de ações.

1. Após inserir a data/hora inicial e a data/hora final da **Atribuição de canal** você pode usar uma expressão ou uma versão de texto natural para especificar o cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

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
>Também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).


### MonthParting {#month-parting}

1. Selecione o canal e **Painel** na barra de ações.

1. Após inserir a data/hora inicial e a data/hora final da **Atribuição de canal** você pode usar uma expressão ou uma versão de texto natural para especificar o cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

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
>Também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).

### Combinação de Peças {#combined-parting}

1. Selecione o canal e **Painel** na barra de ações.

1. Após inserir a data/hora inicial e a data/hora final da **Atribuição de canal** você pode usar uma expressão ou uma versão de texto natural para especificar o cronograma de recorrência.

   >[!NOTE]
   >
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

#### Expressões de Exemplo para Combinação de Parcelas {#example-four}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00 na segunda-feira, quarta-feira de janeiro-mar | o ativo é reproduzido no canal entre 6h e 18h nas segundas e quartas-feiras de janeiro ao final de março |
| no primeiro dia de janeiro depois das 14h também no segundo dia de janeiro também no terceiro dia de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia de 2 de janeiro até as 3h de 3 de janeiro |
| nos dias 1 a 2 de janeiro depois das 14h também nos dias 2 a 3 de janeiro antes das 3h. | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua a ser reproduzido até às 3h de 2º de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3º de janeiro |

>[!NOTE]
>
>Ao definir dias da semana e meses, você pode usar as notações abreviadas e de nome completo, como Seg/Segunda-feira e Jan/Janeiro. Além disso, também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).
