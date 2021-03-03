---
title: Notas de versão do Feature Pack 202103
description: A página destaca as Notas de versão do Feature Pack 202103.
translation-type: tm+mt
source-git-commit: 34f93df3fa212eaae713b0c8686d95beeb0c7b67
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 2%

---


# Notas de versão do Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para a plataforma do AEM 6.3 Screens.

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 7.

Você pode baixar o pacote de recursos mais recente para a versão do AEM Screens 6.5.7 no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP7**.

## Data de lançamento {#release-date}

A data de lançamento do Feature Pack 202103 do AEM Screens é 8 de março de 2021.

### Novidades {#what-is-new}

* **Registro e atribuição em massa do AEM Screens**

   O registro em massa de milhares de jogadores manualmente é muito complicado e aumenta o tempo e o custo. Para simplificar esse processo, o recurso Registro em massa permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um player por meio de um arquivo de configuração ou de uma solução de Gerenciamento de dispositivo móvel (MDM).

* **Provisionamento em massa do Android Player usando o Gerenciamento de mobilidade empresarial**

   Ao implantar o reprodutor Android em massa, torna-se entediante registrar manualmente cada reprodutor no AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron ou Samsung Knox para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android player é compatível com o EMM AppConfig padrão do setor para permitir provisionamento remoto.


### Correções de erros {#bug-fixes}

* Desempenho aprimorado para computação `clientlib` e `asset hashes`.

* A migração do SmartSync quebraria o reprodutor, se o cache não fosse invalidado.

* Os caches offline não foram criados, se a Atribuição tivesse *OfflineConfig*.

* Atualizações para problemas do Tizen player porque a política de referência origem estrita quando origem cruzada não é suportada.

* A alteração do campo &quot;Repetir&quot; do agendamento do canal atribuído estava quebrando a interface do usuário.

* A atualização do conteúdo offline falhava com exceções de consulta.

* A migração do SmartSync estava quebrando o reprodutor, se o cache não foi invalidado


### Players do AEM Screens {#released-aem-screens-players} liberados

Os seguintes players do AEM Screens foram lançados para o Feature Pack 7 do AEM 6.5:

* Chrome OS
* Windows
* Android
* Tizen
* Linux

#### Downloads do Player do AEM Screens {#aem-screens-player-downloads}

Para baixar o reprodutor do AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do reprodutor do AEM Screens](https://download.macromedia.com/screens/index.html)**.
