---
title: Notas de versão do Pacote de recursos 202105
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202105, lançado em 4 de junho de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
TQID: https://experienceleague.adobe.com/lm2FhBZ2X-GzGoCRrsUuAKmC7vPfyaPXwYXSTxxOBJg
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 415
ht-degree: 5%

---

# Notas de versão do Pacote de recursos 202105 {#release-notes-for-feature-pack}

>[!CAUTION]
>A Adobe recomenda atualizar para a versão mais recente do Adobe Experience Manager (AEM). A AEM Screens fornece suporte de manutenção para a plataforma Screens do AEM 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou o Pacote de recursos 8 do AEM 6.5.

Você pode baixar o Feature Pack mais recente para a versão AEM Screens 6.5.8 do [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o Pacote de Recursos mais recente denominado **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>Instale a versão mínima do AEM 6.5 Feature Pack 8 para que o conector AMS funcione após a instalação dos pacotes `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16` e `screens core bundles`.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos 202105 do AEM Screens é 4 de junho de 2021.

### Novidades {#what-is-new}

* **Bloqueando página em um canal do AEM Screens**

  O AEM Screens agora oferece suporte ao *Bloqueio de Página*, conforme já implementado no AEM Sites. O Adobe Experience Manager (AEM) permite bloquear uma página, de modo que ninguém mais possa editar o conteúdo. Esse recurso é útil ao fazer várias edições em uma página específica ou quando é necessário congelar uma página por pouco tempo.

* **Nomeando Dispositivo AEM Screens Player**

  Os players do AEM Screens agora incluem a capacidade de enviar um nome de dispositivo para o Adobe Experience Manager (AEM).
Por padrão, quando o registro em massa é usado para registrar um dispositivo, um nome de usuário gerado pelo sistema é inserido no campo de título. Como alternativa, um cliente pode usar uma tag de ativo ou outro nome amigável para que fique visível no AEM e seja mais fácil atribuir o conteúdo apropriado.

  Consulte a documentação a seguir para obter informações sobre como configurar o nome em cada sistema operacional suportado:

   * [Android™](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [SO CHROME](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **Geração de manifesto**

  Geração de manifesto de canal mais rápida com desempenho aprimorado, como alocação de menos recursos no servidor.

### Correções de erros {#bug-fixes}

* O reprodutor exibia uma tela preta ao alternar para um canal contendo uma sequência incorporada dinâmica.
* Os players do Screens agora bloqueiam a alternância para qualquer canal com falha que evita um erro 404 ou uma página com uma mensagem de erro.

### Players do AEM Screens lançados

Os seguintes players de AEM Screens foram lançados para o Pacote de recursos 8 do AEM 6.5:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
