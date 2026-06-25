---
title: Criar e gerenciar cronogramas
description: Saiba mais sobre os cronogramas que permitem organizar canais em grupos reutilizáveis para que você não precise repetir as atribuições individualmente.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
TQID: https://experienceleague.adobe.com/FJomd-Wz-r8vJZK7PH6wgL4LY3zRmOucBhIbTdjUmQ4
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: cf6d61d1-acb6-4411-ad1b-25fb57e94db6
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 0%

---

# Criar e gerenciar agendas {#creating-and-managing-schedules}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

**Calendários** no AEM Screens permitem organizar canais em grupos reutilizáveis. Isso significa que não é necessário repetir a atribuição individualmente para cada exibição na qual deseja mostrar o conteúdo.

O agendamento, quando combinado com ***DayParting***, permite que você defina um agendamento global com vários canais em execução em horários específicos do dia e reutilize essa configuração para todas as suas exibições de uma só vez.

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3 Sites Feature Pack 1. Para obter acesso a este Feature Pack, entre em contato com o Suporte da Adobe e solicite acesso. Após ter as permissões necessárias, você pode baixá-lo do Compartilhamento de pacotes.

## Criar um agendamento {#creating-a-schedule}

Você pode criar um agendamento para o seu projeto do Screens que possa gerenciar todas as atividades do seu caso de uso.

Siga as etapas abaixo para criar um agendamento para seu canal:

1. Clique no link Adobe Experience Manager (canto superior esquerdo) e, em seguida, em Screens. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até o projeto do Screens e clique em **Agendamentos**.
1. Clique em **Criar** na barra de ações.
1. Clique em **Agendar** no assistente **Criar** e clique em **Avançar**.

1. Insira o **Nome** e o **Título** e clique em **Criar**.

Você pode ver uma pasta de agendamento com o nome e o título designados em seu projeto.


## Exibir painel {#viewing-dashboard}

Depois de criar uma pasta de agendamentos no projeto, você pode exibir os detalhes no painel de agendamentos.

Siga as etapas abaixo para visualizar o painel de agendamento. O exemplo a seguir mostra o painel do projeto `We.Retail`:

1. Navegue até a pasta **Agendamentos** do projeto Screens (exemplo, `We.Retail`).

   ![chlimage_1](assets/chlimage_1.png)

1. Clique em **Painel** na barra de ações.

   Você pode exibir três painéis diferentes, como **INFORMAÇÕES DE AGENDAMENTO**, **CANAIS ATRIBUÍDOS** e **EXIBIÇÕES ATRIBUÍDAS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Painel de Informações de Agendamento** - Clique em Propriedades no canto superior direito do Painel de INFORMAÇÕES DE AGENDAMENTO para exibir/alterar as propriedades do agendamento.

   **Painel Canais atribuídos** - Clique em +Atribuir canal no canto superior direito do painel CANAIS ATRIBUÍDOS para abrir a caixa de diálogo Atribuição de canal.

   **Painel Exibições Atribuídas** - Clique em qualquer exibição do Painel EXIBIÇÕES ATRIBUÍDAS para abrir o painel de exibição.
