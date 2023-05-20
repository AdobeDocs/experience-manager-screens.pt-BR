---
title: Ambientes para [!UICONTROL AEM Screens]
seo-title: Environments for [!UICONTROL AEM Screens]
description: Esta página descreve os ambientes de um projeto do AEM Screens.
seo-description: This page highlights the environments for an AEM Screens project.
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# Ambientes {#environments}

Determine com antecedência quais ambientes AEM o cliente tem e espera que você use, tanto para *desenvolvimento* e *implantação*.

>[!NOTE]
>
>O AEM Screens requer vários pacotes para que os projetos funcionem. Todos os ambientes devem estar executando a mesma versão do Adobe Experience Manager.

Siga as diretrizes abaixo para configurar o ambiente para seu projeto do AEM Screens:

1. Execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager:

   * **AEM Service Pack**
   * **Pacote de recursos do Screens**
   * **AEM Pacote de correções cumulative**

1. Identifique todos os pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.

1. Instale os mesmos pacotes de software em seus ambientes de desenvolvimento locais.

1. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.
