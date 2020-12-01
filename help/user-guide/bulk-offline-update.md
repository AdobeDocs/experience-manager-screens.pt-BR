---
title: Atualização em massa off-line
seo-title: Atualização em massa off-line
description: Siga esta página para saber como atualizar todos os canais em massa.
seo-description: Siga esta página para saber como atualizar todos os canais em massa.
uuid: 9b52c5e7-aa6d-4f55-b23c-8bd923723552
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 5d4ca652-d918-4b2b-b239-a2be9255ef0d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 8%

---


# Atualização em massa offline {#bulk-offline-update}

Esta seção aborda os seguintes tópicos em Atualização offline em massa:

* **Visão geral**
* **Usando Atualização Offline em Massa**

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

Atualização off-line em massa, permite atualizar todo o canal em massa. Evita o incômodo de navegar até um canal específico e atualizar o conteúdo. Em vez disso, você pode atualizar todo o conteúdo em canais de um projeto específico em um instante.

Você também pode agendar essa atividade para um tempo de menor tráfego de rede.

>[!NOTE]
>
>O recurso Atualização off-line em massa é otimizado para atualizar apenas os canais que foram modificados.

## Usando a Atualização Offline em Massa {#using-bulk-offline-update}

Você pode usar manualmente a atualização offline em massa da interface do usuário (UI) ou agendar a atualização em massa dos serviços OSGi.

### Usando a interface de usuário do AEM Screens {#using-aem-screens-user-interface}

Siga as etapas abaixo para usar a atualização offline em massa para um projeto AEM Screens:

1. Navegue até o seu projeto AEM Screens.
1. Selecione o projeto e clique em **Atualizar conteúdo offline** na barra de ações para atualizar manualmente o conteúdo do canal.

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Configuração do Adobe Experience Manager Web Console {#adobe-experience-manager-web-console-configuration}

Siga as etapas abaixo para usar a atualização offline em massa para um projeto AEM Screens:

1. Configuração do Adobe Experience Manager Web Console.
1. Procurar serviços de atualização offline em massa.

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. Adicione as seguintes propriedades:

   **Caminho do** projetoEspecifique o caminho do seu projeto AEM Screens. O caminho normalmente é `/content/screens/<Name of your project>`.

   *Por exemplo*, `/content/screens/we-retail`. Você pode encontrar esse caminho no URL selecionando qualquer projeto no AEM Screens (não clique no ícone).

   >[!NOTE]
   >
   >Especifique o caminho do projeto relativo ao seu canal.

   **Agendar** frequênciaEspecifique uma hora, por exemplo, 17:00 ou 17:00, na qual este serviço deve atualizar o conteúdo offline.

1. Clique em **Salvar** para salvar suas configurações e seu conteúdo será atualizado no horário especificado.

