---
title: Ambientes para [!UICONTROL AEM Screens]
description: Saiba mais sobre os ambientes de um projeto do AEM Screens.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Ambientes {#environments}

Determine com antecedência quais ambientes AEM o cliente tem e espera que você use, para *desenvolvimento* e *implantação*.

>[!NOTE]
>
>O AEM Screens requer vários pacotes para que os projetos funcionem. Todos os ambientes devem estar executando a mesma versão do Adobe Experience Manager.

Siga as diretrizes abaixo para configurar o ambiente para seu projeto do AEM Screens:

1. Execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager:

   * **Service Pack do AEM**
   * **Pacote de recursos do Screens**
   * **Pacote de correções cumulative do AEM**

1. Identifique todos os pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.

1. Instale os mesmos pacotes de software no ambiente de desenvolvimento local.

1. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criam problemas ao implantar e testar.
