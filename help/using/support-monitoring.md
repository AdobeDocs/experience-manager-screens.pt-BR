---
title: Monitoramento de suporte
seo-title: Monitoramento de suporte para AEM Screens
description: A página descreve o Guia de Monitoramento de Suporte para Práticas Recomendadas da AEM Screens
seo-description: A página descreve o Guia de Monitoramento de Suporte para Práticas Recomendadas da AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Monitoramento de suporte {#support-monitoring}

Esta seção fornece as práticas recomendadas relacionadas ao gerenciamento de anomalias de dispositivo e conteúdo em um projeto de sinalização digital.

O monitoramento de suporte inclui:

* **Monitoramento de dispositivos**
* **Monitoramento de conteúdo**

## Monitoramento de conteúdo {#content-monitoring}

O monitoramento de conteúdo permite que você solucione problemas relacionados ao conteúdo que não é exibido corretamente na tela:

1. Se um problema de tela em branco for encontrado:

   * Verifique *pré-visualização* para ver se o canal está a mostrar uma tela preta
   * Registre um *reprodutor local do cromo* (como extensão) no seu computador portátil para essa tela e veja se isso mostra uma tela preta.
   * Clique com o botão direito do mouse e inspecione e verifique *registros aplicáveis*.

   Além disso, se isso não estiver acontecendo no player local, mas apenas no dispositivo:

   * Verifique *o tipo de mídia* (em uso) que pode ter problemas nesse dispositivo e também confirme se o conteúdo foi baixado localmente (cache de canal limpo da interface do usuário do administrador).
   * Inclua *registros do dispositivo* no ticket para solucionar rapidamente o problema.
   * *Colete* logons do dispositivo a partir do AEM.


## Monitoramento de dispositivo {#device-monitoring}

Monitoramento de dispositivo relacionado ao monitoramento do dispositivo físico se você encontrar um problema de tela em branco:

1. Se um problema de tela em branco for encontrado:

   * Verifique se *display* está ligado.
   * Verifique se o *computador* está ligado e a enviar sinal.
   * Clique com o botão direito do mouse, inspecione e verifique *registros aplicáveis*.

