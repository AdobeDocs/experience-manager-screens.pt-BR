---
title: Ativação de nível de ativo
seo-title: Ativação de nível de ativo
description: Siga esta página para saber como ativar um ativo específico em um canal por um período programado no fuso horário local do player.
seo-description: Siga esta página para saber como ativar um ativo específico em um canal por um período programado no fuso horário local do player.
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 2%

---


# Ativação de nível de ativo {#asset-level-scheduling}

Esta página descreve a ativação no nível do ativo para os ativos usados em Canais.

Os seguintes tópicos são abordados nesta seção:

* Visão geral
* Janela de ativação
* Reprodução de Evento único
* Tratamento de recorrência em ativos
   * DayParting
   * WeekParting
   * MonthParting
   * Combinação de peças
* Ativação de vários ativos

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

***Ativação*** de nível de ativo, permite ativar um ativo específico em um canal por um período programado no fuso horário local do player. Isso está disponível para imagens, vídeos, transições, páginas e canais incorporados (dinâmicos ou estáticos).

*Por exemplo*, você deseja que uma promoção especial seja exibida somente durante a hora de felicidade (de 2h às 5h) nas segundas e quartas-feiras.

Com esse recurso, não somente você pode especificar o start e a data e hora de término, como também um padrão de recorrência.

## Janela de ativação {#single-event-playback}

A Ativação de nível de ativo é feita configurando a guia **Ativação** ao acessar as propriedades de um ativo.

Siga as etapas abaixo para executar a programação de nível de ativos:

