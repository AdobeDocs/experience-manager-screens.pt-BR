---
title: Atualização de Conteúdo como um Serviço
seo-title: Content Update As a Service
description: Siga esta página para saber mais sobre a Atualização de conteúdo como um serviço.
seo-description: Follow this page to learn about Content Update As a Service.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Atualização de Conteúdo como um Serviço {#content-update-as-a-service}

Esta seção aborda os seguintes tópicos sobre a atualização do conteúdo como um serviço:

* **Visão geral**
* **Usando atualização off-line em massa**

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3 Feature Pack 3 ou o AEM 6.4 Screens Feature Pack 1.
>
>Para obter acesso a este Feature Pack, entre em contato com o Suporte do Adobe e solicite acesso. Depois de ter permissões, você pode baixá-las do Compartilhamento de pacotes.

## Visão geral {#overview}

Atualização offline em massa, permite atualizar todos os canais em massa. Isso evita o incômodo de navegar até um canal específico e atualizar o conteúdo. Em vez disso, você pode atualizar todo o conteúdo dos canais de um projeto específico em um instante.

Você também pode agendar essa atividade para um horário de tráfego de rede mais baixo.

>[!NOTE]
>
>O recurso Atualização offline em massa é otimizado para atualizar apenas os canais que foram modificados.

## Usando atualização off-line em massa {#using-bulk-offline-update}

Você pode usar a atualização offline em massa manualmente na interface do usuário ou agendar a atualização em massa dos serviços OSGi.

### Utilização da interface do usuário do AEM Screens {#using-aem-screens-user-interface}

Siga as etapas abaixo para usar a atualização em massa offline para um projeto do AEM Screens:

1. Navegue até o projeto do AEM Screens.
1. Selecione o projeto e clique em **Atualizar conteúdo offline** na barra de ações para atualizar manualmente o conteúdo do canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuração do console da Web do Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga as etapas abaixo para usar a atualização em massa offline para um projeto do AEM Screens:

1. Configuração do console da Web do Adobe Experience Manager.
1. Procurar serviços de atualização offline em massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Adicione as seguintes propriedades:

   **Caminho do projeto** Especifique o caminho do projeto do AEM Screens. Normalmente, o caminho é `/content/screens/<Name of your project>`.

   *Por exemplo*, `/content/screens/we-retail`. Você pode encontrar esse caminho no URL selecionando qualquer projeto no AEM Screens (não clique no ícone ).

   >[!NOTE]
   >
   >Especifique o caminho do projeto relativo ao seu canal.

   **Frequência de programação** Especifique um horário, por exemplo, 17h ou 17h, em que esse serviço deve atualizar o conteúdo offline.

1. Clique em **Salvar** para salvar as configurações e o conteúdo será atualizado no horário especificado.
