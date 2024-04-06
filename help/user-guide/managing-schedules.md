---
title: Criação e Gerenciamento de Agendamentos
description: Saiba mais sobre os Cronogramas que permitem organizar canais em grupos reutilizáveis para que você não precise repetir a atribuição individualmente para cada exibição na qual deseja mostrar o conteúdo.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Criação e Gerenciamento de Agendamentos {#creating-and-managing-schedules}

**Agendamentos** no AEM Screens, permitem organizar canais em grupos reutilizáveis para que não seja necessário repetir a atribuição individualmente para cada exibição na qual deseja mostrar o conteúdo.

Agendamentos quando combinados com ***DayParting***, permite definir um agendamento global com vários canais sendo executados em horários específicos do dia e reutilizar essa configuração para todas as exibições de uma só vez.

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3 Sites Feature Pack 1. Para obter acesso a este Feature Pack, entre em contato com o Suporte do Adobe e solicite acesso. Após ter as permissões necessárias, você pode baixá-lo do Compartilhamento de pacotes.

## Criação de uma programação {#creating-a-schedule}

Você pode criar um agendamento para o seu projeto do Screens que possa gerenciar todas as atividades do seu caso de uso.

Siga as etapas abaixo para criar um agendamento para seu canal:

1. Selecione o link Adobe Experience Manager (canto superior esquerdo) e, em seguida, Screens. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até o projeto do Screens e clique em **Agendamentos**.
1. Clique em **Criar** na barra de ações.
1. Selecionar **Agendar** do **Criar** e clique em **Próxima**.

1. Insira o **Nome** e **Título** e clique em **Criar**.

Você pode ver uma pasta de agendamento com o nome e o título designados em seu projeto.


## Visualizando painel {#viewing-dashboard}

Depois de criar a pasta de agendamentos no projeto, você pode exibir os detalhes no painel de agendamentos.

Siga as etapas abaixo para visualizar o painel de agendamento. O exemplo a seguir mostra o painel do `We.Retail` projeto:

1. Navegue até a **Agendamentos** pasta de Telas (exemplo, `We.Retail`) projeto.

   ![chlimage_1](assets/chlimage_1.png)

1. Selecionar **Painel** na barra de ações.

   É possível exibir três painéis diferentes, como **INFORMAÇÕES DA PROGRAMAÇÃO**, **CANAIS ATRIBUÍDOS**, e **EXIBIÇÕES ATRIBUÍDAS**.

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **Painel de Informações de Agendamento** Clique em Propriedades no canto superior direito do Painel INFORMAÇÕES DA PROGRAMAÇÃO para exibir/alterar as propriedades da programação.

   **Painel Canais atribuídos** Clique em +Atribuir canal no canto superior direito do painel CANAIS ATRIBUÍDOS para abrir a caixa de diálogo Atribuição de canal.

   **Painel Exibições atribuídas** Selecione qualquer uma das exibições no painel EXIBIÇÕES ATRIBUÍDAS para abrir o painel de exibição.
