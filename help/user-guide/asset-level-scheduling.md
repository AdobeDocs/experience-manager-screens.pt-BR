---
title: Ativação em nível de ativo
seo-title: Asset Level Activation
description: Siga esta página para saber como ativar um ativo específico em um canal para um período agendado no fuso horário local do reprodutor.
seo-description: Follow this page to learn how to activate a specific asset in a channel for a scheduled time frame in the player's local timezone.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: 939d078def133e0db0e61ec80167f496c65ade46
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

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

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3 Feature Pack 3 ou o AEM 6.4 Screens Feature Pack 1.
>
>Para obter acesso a este Feature Pack, entre em contato com o Suporte do Adobe e solicite acesso. Depois de ter permissões, você pode baixá-las do Compartilhamento de pacotes.

## Visão geral {#overview}

***Ativação em nível de ativo***, permite ativar um ativo específico em um canal para um período agendado no fuso horário local do reprodutor. Ele está disponível para imagens, vídeos, transições, páginas e canais incorporados (dinâmico ou estático).

*Por exemplo*, você deseja que uma promoção especial seja exibida somente durante o happy hour (das 14h às 17h) nas segundas e quartas-feiras.

Com esse recurso, é possível especificar não apenas a data e a hora de início e término, mas também um padrão de recorrência.

## Janela de ativação {#single-event-playback}

A ativação no nível do ativo é feita configurando o **Ativação** ao acessar as propriedades de um ativo.

Siga as etapas abaixo para executar a programação no nível do ativo:

1. Selecione qualquer canal e clique em **Editar** na barra de ações para adicionar ou editar conteúdo no seu canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para saber mais detalhes sobre como
   >
   >* Para criar um projeto, consulte [Criação de um novo projeto](creating-a-screens-project.md).
   >* Criar e adicionar conteúdo a um canal, consulte [Gerenciamento de canais](managing-channels.md).


1. Clique em **Editar** para abrir o editor de canal e selecionar um ativo ao qual deseja aplicar o agendamento.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Selecione o ativo e clique em no canto superior esquerdo **Configurar** (ícone de chave inglesa) para abrir as propriedades da imagem.

   Clique em **Ativação** guia.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Você pode especificar a data no seletor de datas usando **Ativo desde** e **Ativo até** campos.

   Se você selecionar a variável **Ativo desde** e **Ativo até** data e hora, o ativo será exibido e repetirá somente entre essa data/hora inicial e a data/hora final, respectivamente.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

## Lidar com a recorrência em ativos {#handling-recurrence-in-assets}

Você pode programar ativos para recorrência em determinados intervalos diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseja exibir uma imagem somente nas sextas-feiras, das 13h às 22h. Você pode usar o **Ativação** para definir o intervalo recorrente desejado para o ativo.

### Divisão de dia {#day-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo será exibido para o intervalo específico do dia e da hora.

#### Expressões de Exemplo para Divisão de Dia {#example-one}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8h | o ativo no canal é reproduzido antes das 8h todos os dias |
| depois das 14h | o ativo no canal é reproduzido depois das 14h todos os dias |
| depois de 12:15 e antes de 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes de 12:15 também depois de 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e também depois das 12h45 |


>[!NOTE]
>
>Também é possível usar _hora militar_ notação (ou seja, 14:00) em vez de *am/pm* (ou seja, 14h).

### WeekParting {#week-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo será exibido para o intervalo específico do dia e da hora.

#### Expressões de exemplo para WeekParting {#example-two}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Seg,Qua,Sex | o ativo é reproduzido no canal nas segundas, quartas e sextas-feiras |
| Seg a quinta | o ativo é reproduzido no canal de segunda a quinta-feira |

>[!NOTE]
>
>Também é possível usar _completo_ notação (ou seja, segunda, quarta, sexta) em vez de _mão curta_ notação (ou seja, seg, qua, sex).


### MonthParting {#month-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo será exibido para o intervalo específico do dia e da hora.

#### Expressões de exemplo para MonthParting {#example-three}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de fevereiro,maio,agosto,novembro | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |
| de fevereiro a julho | o ativo é reproduzido no canal de fevereiro até o final de julho |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações abreviada e de nome completo, como Seg/Segunda-feira e Jan/Janeiro.

