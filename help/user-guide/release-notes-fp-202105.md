---
title: Notas de versão do Pacote de recursos 202105
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202105, lançado em 4 de junho de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 3%

---

# Notas de versão do Pacote de recursos 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>A Adobe recomenda que você atualize para a versão mais recente do Adobe Experience Manager (AEM). O AEM Screens fornece suporte de manutenção para a plataforma AEM 6.3 Screens.

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 8.

Você pode baixar o Feature Pack mais recente para a versão AEM Screens 6.5.8 do [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o Pacote de Recursos mais recente denominado **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Instale a versão mínima do AEM 6.5 Feature Pack 8 para o conector AMS para funcionar após instalar os pacotes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` e `screens core bundles`.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos 202105 do AEM Screens é 4 de junho de 2021.

### Novidades {#what-is-new}

* **Bloqueando página em um canal do AEM Screens**

  O AEM Screens agora oferece suporte ao *Bloqueio de Página*, conforme já implementado no AEM Sites. O Adobe Experience Manager (AEM) permite bloquear uma página, de modo que ninguém mais possa editar o conteúdo. Esse recurso é útil ao fazer várias edições em uma página específica ou quando é necessário congelar uma página por pouco tempo.

* **Nomeando Dispositivo AEM Screens Player**

  Os players do AEM Screens agora incluem a capacidade de enviar um nome de dispositivo para o Adobe Experience Manager (AEM).
Por padrão, quando o registro em massa é usado para registrar um dispositivo, um nome de usuário gerado pelo sistema é inserido no campo de título. Como alternativa, um cliente pode usar uma tag de ativo ou outro nome amigável para que seja visível no AEM e mais fácil atribuir o conteúdo apropriado.

  Consulte a documentação a seguir para obter informações sobre como configurar o nome em cada sistema operacional suportado:

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [SO CHROME](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Geração de manifesto**

  Geração de manifesto de canal mais rápida com desempenho aprimorado, como alocação de menos recursos no servidor.

### Correções de erros {#bug-fixes}

* O reprodutor exibia uma tela preta ao alternar para um canal contendo uma sequência incorporada dinâmica.
* Os players do Screens agora bloqueiam a alternância para qualquer canal com falha que evita um erro 404 ou uma página com uma mensagem de erro.

### Players do AEM Screens lançados

Os seguintes players de AEM Screens são lançados para AEM 6.5 Feature Pack 8:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
