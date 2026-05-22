---
title: Notas de versão do Pacote de recursos do Screens 20250327
description: Saiba mais sobre o Pacote de recursos 20250327 do AEM Screens, lançado em 27 de março de 2025.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
TQID: https://experienceleague.adobe.com/q6KAClMHbAULOEumQlx5-FdaaVmAcMOCL8m6KWIB458
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 10%

---

# Notas de versão do Pacote de recursos 20250327 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>A Adobe recomenda atualizar para a versão mais recente do 6.5 Adobe Experience Manager (AEM 6.5). Você pode obter as informações da versão mais recente de [aqui](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes).
>A Adobe recomenda usar FP11.6 com SP (servicepack) >= 21.

## Disponibilidade {#availability}

A AEM Screens lançou o Pacote de recursos 11.6 do AEM 6.5.

Você pode baixar o Feature Pack mais recente para a Versão 6.5.11.6 do AEM Screens no [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o Pacote de Recursos mais recente denominado **AEM 6.5 Screens FP11.6**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 20250327 é 27 de março de 2025.

### Novidades {#what-is-new}

* Esta versão corrige o conflito de pacotes que os usuários enfrentam com o Service Pack 21 e superior.

* Esta versão corrige o problema na exibição de cartão com SP22 e superior.

* **Atualização em AEM Screens Players**
   * O AEM Screens Player baseado em Linux foi oficialmente descontinuado. Os usuários são aconselhados a migrar para outro sistema operacional compatível com o AEM Screens.
   * Não são feitas mais atualizações ou aprimoramentos no AEM Screens Player com base em Android. Os usuários são incentivados a migrar para um sistema operacional alternativo compatível com a AEM Screens.

### Correções de erros {#bug-fixes}

* Conflito de pacote com o Service Pack 21 e o Pacote de recursos do Screens. (SCRNS-4638)

* O Screens Dashboard não está funcionando. (SCRNS-4749)

* Problema XSS em /libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js (SCRNS-4761)
