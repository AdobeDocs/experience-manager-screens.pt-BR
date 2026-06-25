---
title: Monitoramento de suporte
description: Saiba mais sobre o Guia de práticas recomendadas de monitoramento de suporte do AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 0%

---

# Monitoramento de suporte {#support-monitoring}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

Esta seção fornece as práticas recomendadas relacionadas ao gerenciamento de anomalias de dispositivo e conteúdo em um projeto de sinalização digital.

O monitoramento de suporte inclui:

* **Monitoramento de dispositivo**
* **Monitoramento de conteúdo**

## Monitoramento de conteúdo {#content-monitoring}

O monitoramento de conteúdo permite que você solucione problemas relacionados ao conteúdo não exibido corretamente na tela:

1. Se um problema de tela em branco for encontrado:

   * Verifique a *visualização* para ver se o canal está mostrando uma tela preta.
   * Registre um *Chrome player local* (como uma extensão) em seu laptop para essa exibição e veja se ele exibe uma tela preta.
   * Clique com o botão direito do mouse, inspecione e verifique os *logs aplicáveis*.

   Além disso, se o problema não estiver acontecendo no reprodutor local, mas somente no dispositivo:

   * Verifique o *tipo de mídia* (em uso) que pode ter problemas nesse dispositivo e também confirme se o conteúdo foi baixado localmente com êxito (a interface do administrador limpa o cache de canal).
   * Inclua quaisquer *logs de dispositivo* no tíquete para resolução rápida de problemas.
   * *Coletar logs* do dispositivo da AEM.

## Monitoramento de dispositivo {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar um problema de tela em branco:

1. Se um problema de tela em branco for encontrado:

   * Verifique se a *exibição* está ativada.
   * Verifique se o *computador* está ligado e enviando um sinal.
   * Clique com o botão direito do mouse, inspecione e verifique *logs aplicáveis*.
