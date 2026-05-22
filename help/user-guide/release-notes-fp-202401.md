---
title: Notas de versão do Pacote de recursos 202401 da Screens
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202401 lançado em 2 de janeiro de 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
TQID: https://experienceleague.adobe.com/b6ZM04Vl6ozehx8E-y9iV1KAo-FI7DZSpDcHvhudkMI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 10%

---

# Notas de versão do Pacote de recursos 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>A Adobe recomenda atualizar para a versão mais recente do 6.5 Adobe Experience Manager (AEM 6.5). Obtenha as informações da última versão de [aqui](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes).

## Disponibilidade {#availability}

A AEM Screens lançou o Pacote de recursos 11.1 do AEM 6.5.

Você pode baixar o Feature Pack mais recente para a Versão 6.5.11.1 do AEM Screens no [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o Pacote de Recursos mais recente denominado **AEM 6.5 Screens FP11.1**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos 202204 do AEM Screens é 2 de janeiro de 2024.

### Novidades {#what-is-new}

Esta versão inclui somente correções de segurança.

### Correções de erros {#bug-fixes}

* Problema XSS no campo &quot;Texto inativo&quot; do dispositivo do AEM Screens. (SCRNS-2614)

* Problema XSS em `screens/dashboard/device.html` por meio da caixa de diálogo de ação `Clear cache`. (SCRNS-2632)

* Problema de XSS na configuração do reprodutor do Screens em `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* O XSS armazenado no título dos dispositivos é acionado quando um dispositivo é excluído. (SCRNS-2653)

* Problema de XSS em `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS refletido com o parâmetro `item` em `/screens/register-device-wizard.html`. (SCRNS-2670)

* XSS refletido em `screens/dashboard/device.html` por meio do parâmetro `returnPage`. (SCRNS-3056)

* Abra Redirecionar em assign-device-wizard.html. (SCRNS-3444)

* Abra Redirecionar no painel do dispositivo. (SCRNS-3443)

* Problema de XSS em `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Botões Fixed, Missing Recurrence Schedule e Add Schedule: A Problem Discovered in Channel Scheduling. (Correção, Ausência de agendamento de recorrência e Adicionar agendamento: Um problema foi descoberto no agendamento do canal.) (SCRNS-2739)
