---
title: Ambientes para [!UICONTROL AEM Screens]
seo-title: Ambientes para [!UICONTROL AEM Screens]
description: Esta página descreve os ambientes de um projeto AEM Screens.
seo-description: Esta página destaca os ambientes de um projeto AEM Screens.
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---


# Ambientes {#environments}

Determine antecipadamente quais AEM ambientes o cliente tem e espera que você use, tanto para *desenvolvimento* quanto para *deployment*.

>[!NOTE]
>
>A AEM Screens requer vários pacotes para que os projetos funcionem. Todos os ambientes devem estar executando a mesma versão do Adobe Experience Manager.

Siga as diretrizes abaixo para configurar o ambiente para seu projeto AEM Screens:

1. Execute as versões mais recentes dos seguintes pacotes para sua versão do Adobe Experience Manager:

   * **AEM Service Pack**
   * **Pacote de recursos do Screens**
   * **AEM Cumulative Fix Pack**

1. Identifique quaisquer pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.

1. Instale os mesmos pacotes de software nos ambientes de desenvolvimento local.

1. Instrua seu cliente a adotar a mesma configuração em todos os seus servidores de QA, estágio e produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.
