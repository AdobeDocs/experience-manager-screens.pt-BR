---
title: Atualização de Conteúdo como um Serviço
description: Saiba mais sobre a Atualização de conteúdo como um serviço.
contentOwner: Jyotika syal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: de9f669b-9ce7-4d70-99b4-0b69ef3c1af5
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Atualização de Conteúdo como um Serviço {#content-update-as-a-service}

Esta seção aborda os seguintes tópicos sobre a atualização do conteúdo como um serviço:

* **Visão geral**
* **Usando Atualização Offline em Massa**

<!--
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission you can download it from Package Share. -->

## Visão geral {#overview}

A Atualização offline em massa permite atualizar todos os canais em massa. Isso evita o incômodo de navegar até um canal específico e atualizar o conteúdo. Em vez disso, você pode atualizar todo o conteúdo dos canais de um projeto específico em um instante.

Você também pode agendar essa atividade para um horário de tráfego de rede mais baixo.

>[!NOTE]
>
>O recurso Atualização offline em massa é otimizado para atualizar apenas os canais que foram modificados.

## Usando atualização off-line em massa {#using-bulk-offline-update}

Você pode usar manualmente a Atualização offline em massa na interface do usuário (UI) ou agendar a atualização em massa dos serviços OSGi.

### Utilização da interface do usuário do AEM Screens {#using-aem-screens-user-interface}

Siga as etapas abaixo para usar a atualização em massa offline para um projeto do AEM Screens:

1. Navegue até o projeto do AEM Screens.
1. Clique no projeto e em **Atualizar conteúdo offline** na barra de ações para atualizar o conteúdo do canal manualmente.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuração do console da Web do Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga as etapas abaixo para usar a atualização em massa offline para um projeto do AEM Screens:

1. Configuração do console da Web do Adobe Experience Manager.
1. Procurar serviços de Atualização Offline em massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Adicione as seguintes propriedades:

   **Caminho do projeto** - Especifica o caminho do seu projeto do AEM Screens. Normalmente, o caminho é `/content/screens/<Name of your project>`.

   *Por exemplo*, `/content/screens/we-retail`. Você pode encontrar esse caminho no URL selecionando qualquer projeto no AEM Screens (não clique no ícone ).

   >[!NOTE]
   >
   >Especifique o caminho do projeto relativo ao seu canal.

   **Frequência de Agendamento** - Especifica uma hora, por exemplo, 17:00 ou 17:00 em que esse serviço deve atualizar o conteúdo offline.

1. Clique em **Salvar** para poder salvar suas configurações. Todo o conteúdo é atualizado no horário especificado.
