---
title: Canal de emergência
seo-title: Emergency Channel
description: Siga este exemplo de caso de uso para saber mais sobre como criar e gerenciar um canal de emergência que o autor de conteúdo pode trocar de um canal de sequência em caso de uma pré-condição.
seo-description: Follow this use case example to learn about creating and managing an emergency channel that the content author can switch from a sequence channel in case of a precondition.
uuid: 612917c9-a832-453b-970c-f4365f7b105d
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: dbb4fae6-f3fb-496a-9bd6-1151e2862b5b
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# Canal de emergência {#emergency-channel}

## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza a criação e o gerenciamento de um canal de emergência que o autor de conteúdo pode trocar de um canal de sequência em caso de uma pré-condição.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e gerenciar cronogramas](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Fluxo básico: configuração do projeto {#basic-flow-setting-up-the-project}

Siga as etapas abaixo para configurar um canal de emergência:

1. Crie um projeto do AEM Screens chamado como **EmergencyChannel**, conforme mostrado abaixo.

   >[!NOTE]
   >Para saber mais sobre como criar e gerenciar projetos no AEM Screens, consulte Criação de um projeto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Criação de um canal de sequência**

   1. Selecione o **Canais** e clique em **Criar** para abrir o assistente e criar um canal.

   1. Selecionar **Canal de sequência** do assistente e crie o canal chamado de **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Adicionar conteúdo ao canal de sequência**

   1. Selecione o canal (**MainAdChannel**).
   1. Clique em **Editar** na barra de ações para abrir o editor. Arraste e solte alguns ativos no seu canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Criação de um canal de emergência**

   1. Selecione o **Canais** pasta.
   1. Clique em **Criar** para abrir o assistente e criar um canal.
   1. Selecionar **Canal de sequência** do assistente e crie o canal chamado de **EmergencyChannel**.

   >[!NOTE]
   >
   >Normalmente, seu canal de emergência é adicionado ao projeto de produção pré-existente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Adicionar conteúdo ao canal de emergência**

   1. Selecione o canal (**Canal de emergência)**.
   1. Clique em **Editar** na barra de ações para abrir o editor. Arraste e solte o ativo que deseja executar durante uma emergência para o seu canal.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Criação de um local**

   1. Navegue até **Localizações** pasta.
   1. Clique em **Criar** na barra de ações e crie um local chamado **Loja** do assistente.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Criação de exibições em seu local**

   Navegue até sua localização (**Loja**) e clique em **Criar** na barra de ações. Siga o assistente para criar dois **Exibições** intitulado como **StoreFront** e **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Criação de uma programação**

   1. Navegue até o **Agendamentos** pasta.
   1. Clique em **Criar** na barra de ações. Siga o assistente para criar um agendamento chamado como **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Atribua as exibições ao seu cronograma e defina as prioridades

   1. Selecionar a programação **(StoreSchedule)** e clique em **Painel** na barra de ações.

   1. Clique em **+ Atribuir canal** do **CANAIS ATRIBUÍDOS** painel.

   1. No **Atribuição de canal** caixa de diálogo:

      1. Selecione o caminho para o **MainAdChannel**
      1. Defina o **Prioridade** as 2
      1. Defina os Eventos compatíveis como **Carga inicial** e **Tela inativa**.
      1. Clique em **Salvar**

      Da mesma forma, será necessário seguir as mesmas etapas novamente para atribuir a **EmergencyChannel** e defina seus **Prioridade**.

   >[!NOTE]
   >
   >A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre terá precedência sobre os valores mais baixos.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Clique em **+ Atribuir canal** do **CANAIS ATRIBUÍDOS** painel.

1. No **Atribuição de canal** caixa de diálogo:

   1. Selecione o caminho para o **EmergencyChannel**
   1. Defina o **Prioridade** as 1

   1. Defina os Eventos compatíveis como **Carga inicial**, **Tela inativa**, e **Interação do usuário**

   1. Clique em **Salvar**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   É possível visualizar os canais atribuídos na **StoreSchedule** painel.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Atribuindo programação a cada exibição**

   1. Navegue até cada exibição, como **EmergencyChannel** > **Localizações** > **Loja** >**StoreFront**.

   1. Clique em **Painel** na ação para abrir o painel de exibição.
   1. Clique em **..** do **CANAIS ATRIBUÍDOS E AGENDAMENTOS** e clique em **+Atribuir Calendário**.

   1. Selecione o caminho para a Programação (por exemplo, aqui, **EmergencyChannel** > **Agendamentos** >**StoreSchedule**).

   1. Clique em **Salvar**.

   Você pode exibir a programação atribuída à exibição na **StoreSchedule** painel.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registro do dispositivo**

   Conclua o processo de registro do dispositivo e, depois de registrar, você visualizará a seguinte saída no AEM Screens player.

   ![novo30](assets/new30.gif)

## Alternar para o canal de emergência {#switching-to-emergency-channel}

No caso de uma emergência, execute as seguintes etapas:

1. Navegue até **EmergencyChannel** > **Agendamentos** > **StoreSchedule** e selecione **Painel** na barra de ações.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Selecione o **EmergencyChannel** do **StoreSchedule** e clique em **Editar atribuição**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Atualize o **Prioridade** do **EmergencyChannel** para **3** do **Atribuição de canal** e clique em **Salvar**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Assim que a prioridade do canal for atualizada, todo o reprodutor de AEM Screens exibirá a variável **EmergencyChannel** conteúdo, conforme mostrado abaixo.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusão {#conclusion}

A variável **EmergencyChannel** O continuará a exibir seu conteúdo até que o autor de conteúdo redefina o Valor de prioridade como 1.

Depois que o autor do conteúdo receber as instruções de que a emergência foi resolvida, ele deve atualizar a prioridade do **MainAdChannel** que fará com que a reprodução normal seja retomada.
