---
title: Monitoramento de suporte
description: Saiba mais sobre o Guia de práticas recomendadas de monitoramento de suporte do AEM Screens.
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '218'
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

   * Verifique a *visualização* para ver se o canal está mostrando uma tela preta.
   * Registre um *Chrome player local* (como uma extensão) em seu laptop para essa exibição e veja se ele exibe uma tela preta.
   * Clique com o botão direito do mouse, inspecione e verifique os *logs aplicáveis*.

   Além disso, se o problema não estiver acontecendo no reprodutor local, mas somente no dispositivo:

   * Verifique o *tipo de mídia* (em uso) que pode ter problemas nesse dispositivo e também confirme se o conteúdo foi baixado localmente com êxito (a interface do administrador limpa o cache de canal).
   * Inclua quaisquer *logs de dispositivo* no tíquete para resolução rápida de problemas.
   * *Coletar logs* do dispositivo do AEM.

## Monitoramento de dispositivo {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar um problema de tela em branco:

1. Se um problema de tela em branco for encontrado:

   * Verifique se a *exibição* está ativada.
   * Verifique se o *computador* está ligado e enviando um sinal.
   * Clique com o botão direito do mouse, inspecione e verifique *logs aplicáveis*.
