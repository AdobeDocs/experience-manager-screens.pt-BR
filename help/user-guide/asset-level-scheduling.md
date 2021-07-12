---
title: Ativação no nível do ativo
seo-title: Ativação no nível do ativo
description: Siga esta página para saber como ativar um ativo específico em um canal para um período agendado no fuso horário local do player.
seo-description: Siga esta página para saber como ativar um ativo específico em um canal para um período agendado no fuso horário local do player.
feature: Telas de criação, Ativação no nível de ativo
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 2%

---

# Ativação no nível do ativo {#asset-level-scheduling}

Esta página descreve a ativação no nível do ativo para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Reprodução de evento único
* Lidar com a recorrência em ativos
   * DayParting
   * Divisão de semana
   * MonthParting
   * Combinação de peças
* Ativação de vários ativos

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Feature Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

***Ativação no nível do ativo***, permite ativar um ativo específico em um canal para um período agendado no fuso horário local do player. Isso está disponível para imagens, vídeos, transições, páginas e canais incorporados (dinâmicos ou estáticos).

*Por exemplo*, você deseja que uma promoção especial seja exibida somente durante a hora feliz (das 2:00 às 17:00) nas segundas e quartas-feiras.

Com esse recurso, não somente é possível especificar a data e a hora de início e término, como também um padrão de recorrência.

## Janela de ativação {#single-event-playback}

A Ativação no nível do ativo é feita configurando a guia **Ativation** ao acessar as propriedades de um ativo.

Siga as etapas abaixo para executar a programação de nível de ativo:

1. Selecione qualquer canal e clique em **Editar** na barra de ações para adicionar ou editar conteúdo no seu canal.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Saiba mais detalhadamente sobre como
   >
   >* Crie um projeto, consulte [Criação de um novo projeto](creating-a-screens-project.md).
   >* Crie e adicione conteúdo a um canal, consulte [Gerenciar canais](managing-channels.md).


1. Clique em **Editar** para abrir o editor de canal e selecionar um ativo ao qual deseja aplicar a programação.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Selecione o ativo e clique no canto superior esquerdo **Configurar** (ícone de chave inglesa) para abrir as propriedades da imagem.

   Clique na guia **Ativation**.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Você pode especificar a data do seletor de datas usando os campos **Ativo de** e **Ativo até**.

   Se você selecionar **Ativo de** e **Ativo até** data e hora, o ativo será exibido e repetido somente entre a data/hora de início e a data/hora de término, respectivamente.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

## Lidar com a recorrência em ativos {#handling-recurrence-in-assets}

Você pode programar ativos para recorrência em determinados intervalos diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você deseja exibir uma imagem somente às sextas-feiras, das 13:00 às 22:00. Você pode usar a guia **Ativation** para definir o intervalo recorrente desejado para o ativo.

### Divisão de dia {#day-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora de início e a hora de término/data, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para divisão de dia {#example-one}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 AM todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |


>[!NOTE]
>
>Você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).

### Divisão de semana {#week-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora de início e a hora de término/data, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para WeekParting {#example-two}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Seg,Qua,Sex | o ativo é reproduzido no canal de segunda, quarta e sexta-feira |
| Mon-Thu | o ativo é reproduzido no canal de segunda a quinta-feira |

>[!NOTE]
>
>Você também pode usar a notação _full_ (ou seja, segunda-feira,quarta-feira,sexta-feira) em vez da notação _short-hand_ (ou seja, Mon,Wed,Fri).


### MonthParting {#month-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora de início e a hora de término/data, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para MonthParting {#example-three}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de fevereiro,maio,agosto,novembro | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |
| de fevereiro a julho | o ativo é reproduzido no canal de fevereiro até o final de julho |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.

### Combinação de peças {#combined-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave inglesa) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora de início e a hora de término/data, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Ignore ou inclua os campos **Ativo de** e **Ativo Até** e adicione a expressão ao campo Agendamentos, de acordo com seu requisito.

1. Insira a expressão no **Schedule** e o ativo será exibido para o intervalo específico de dia e hora.

#### Exemplo de expressões para combinação de partes {#example-four}

A tabela a seguir resume alguns exemplos de expressões que podem ser adicionadas ao agendamento, enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00, em Mon,Fim de Jan-Mar | o ativo é reproduzido no canal entre as 6h e as 18h das segundas e quartas-feiras, de janeiro a fim de março |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 3:00 | o ativo no canal começa a ser reproduzido depois das 14:00 em 1º de janeiro, continua reproduzindo o dia inteiro em 2 de janeiro até as 3:00 em 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 3:00 | o ativo no canal inicia o reprodutor depois das 14:00 PM no dia 1º de janeiro, continua reproduzindo até as 3:00 AM no dia 2 de janeiro, depois começa novamente no dia 2 de janeiro às 14:00 e continua reproduzindo até as 3:00 AM no dia 3 de janeiro |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notações de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.  Além disso, você também pode usar a notação _militar time_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00).


## Ativação de vários ativos {#multi-asset-scheduling}

>[!CAUTION]
>
>O recurso **Multi-asset Ativation** só estará disponível se tiver instalado AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

***A*** Ativação de vários ativos permite que o usuário selecione vários ativos e aplique um agendamento de reprodução a todos os ativos selecionados.

### Pré-requisitos {#prerequisites}

Para usar a ativação em nível de vários ativos para seus ativos, crie um projeto do AEM Screens com um canal de sequência. Por exemplo, o caso de uso a seguir mostra a implementação do recurso:

* Crie um projeto do AEM Screens chamado **MultiAssetDemo**
* Crie um canal chamado **MultiAssetChannel** e adicione conteúdo ao canal, conforme mostrado na figura abaixo

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga as etapas abaixo para selecionar vários ativos e agendar a exibição deles em um projeto do AEM Screens:

1. Selecione **MultiAssetChannel** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selecione vários ativos no editor e clique em **Editar ativação** (ícone superior esquerdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selecione a data e a hora em **Ativo de** e **Ativo até** na caixa de diálogo **Ativação de componente**. Clique no ícone de marca de seleção quando terminar de selecionar as programações.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Clique em atualizar para verificar os ativos aos quais a programação de vários ativos é aplicada.

   >[!NOTE]
   >
   >O ícone de agendamento é visível no canto superior direito dos ativos que têm ativação de vários ativos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)
