---
title: Canal de emergência
description: Saiba mais sobre como criar e gerenciar um canal de emergência que o Autor de conteúdo pode alternar de um canal de sequência se houver uma pré-condição.
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Canal de emergência {#emergency-channel}

## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso. Ela enfatiza a criação e o gerenciamento de um canal de emergência que o Autor de conteúdo pode alternar de um canal de sequência, se houver uma pré-condição.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e Gerenciar Canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e Gerenciar Agendamentos](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Fluxo básico: configuração do projeto {#basic-flow-setting-up-the-project}

Siga as etapas abaixo para configurar um canal de emergência:

1. Crie um Projeto do AEM Screens chamado **EmergencyChannel**, como mostrado abaixo.

   >[!NOTE]
   >Para saber mais sobre como criar e gerenciar projetos no AEM Screens, consulte Criação de um projeto.

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **Criando um Canal de Sequência**

   1. Clique na pasta **Canais** e clique em **Criar**.

   1. Clique em **Canal de sequência** no assistente e crie o canal intitulado como **MainAdChannel**.

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **Adicionando conteúdo ao canal de sequência**

   1. Clique no canal **MainAdChannel**.
   1. Clique em **Editar** na barra de ações.
   1. Arraste e solte alguns ativos no canal.

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **Criando um Canal de Emergência**

   1. Clique na pasta **Channels**.
   1. Clique em **Criar**.
   1. Clique em **Canal de sequência** no assistente e crie o canal intitulado **Canal de emergência**.

   >[!NOTE]
   >
   >Normalmente, seu canal de emergência é adicionado ao projeto de produção pré-existente.

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **Adicionando conteúdo ao canal de emergência**

   1. Clique no canal (**Canal de emergência)**.
   1. Clique em **Editar** na barra de ações.
   1. Arraste e solte o ativo que deseja executar durante uma emergência no seu canal.

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **Criando um Local**

   1. Navegue até a pasta **Locais**.
   1. Clique em **Criar** na barra de ações e crie um local chamado **Armazenar** no assistente.

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **Criando exibições em sua localização**

   Navegue até seu local (**Armazenar**) e clique em **Criar** na barra de ações. Após o assistente, crie duas **Exibições** intituladas **StoreFront** e **StoreRear**.

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **Criando um Cronograma**

   1. Navegue até a pasta **Agendamentos**.
   1. Clique em **Criar** na barra de ações.
   1. Após o assistente, crie um agendamento denominado **StoreSchedule**.

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. Atribua as exibições ao seu cronograma e defina as prioridades

   1. Clique no agendamento **(StoreSchedule)** e clique em **Painel** na barra de ações.

   1. Clique em **+ Atribuir canal** no painel **CANAIS ATRIBUÍDOS**.

   1. Na caixa de diálogo **Atribuição de canal**:

      1. Clique no caminho para o **MainAdChannel**
      1. Defina a **Prioridade** como 2
      1. Defina os Eventos Suportados como **Carregamento Inicial** e **Tela Ociosa**.
      1. Clique em **Salvar**

      Da mesma forma, siga as mesmas etapas novamente para atribuir o **EmergencyChannel** e definir sua **Prioridade**.

   >[!NOTE]
   >
   >A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre tem prioridade sobre valores mais baixos.

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. Clique em **+ Atribuir canal** no painel **CANAIS ATRIBUÍDOS**.

1. Na caixa de diálogo **Atribuição de canal**:

   1. Clique no caminho para o **EmergencyChannel**
   1. Definir a **Prioridade** como 1

   1. Defina os Eventos Suportados como **Carregamento Inicial**, **Tela Ociosa** e **Interação do Usuário**

   1. Clique em **Salvar**

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   Você pode exibir os canais atribuídos no painel **StoreSchedule**.

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **Atribuindo agenda a cada exibição**

   1. Navegue até cada exibição, como **EmergencyChannel** > **Locais** > **Loja** >**StoreFront**.

   1. Clique em **Painel** na barra de ações.
   1. Clique em **...** no painel **CANAIS ATRIBUÍDOS e AGENDAMENTOS** e clique em **+Atribuir agendamento**.

   1. Clique no caminho para o Agendamento (por exemplo, aqui, **EmergencyChannel** > **Agendamentos** >**StoreSchedule**).

   1. Clique em **Salvar**.

   Você pode exibir o agendamento atribuído à exibição no painel **StoreSchedule**.
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **Registro do dispositivo**

   Conclua o processo de registro do dispositivo. Depois de se registrar, é possível exibir a seguinte saída no AEM Screens Player.

   ![novos30](assets/new30.gif)

## Alternar para o canal de emergência {#switching-to-emergency-channel}

Se houver uma emergência, execute as seguintes etapas:

1. Navegue até **EmergencyChannel** > **Agendas** > **StoreSchedule** e clique em **Dashboard** na barra de ações.

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. Clique no **EmergencyChannel** do painel **StoreSchedule** e clique em **Editar Atribuição**.

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. Atualize a **Prioridade** do **EmergencyChannel** para **3** na caixa de diálogo **Atribuição de canal** e clique em **Salvar**.

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. Quando a prioridade do canal é atualizada, todo o AEM Screens Player exibe o conteúdo **EmergencyChannel**.

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### Conclusão {#conclusion}

O **EmergencyChannel** continua a exibir seu conteúdo até que o Autor de Conteúdo redefina o Valor de Prioridade para 1.

Quando o Autor de Conteúdo receber as instruções de que a emergência foi resolvida, ele deverá atualizar a prioridade do **MainAdChannel**. Isso faz com que a reprodução normal seja retomada.
