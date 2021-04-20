---
title: Atualização de conteúdo como um serviço
seo-title: Atualização de conteúdo como um serviço
description: Siga esta página para saber mais sobre a Atualização de conteúdo como um serviço.
seo-description: Siga esta página para saber mais sobre a Atualização de conteúdo como um serviço.
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
feature: Authoring Screens
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 8%

---


# Atualização de conteúdo como um serviço {#content-update-as-a-service}

Esta seção aborda os seguintes tópicos sobre atualização de conteúdo como um serviço:

* **Visão geral**
* **Como usar a atualização em massa off-line**

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Feature Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

Atualização offline em massa, permite atualizar todo o canal em massa. Evita a inconveniência de navegar para um canal específico e atualizar o conteúdo. Em vez disso, você pode atualizar todo o conteúdo nos canais de um projeto específico em um instante.

Também é possível agendar essa atividade por um tempo de tráfego de rede menor.

>[!NOTE]
>
>O recurso Atualização offline em massa é otimizado para atualizar apenas os canais que foram modificados.

## Usando a atualização offline em massa {#using-bulk-offline-update}

Você pode usar manualmente a atualização offline em massa na interface do usuário ou agendar a atualização em massa dos serviços OSGi.

### Usando a interface do usuário do AEM Screens {#using-aem-screens-user-interface}

Siga as etapas abaixo para usar a atualização offline em massa para um projeto do AEM Screens:

1. Navegue até o projeto do AEM Screens.
1. Selecione o projeto e clique em **Atualizar conteúdo offline** na barra de ações para atualizar manualmente o conteúdo do canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuração do Console Web do Adobe Experience Manager {#adobe-experience-manager-web-console-configuration}

Siga as etapas abaixo para usar a atualização offline em massa para um projeto do AEM Screens:

1. Configuração do Console da Web do Adobe Experience Manager.
1. Procurar serviços de atualização offline em massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Adicione as seguintes propriedades:

   **Caminho** do projetoEspecifique o caminho do seu projeto do AEM Screens. Normalmente, o caminho é `/content/screens/<Name of your project>`.

   *Por exemplo*, `/content/screens/we-retail`. Você pode encontrar esse caminho no URL selecionando qualquer projeto no AEM Screens (não clique no ícone ).

   >[!NOTE]
   >
   >Especifique o caminho do projeto em relação ao seu canal.

   **Agendar** frequênciaEspecifique uma hora, por exemplo, 17:00 ou 17:00, em que este serviço deve atualizar o conteúdo offline.

1. Clique em **Salvar** para salvar suas configurações e seu conteúdo será atualizado no horário especificado.