1. Selecione qualquer canal e clique em **Editar** na barra de ações para adicionar ou editar conteúdo no canal.

   ![screen_shot_2018-04-23at111422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Para saber mais detalhes sobre como
   >
   >* Crie um projeto, consulte [Criando um novo Projeto](creating-a-screens-project.md).
   >* Crie e adicione conteúdo a um canal, consulte [Gerenciando Canais](managing-channels.md).


1. Clique em **Editar** para abrir o editor de canais e selecionar um ativo ao qual deseja aplicar o agendamento.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Selecione o ativo e clique no canto superior esquerdo **Configurar** (ícone de chave) para abrir as propriedades da imagem.

   Clique na guia **Ativação**.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Você pode especificar a data do seletor de datas usando os campos **Ativo de** e **Ativo até**.

   Se você selecionar **Ativo de** e **Ativo até** data e hora, o ativo exibirá e fará loop apenas entre a data/hora do start e a data/hora de término, respectivamente.

   ![imagem](/help/user-guide/assets/asset-activation/asset-level3.png)

## Tratamento de recorrência em ativos {#handling-recurrence-in-assets}

Você pode programar a recorrência de ativos em determinados intervalos, diariamente, semanalmente ou mensalmente, de acordo com sua necessidade.

Suponha que você queira exibir uma imagem somente às sextas-feiras das 13:00 às 10:00 horas. Você pode usar a guia **Ativação** para definir o intervalo recorrente desejado para seu ativo.

### Partilha de Dia {#day-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora e a hora de término/data do start, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo Até** e adicionar a expressão ao campo Programações, conforme seu requisito.

1. Insira a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para Programação de Dias {#example-one}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| antes das 8:00 | o ativo no canal é reproduzido antes das 8:00 da manhã todos os dias |
| depois das 14:00 | o ativo no canal é reproduzido depois das 14:00 horas todos os dias |
| depois das 12:15 e antes das 12:45 | o ativo no canal é reproduzido depois das 12h15 todos os dias por 30 minutos |
| antes das 12:15 também depois das 12:45 | o ativo no canal é reproduzido antes das 12h15 todos os dias e depois também depois das 12h45 |


>[!NOTE]
>
>Você também pode usar a notação _militar_ (isto é, 14:00) em vez da notação *am/pm* (isto é, 14:00 horas).

### WeekParting {#week-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora e a hora de término/data do start, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo Até** e adicionar a expressão ao campo Programações, conforme seu requisito.

1. Insira a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para WeekParting {#example-two}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| Seg,Qua,Sex | o ativo é reproduzido no canal de segunda, quarta e sexta-feira |
| Mon-Thu | o ativo é reproduzido no canal de segunda a quinta |

>[!NOTE]
>
>Você também pode usar a notação _full_ (isto é, segunda-feira,quarta-feira,sexta-feira) em vez da notação _short-hand_ (isto é, Mon,Wed,Sex).


### MonthParting {#month-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora e a hora de término/data do start, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo Até** e adicionar a expressão ao campo Programações, conforme seu requisito.

1. Insira a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para MonthParting {#example-three}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| de fevereiro,maio,agosto,novembro | o ativo é reproduzido no canal em fevereiro, maio, agosto e novembro |
| de fevereiro a julho | o ativo é reproduzido no canal de fevereiro até o final de julho |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notas de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.

### Combinação de peças {#combined-parting}

1. Selecione o ativo e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo de propriedades.

1. Depois de inserir a data/hora e a hora de término/data do start, você pode usar uma expressão ou uma versão de texto natural para especificar a programação de recorrência.

   >[!NOTE]
   >Você pode ignorar ou incluir os campos **Ativo de** e **Ativo Até** e adicionar a expressão ao campo Programações, conforme seu requisito.

1. Insira a expressão na **Programação** e seu ativo será exibido para o intervalo específico de dia e hora.

#### Expressões de exemplo para combinação de partições {#example-four}

A tabela a seguir resume algumas expressões de exemplo que podem ser adicionadas ao agendamento enquanto o canal é atribuído a uma exibição.

| **Expressão** | **Interpretação** |
|---|---|
| depois das 6:00 e antes das 18:00 em Lua,Qua de Jan-Mar | o ativo é reproduzido no canal entre as 18h e as 18h de segunda e quarta-feira, de janeiro a fim de março |
| no primeiro dia de janeiro depois das 14:00 também no dia 2 de janeiro também no dia 3 de janeiro antes das 15:00 | o ativo nos start do canal reproduzindo depois das 14:00 em 1º de janeiro, continua reproduzindo o dia inteiro em 2º de janeiro até as 15:00 em 3 de janeiro |
| no dia 1-2 de janeiro depois das 14:00 também no dia 2-3 de janeiro antes das 15:00 | o ativo no player de start de canais depois das 14:00 horas de 1º de janeiro, continua sendo reproduzido até as 15:00 da manhã de 2º de janeiro, depois start novamente em 2º de janeiro às 14:00 e continua sendo reproduzido até as 15:00 da manhã de 3 de janeiro |

>[!NOTE]
>Ao definir dias da semana e meses, você pode usar as notas de mão curta e de nome completo, como Mon/Segunda e Jan/Janeiro.  Além disso, você também pode usar a notação _militar_ (ou seja, 14:00) em vez da notação *am/pm* (ou seja, 14:00 horas).


## Ativação de vários ativos {#multi-asset-scheduling}

>[!CAUTION]
>
>O recurso **Ativação de vários ativos** só estará disponível se você tiver instalado AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

***A*** Ativação de vários ativos permite que o usuário selecione vários ativos e aplique um cronograma de reprodução a todos os ativos selecionados.

### Pré-requisitos {#prerequisites}

Para usar a ativação de nível de vários ativos para seus ativos, crie um projeto AEM Screens com um canal de sequência. Por exemplo, o caso de uso a seguir mostra a implementação do recurso:

* Crie um projeto da AEM Screens chamado **MultiAssetDemo**
* Crie um canal chamado **MultiAssetChannel** e adicione conteúdo ao canal, como mostrado na figura abaixo

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Siga as etapas abaixo para selecionar vários ativos e agendar sua exibição em um projeto da AEM Screens:

1. Selecione **MultiAssetChannel** e clique em **Editar** na barra de ações para abrir o editor.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Selecione vários ativos no editor e clique em **Editar Ativação** (ícone superior esquerdo).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Selecione a data e a hora em **Ativa de** e **Ativa até** na caixa de diálogo **Ativação de componentes**. Clique no ícone da marca de seleção quando terminar de selecionar os agendamentos.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Clique em atualizar para verificar os ativos aos quais a programação de vários ativos é aplicada.

   >[!NOTE]
   >
   >O ícone de programação fica visível no canto superior direito para os ativos que têm ativação de vários ativos.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

