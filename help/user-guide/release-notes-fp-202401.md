---
title: Notas de versão do Pacote de recursos do Screens 202401
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202401 lançado em 2 de janeiro de 2024.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# Notas de versão do Pacote de recursos 202401 {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager 6.5 (AEM 6.5). Você pode obter as informações da versão mais recente de [aqui](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes)

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 11.1.

Baixe o pacote de recursos mais recente do AEM Screens 6.5.11.1 versão no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até **Adobe Experience Manager** e pesquisar **Screens** para obter o pacote de recursos mais recente intitulado como **Telas AEM 6.5 FP11.1**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos 202204 do AEM Screens é 2 de janeiro de 2024.

### Novidades {#what-is-new}

Esta versão inclui somente correções de segurança.

### Correções de erros {#bug-fixes}

* Problema XSS no campo &quot;Texto inativo&quot; do dispositivo do AEM Screens. (SCRNS-2614)

* Problema XSS em `screens/dashboard/device.html` por meio da `Clear cache` caixa de diálogo de ação. (SCRNS-2632)

* Problema XSS na configuração do reprodutor do Screens em `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* O XSS armazenado no título dos dispositivos é acionado quando um dispositivo é excluído. (SCRNS-2653)

* Problema XSS em `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS refletido com o parâmetro `item` em `/screens/register-device-wizard.html`. (SCRNS-2670)

* Entrada de XSS refletida `screens/dashboard/device.html` por meio da `returnPage` parâmetro. (SCRNS-3056)

* Abra Redirecionar em assign-device-wizard.html. (SCRNS-3444)

* Abra Redirecionar no painel do dispositivo. (SCRNS-3443)

* Problema XSS em `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* Botões Fixed, Missing Recurrence Schedule e Add Schedule: A Problem Discovered in Channel Scheduling. (Correção, Ausência de agendamento de recorrência e Adicionar agendamento: Um problema foi descoberto no agendamento do canal.) (SCRNS-2739)
