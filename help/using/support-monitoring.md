---
title: Monitoramento de suporte
seo-title: Monitoramento de suporte para o AEM Screens
description: A página descreve o Guia de práticas recomendadas para monitoramento de suporte do AEM Screens
seo-description: A página descreve o Guia de práticas recomendadas para monitoramento de suporte do AEM Screens
translation-type: tm+mt
source-git-commit: 3c91e0ec80b29bebcc066f45a1eef1fd74e00a13

---


# Monitoramento de suporte {#support-monitoring}

Esta seção fornece as práticas recomendadas relacionadas ao gerenciamento de anomalias de dispositivo e conteúdo em um projeto de sinalização digital.

O monitoramento de suporte inclui:

* **Monitoramento de dispositivos**
* **Monitoramento de conteúdo**

## Monitoramento de conteúdo {#content-monitoring}

O monitoramento de conteúdo permite que você solucione problemas relacionados ao conteúdo que não é exibido corretamente na tela:

1. Se um problema de tela em branco for encontrado:

   * Verifique a *visualização* para ver se o canal está mostrando uma tela preta
   * Registre um reprodutor *cromático* local (como extensão) no seu laptop para ver se ele mostra uma tela preta.
   * Clique com o botão direito do mouse e inspecione e verifique os registros *aplicáveis*.
   Além disso, se isso não estiver acontecendo no player local, mas apenas no dispositivo:

   * Verifique o tipo *de* mídia (em uso) que pode apresentar problemas nesse dispositivo e também confirme se o conteúdo foi baixado localmente (cache de canal limpo da interface do administrador).
   * Inclua todos os registros *do* dispositivo no tíquete para uma rápida solução de problemas.
   * *Colete logs* do dispositivo a partir do AEM.


## Monitoramento de dispositivos {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar problemas de tela em branco:

1. Se um problema de tela em branco for encontrado:

   * Verifique se o *monitor* está ligado.
   * Verifique se o *computador* está ligado e enviando sinal.
   * Clique com o botão direito do mouse, inspecione e verifique os registros *aplicáveis*.

