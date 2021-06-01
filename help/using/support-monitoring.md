---
title: Monitoramento de suporte
seo-title: Monitoramento de suporte para AEM Screens
description: A página descreve o Guia de monitoramento de suporte para práticas recomendadas do AEM Screens
seo-description: A página descreve o Guia de monitoramento de suporte para práticas recomendadas do AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Monitoramento de suporte {#support-monitoring}

Esta seção fornece as práticas recomendadas relacionadas ao gerenciamento de anomalias de dispositivo e conteúdo em um projeto de sinalização digital.

O monitoramento de suporte inclui:

* **Monitoramento de dispositivo**
* **Monitoramento de conteúdo**

## Monitoramento de conteúdo {#content-monitoring}

O monitoramento de conteúdo permite que você solucione os problemas relacionados ao conteúdo que não é exibido corretamente na tela:

1. Se for encontrado um problema de tela em branco:

   * Marque *preview* para ver se o canal está mostrando uma tela preta
   * Registre um *chrome player local* (como extensão) no laptop para essa exibição e veja se isso mostra uma tela preta.
   * Clique com o botão direito e inspecione e verifique *logs aplicáveis*.

   Além disso, se isso não estiver acontecendo no reprodutor local, mas somente no dispositivo:

   * Verifique *media type* (em uso) que pode ter problemas nesse dispositivo e também confirme se o conteúdo foi baixado com êxito localmente (interface de usuário do administrador limpar cache de canal).
   * Inclua qualquer *log do dispositivo* no tíquete para solução de problemas rápida.
   * *Colete* registros do dispositivo a partir do AEM.


## Monitoramento de dispositivo {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar um problema de tela em branco:

1. Se for encontrado um problema de tela em branco:

   * Verifique se *display* está ligado.
   * Verifique se o *computador* está ligado e está a enviar sinal.
   * Clique com o botão direito do mouse, inspecione e verifique *logs aplicáveis*.

