---
title: Notas de versão do Feature Pack 202105
description: '"Siga esta página para obter informações sobre o AEM Screens Feature Pack 202105 lançado em 04 de junho de 2021."'
feature: Pacote de recursos
role: Developer
level: Intermediate
source-git-commit: 444535b38fdf112939fdbf4c0f3f48e1cc28c902
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 10%

---

# Notas de versão do Feature Pack 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para AEM plataforma do Screens 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou AEM 6.5 Feature Pack 8.

Você pode baixar o pacote de recursos mais recente para a versão do AEM Screens 6.5.8 no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP8**.

## Data de lançamento {#release-date}

A data de lançamento do AEM Screens Feature Pack 202105 é 4 de junho de 2021.

### Novidades {#what-is-new}

* **Bloquear página em um canal da AEM Screens**

   O AEM Screens agora oferece suporte para *Bloquear uma página*, conforme já implementado no AEM Sites. O Adobe Experience Manager (AEM) permite bloquear uma página, de modo que ninguém mais possa modificar o conteúdo. Isso é útil quando você está fazendo diversas edições para uma página específica ou quando precisa congelar uma página por pouco tempo.

* **Como nomear dispositivo reprodutor do AEM Screens**

   Os players do AEM Screens agora incluem a capacidade de enviar um nome de dispositivo para o Adobe Experience Manager (AEM).
Por padrão, quando o registro em massa é usado para registrar um dispositivo, um nome de usuário gerado pelo sistema é inserido no campo de título. Como alternativa, um cliente pode usar uma tag de ativo ou outro nome amigável para que seja visível em AEM e fácil atribuir o conteúdo apropriado.

   Consulte a seguinte documentação para saber como configurar o nome em cada sistema operacional suportado:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Geração de Manifesto**

   Geração de manifesto de canal mais rápida com desempenho aprimorado, como alocar menos recursos no servidor.

### Correções de erros {#bug-fixes}

* O player exibia uma tela preta ao alternar para um canal que continha uma sequência incorporada dinâmica.
* Os players do Screens agora bloqueiam a alternância para qualquer canal quebrado que evite mais o erro 404 ou uma página com uma mensagem de erro.

### Players AEM Screens liberados {#released-aem-screens-players}

Os seguintes Players do AEM Screens são lançados para o AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Downloads do Player do AEM Screens {#aem-screens-player-downloads}

Para baixar o reprodutor AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.