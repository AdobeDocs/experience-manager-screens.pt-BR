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
source-git-commit: 1dbbe62875cdc1a0c1c7d5fe45221d7ebd12207f

---


# Ativação de nível de canal {#channel-level-activation-single-event-playback}

O uso da Ativação de nível de canal aborda os seguintes tópicos:

* Visão geral
* Usando a ativação de nível de canal como uma reprodução de evento único

## Visão geral {#overview}

***A Ativação*** de nível de canal permite que os canais alternem após uma programação definida específica. O canal de evento único substitui o canal principal após um agendamento definido e é reproduzido por um determinado tempo, até que o canal principal reproduza seu conteúdo novamente.

O exemplo a seguir fornece uma solução focando nos seguintes termos principais:

* um canal ***de sequência*** principal para a sequência global
* um canal ***de evento*** único que é executado somente uma vez em um horário definido
* um cronograma ***definido e prioridade*** para o evento de reprodução única que ocorre dentro do canal da sequência principal

## Usando a ativação de nível de canal {#using-channel-level-activation}

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

