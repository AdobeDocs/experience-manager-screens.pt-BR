---
title: Suporte e manutenção no segundo dia
description: Saiba mais sobre o suporte e a manutenção do segundo dia da AEM Screens.
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
TQID: https://experienceleague.adobe.com/IMuRCxE7v8DyK-T4Q3lehhclfgGtu0VIHyIsODOpEzA
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 186
ht-degree: 0%

---

# Suporte e manutenção da plataforma no segundo dia {#day-two-support-maintenance}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

O AEM Screens requer vários pacotes para que os projetos funcionem. Todos os ambientes devem estar executando a mesma versão do Adobe Experience Manager.

Siga as diretrizes de suporte e manutenção para o Segundo dia da fase de desenvolvimento do projeto:

1. Execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager:

   * **AEM Service Pack**
   * **Pacote de recursos do Screens**
   * **AEM Cumulative Fix Pack**

1. Identifique todos os pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.

1. Instale os mesmos pacotes de software no ambiente de desenvolvimento local.

1. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criam problemas ao implantar e testar.
