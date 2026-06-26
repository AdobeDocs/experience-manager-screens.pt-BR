---
title: Criação e Gerenciamento de Locais
description: Saiba mais sobre como criar e gerenciar locais relacionados ao AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 7935c206-7189-4243-9a2d-ccc322caf441
TQID: https://experienceleague.adobe.com/xu7NZILsH3YpmYOrI0XObYrLnkwjPENqBWQJSlhnTN4
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: d8a4be83-7d41-47be-b4a6-f8f3d35caceb
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 283
ht-degree: 1%

---

# Criação e Gerenciamento de Locais {#creating-and-managing-locations}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Os locais hospedam a configuração das exibições de acordo com o local em que as várias telas estão.

Esta página mostra como criar e gerenciar locais para o Screens.

**Pré-requisitos**:

* [Configuração e implantação do Screens](configuring-screens-introduction.md)
* [Criação e gerenciamento de projetos do Screens](creating-a-screens-project.md)
* [Criação e gerenciamento de canais](managing-channels.md)

## Criar um novo local {#creating-a-new-location}

Depois de criar seu projeto para o Screens, siga as etapas abaixo para criar um Local para um projeto do Screens:

1. Clique no link Adobe Experience Manager (canto superior esquerdo) e, em seguida, em Screens. Como alternativa, você pode navegar diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até o projeto do Screens e clique em **Locais**.
1. Clique em **Criar** ao lado do ícone de adição na barra de ações.
1. Clique no modelo **Local** no assistente e clique em **Avançar**.
1. Insira as propriedades para **Título e Marcas**, **Mais Títulos e Descrição**, **Horário Ligado/Desligado** e **URL Personalizada**.
1. Clique em **Criar** e o local será criado e adicionado à pasta de locais.

Consulte as etapas abaixo para entender a criação de um local para um projeto do AEM Screens. Para fins de demonstração, o novo local (SanJose) é criado em *DemoProject*.

![reprodutor2](assets/player2.gif)

Depois de criar um local, crie uma exibição para o seu local.

### Editando Propriedades de um Local {#editing-properties-for-a-location}

Para editar/acessar as propriedades de um local:

1. Clique no local.
1. Clique em **Propriedades** na barra de ações.

![player3](assets/player3.gif)

#### Próximas etapas {#the-next-steps}

Depois de criar um local, crie uma exibição para o seu local.

Consulte [Criação e gerenciamento de exibições](managing-displays.md).

