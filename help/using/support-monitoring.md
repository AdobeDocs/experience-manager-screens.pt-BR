---
title: Monitoramento de suporte
description: Saiba mais sobre o Guia de práticas recomendadas de monitoramento de suporte do AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Monitoramento de suporte {#support-monitoring}

Esta seção fornece as práticas recomendadas relacionadas ao gerenciamento de anomalias de dispositivo e conteúdo em um projeto de sinalização digital.

O monitoramento de suporte inclui:

* **Monitoramento de dispositivo**
* **Monitoramento de conteúdo**

## Monitoramento de conteúdo {#content-monitoring}

O monitoramento de conteúdo permite que você solucione problemas relacionados ao conteúdo não exibido corretamente na tela:

1. Se um problema de tela em branco for encontrado:

   * Marcar *pré-visualização* assim, você pode ver se o canal está mostrando uma tela preta.
   * Registrar um *reprodutor chrome local* (como extensão) no laptop para essa tela e veja se ela mostra uma tela preta.
   * Clique com o botão direito do mouse, inspecione e marque *logs aplicáveis*.

   Além disso, se isso não estiver acontecendo no reprodutor local, mas somente no dispositivo:

   * Marcar *tipo de mídia* (em uso) que pode ter problemas nesse dispositivo e também confirmar se o conteúdo foi baixado localmente com êxito (a interface do administrador limpa o cache de canal).
   * Incluir qualquer *logs do dispositivo* no tíquete para solução rápida de problemas.
   * *Coletar logs* do dispositivo do AEM.

## Monitoramento de dispositivo {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar um problema de tela em branco:

1. Se um problema de tela em branco for encontrado:

   * Verifique se *exibição* está ligado.
   * Verifique se *computador* está ligado e está enviando sinal.
   * Clique com o botão direito do mouse, inspecione e marque *logs aplicáveis*.
