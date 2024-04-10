---
title: Ativação em nível de ativo
description: Saiba como ativar um ativo específico em um canal para um período agendado no fuso horário local do reprodutor.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 1%

---

# Ativação em nível de ativo {#asset-level-scheduling}

Esta página descreve a ativação no nível do ativo para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Reprodução de evento único
* Lidar com a recorrência em ativos
   * DayParting
   * WeekParting
   * MonthParting
   * Combinação de Peças
* Ativação de vários ativos
* Substituição Global Para Hora De Início Universal

<!-- REFERS TO ARCHIVED VERSIONS THAT ADOBE NO LONGER SUPPORTS>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, you must contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## Visão geral {#overview}

***Ativação em nível de ativo*** permite ativar um ativo específico em um canal para um período agendado no fuso horário local do reprodutor. Ele está disponível para imagens, vídeos, transições, páginas e canais incorporados (dinâmico ou estático).

*Por exemplo*, você deseja que uma promoção especial seja exibida somente durante o happy hour (das 14h às 17h) nas segundas e quartas-feiras.

Com esse recurso, é possível especificar não apenas a data e a hora de início e término, mas também um padrão de recorrência.

## Janela de ativação {#single-event-playback}

A ativação no nível do ativo é feita configurando o **Ativação** ao acessar as propriedades de um ativo.

Siga as etapas abaixo para executar a programação no nível do ativo:

1. Selecione qualquer canal, depois selecione **Editar** na barra de ações.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para saber mais detalhes sobre como
   >
   >* Para criar um projeto, consulte [Criação de um novo projeto](creating-a-screens-project.md).
   >* Criar e adicionar conteúdo a um canal, consulte [Gerenciamento de canais](managing-channels.md).

1. Selecionar **Editar** para que você possa abrir o editor de canal e selecionar um ativo ao qual deseja aplicar o agendamento.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Selecione o ativo e, em seguida, selecione superior esquerdo **Configurar** (ícone de chave inglesa).

   Selecione o **Ativação** guia.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Você pode especificar a data no seletor de datas usando **Ativo desde** e **Ativo até** campos.

   Se você selecionar a variável **Ativo desde** e **Ativo até** data e hora, o ativo exibe e faz loop somente entre essa data/hora inicial e a data/hora final, respectivamente.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

## Lidar com a recorrência em ativos {#handling-recurrence-in-assets}

Você pode programar ativos para recorrência em determinados intervalos diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseje exibir uma imagem somente nas sextas-feiras, das 13h às 22h. Você pode usar o **Ativação** para definir o intervalo recorrente desejado para o ativo.

### Divisão de dia {#day-parting}

1. Selecione o ativo e selecione em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
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

>[!NOTE]
>
>Também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.* (14H).

### WeekParting {#week-parting}

1. Selecione o ativo e **Configurar** (ícone de chave inglesa).

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

#### Expressões de exemplo para WeekParting {#example-two}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| `Mon,Wed,Fri` | o ativo é reproduzido no canal nas segundas, quartas e sextas-feiras |
| `Mon-Thu` | o ativo é reproduzido no canal de segunda a quinta-feira |

>[!NOTE]
>
>Também é possível usar _completo_ notação (`Monday,Wednesday,Friday`) em vez de _mão curta_ (`Mon,Wed,Fri`).


### MonthParting {#month-parting}

1. Selecione o ativo e **Configurar** (ícone de chave inglesa).

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

#### Expressões de exemplo para MonthParting {#example-three}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| `on February,May,August,November` | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |
| `on February-July` | o ativo é reproduzido no canal de fevereiro ao final de julho |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações abreviadas e de nome completo, como Seg/Segunda-feira e Jan/Janeiro.

### Combinação de Peças {#combined-parting}

1. Selecione o ativo e **Configurar** (ícone de chave inglesa).

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo é exibido para o intervalo específico do dia e da hora.

#### Expressões de Exemplo para Combinação de Parcelas {#example-four}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | o ativo é reproduzido no canal entre 6h e 18h nas segundas e quartas-feiras de janeiro ao final de março |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia de 2 de janeiro até as 3h de 3 de janeiro |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua a ser reproduzido até às 3h de 2º de janeiro e, em seguida, recomeça em 2 de janeiro às 14h e continua a ser reproduzido até às 3h de 3º de janeiro |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações abreviadas e de nome completo, como Seg/Segunda-feira e Jan/Janeiro. Além disso, também é possível usar _hora militar_ notação (14:00) em vez de *A.M./P.M.*(14H).


## Ativação de vários ativos {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***Ativação de vários ativos*** permite que o usuário selecione vários ativos e aplique uma programação de reprodução a todos os ativos selecionados.

### Pré-requisitos {#prerequisites}

Para usar a ativação em nível de vários ativos para seus ativos, crie um projeto do AEM Screens com um canal de sequência. Por exemplo, o caso de uso a seguir mostra a implementação do recurso:

* Crie um projeto do AEM Screens com o título **Demonstração de vários ativos**.
* Crie um canal chamado como **Canal de vários ativos** e adicionar conteúdo ao canal, conforme mostrado na figura abaixo.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga as etapas abaixo para selecionar vários ativos e agendar sua exibição em um projeto do AEM Screens:

1. Selecionar **Canal de vários ativos** e selecione **Editar** na barra de ações.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selecione vários ativos no editor e selecione **Editar ativação** (ícone superior esquerdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selecione a data e a hora em **Ativo desde** e **Ativo até** do **Ativação de componente** caixa de diálogo. Selecione o ícone de marca de seleção quando terminar de selecionar as programações.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Selecione Atualizar para verificar os ativos aos quais o agendamento de vários ativos é aplicado.

   >[!NOTE]
   >
   >O ícone de programação está visível no canto superior direito para os ativos que têm ativação de vários ativos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Substituição Global Para Hora De Início Universal {#global-override-scheduling}

***Substituição global para hora de início universal***, é uma configuração que permite que o autor de conteúdo defina a reprodução de uma imagem ou de um ativo de vídeo com base em um momento específico. A configuração de hora/fuso horário de qualquer player individual não é usada.

Normalmente, a reprodução é determinada pela hora local de qualquer player, mas com a substituição global, uma hora de início específica e universal pode ser usada para iniciar a reprodução do ativo.

Isso permite que o autor de conteúdo designe a reprodução de um ativo específico como ocorrendo em uma data/hora específica, independentemente do relógio local em todos os players com o conteúdo atribuído.

A Substituição Global para Horário de Início Universal é feita configurando o **Ativação** ao acessar as propriedades de um ativo. Siga as etapas abaixo para executar uma Sobreposição Global para a programação de ativos:

1. Selecione qualquer canal, depois selecione **Editar** na barra de ações para que você possa adicionar ou editar o conteúdo no seu canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Selecione **Editar**.
1. No editor de canal, selecione um ativo cujo agendamento você deseja aplicar a ele.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Para uma Sobreposição Global, informe o horário de ativação na **Substituição de fuso horário** para o ativo. Se você não inserir nada nesta área, o fuso horário aplicado será o fuso horário do reprodutor.