### Combinação de Peças {#combined-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora inicial e a data/hora final, você pode usar uma expressão ou uma versão de texto natural para especificar seu cronograma de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir a variável **Ativo desde** e **Ativo até** e adicione a expressão ao campo Schedule, de acordo com sua necessidade.

1. Insira a expressão na variável **Agendar** e seu ativo será exibido para o intervalo específico do dia e da hora.

#### Expressões de Exemplo para Combinação de Parcelas {#example-four}

A tabela a seguir resume algumas expressões de exemplo que você pode adicionar ao agendamento ao atribuir um canal a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois de 6:00 e antes de 18:00 na segunda-feira,Qua de Jan-Mar | o ativo é reproduzido no canal entre 6h e 18h nas segundas e quartas-feiras de janeiro ao final de março |
| no primeiro dia de janeiro depois das 14h também no segundo dia de janeiro também no terceiro dia de janeiro antes das 3:00 am | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido todo o dia em 2 de janeiro até as 3h de 3º de janeiro |
| no dia 1-2 de janeiro depois das 14h também no dia 2-3 de janeiro antes das 3h | o ativo no canal começa a ser reproduzido depois das 14h de 1º de janeiro, continua sendo reproduzido até 3h de 2º de janeiro e, em seguida, começa novamente em 2º de janeiro às 14h e continua sendo reproduzido até 3h de 3º de janeiro |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações abreviada e de nome completo, como Seg/Segunda-feira e Jan/Janeiro.  Além disso, também é possível usar _hora militar_ notação (ou seja, 14:00) em vez de *am/pm* (ou seja, 14h).


## Ativação de vários ativos {#multi-asset-scheduling}

>[!CAUTION]
>
>A variável **Ativação de vários ativos** Este recurso só estará disponível se você tiver instalado o AEM 6.3 Feature Pack 5 ou o AEM 6.4 Feature Pack 3.

***Ativação de vários ativos*** O permite que o usuário selecione vários ativos e aplique uma programação de reprodução a todos os ativos selecionados.

### Pré-requisitos {#prerequisites}

Para usar a ativação em nível de vários ativos para seus ativos, crie um projeto do AEM Screens com um canal de sequência. Por exemplo, o caso de uso a seguir mostra a implementação do recurso:

* Crie um projeto do AEM Screens com o título **Demonstração de vários ativos**
* Crie um canal chamado como **Canal de vários ativos** e adicionar conteúdo ao canal, conforme mostrado na figura abaixo

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga as etapas abaixo para selecionar vários ativos e agendar sua exibição em um projeto do AEM Screens:

1. Selecionar **Canal de vários ativos** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selecione vários ativos no editor e clique em **Editar ativação** (ícone superior esquerdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selecione a data e a hora em **Ativo desde** e **Ativo até** do **Ativação de componente** caixa de diálogo. Clique no ícone de marca de seleção quando terminar de selecionar os cronogramas.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Clique em atualizar para verificar os ativos aos quais a programação de vários ativos é aplicada.

   >[!NOTE]
   >
   >O ícone de programação está visível no canto superior direito para os ativos que têm ativação de vários ativos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Substituição Global Para Hora De Início Universal {#global-override-scheduling}

***Substituição global para hora de início universal***, é uma configuração que permite que o autor de conteúdo defina a reprodução de uma imagem ou de um ativo de vídeo com base em um momento específico. A configuração de hora/fuso horário de qualquer player individual não é usada.

Normalmente, a reprodução é determinada pela hora local de qualquer player, mas com a substituição global, uma hora de início específica e universal pode ser usada para iniciar a reprodução do ativo.

Isso permite que o autor de conteúdo designe a reprodução de um ativo específico como ocorrendo em uma data/hora específica, independentemente do relógio local em todos os players com o conteúdo atribuído.

A Substituição Global para Horário de Início Universal é feita configurando o **Ativação** ao acessar as propriedades de um ativo. Siga as etapas abaixo para executar uma Sobreposição Global para a programação de ativos:

1. Selecione qualquer canal e clique em **Editar** na barra de ações para adicionar ou editar conteúdo no seu canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Clique em **Editar** para abrir o editor de canal e selecionar um ativo ao qual deseja aplicar o agendamento.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Para uma Substituição global, insira o horário de ativação na caixa **Substituição de fuso horário** para o ativo. Se você não inserir nada nesta área, o fuso horário aplicado será o fuso horário do reprodutor.


