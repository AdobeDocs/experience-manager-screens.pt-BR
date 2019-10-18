---
title: Ambientes para o [!UICONTROL AEM Screens]
seo-title: Ambientes para o [!UICONTROL AEM Screens]
description: Esta página descreve os ambientes de um projeto do AEM Screens.
seo-description: Esta página destaca os ambientes de um projeto do AEM Screens.
translation-type: tm+mt
source-git-commit: 0d91aa653508969cf1f4ccfba23a570e22e6414c

---


# Ambientes {#environments}

Determine antecipadamente quais ambientes AEM o cliente tem e espera que você use, tanto para *desenvolvimento* quanto para *implantação*.

>[!NOTE]
>
>O AEM Screens requer vários pacotes para que os projetos funcionem. Todos os ambientes devem estar executando a mesma versão do Adobe Experience Manager.

Siga as diretrizes abaixo para configurar o ambiente para seu projeto do AEM Screens:

1. Execute as versões mais recentes dos seguintes pacotes para sua versão do Adobe Experience Manager:

   * **AEM Service Pack**
   * **Pacote de recursos do Screens**
   * **Pacote de correções cumulativo do AEM**

1. Identifique quaisquer pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, Hybris SAP) necessários.

1. Instale os mesmos pacotes de software nos ambientes de desenvolvimento local.

1. Instrua seu cliente a adotar a mesma configuração em todos os servidores de QA, estágio e produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.
