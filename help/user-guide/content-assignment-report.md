---
title: Relatório de atribuição de conteúdo
description: Saiba mais sobre o download e o uso do Relatório de atribuição de conteúdo relacionado ao AEM Screens.
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
TQID: https://experienceleague.adobe.com/Pwq3ebRrbCufXFMk7R-FJj90xq4b7gLOcLvslch2L5o
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 397
ht-degree: 2%

---

# Relatório de atribuição de conteúdo {#content-assignment-report}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

O recurso Relatório de atribuição de conteúdo permite que um administrador ou autor do AEM Screens exporte um *Relatório de atribuição de conteúdo* em formato de planilha.

## Uso do relatório de atribuição de conteúdo {#using-content-assignment-report}

O Relatório de atribuição de conteúdo permite que um autor do AEM Screens ou um administrador baixe o relatório que contém todos os ativos, como imagens, vídeos em todos os canais criados em um projeto do AEM Screens. Além disso, inclui as informações de todos os canais atribuídos a todas as exibições designadas e, de agora em diante, todos os dispositivos atribuídos a suas exibições designadas.

O Relatório de atribuição de conteúdo não só permite uma pré-visualização de todos os canais, Assets, exibições e dispositivos no projeto AEM Screens selecionado, como também fornece uma estrutura de alto nível do seu projeto.


### Pré-requisitos {#pre-reqs}

Antes de baixar o Relatório de atribuição de conteúdo, configure um projeto do AEM Screens com canais, locais e dispositivos.
Consulte os seguintes recursos para obter mais detalhes:

1. [Criação e gerenciamento de projetos](/help/user-guide/creating-a-screens-project.md)
1. [Criação e gerenciamento de canais](/help/user-guide/managing-channels.md)
1. [Criação e Gerenciamento de Locais](/help/user-guide/managing-locations.md)
1. [Criando e Gerenciando Exibições](/help/user-guide/managing-displays.md)
1. [Criando dispositivos](/help/user-guide/managing-devices.md)
1. [Atribuição de canais](/help/user-guide/channel-assignment-latest-fp.md)


## Baixar o relatório de atribuição de conteúdo {#downloading-content-assignment-report-fp}

Quando você tiver configurado seu projeto do AEM Screens e tiver atribuído exibições a cada um dos locais como mostrado nas etapas anteriores, baixe o Relatório de atribuição de conteúdo.

>[!NOTE]
>O recurso Relatório de atribuição de conteúdo só pode ser acessado no nível do projeto.

Siga as instruções abaixo para baixar o Relatório de atribuição de conteúdo:

1. Navegue até o projeto do AEM Screens e clique no projeto **DemoScreens**.

1. Clique em **Relatório de atribuição de conteúdo** na barra de ações.

   ![imagem](/help/user-guide/assets/content-assignment-report/can-download.png)

1. A planilha baixada consiste em duas guias, como **Locais** e **Conteúdo**. A guia Local exibe quatro colunas, como **Locais**, **Exibições**, **Canais** e **Dispositivos**, que podem ser usadas para investigar essas quatro entidades pertencentes ao seu projeto do AEM Screens.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >Os dados exibidos na planilha são classificados em ordem alfabética em um formato fácil de ler.

1. Selecionar qualquer um dos canais na coluna **Canais** abre a guia **Conteúdo**. Por sua vez, ele navega diretamente para esse canal e fornece informações sobre ativos (imagens e vídeos) associados a esse canal específico.

   ![imagem](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
