---
title: Notas de versão do Pacote de recursos 202103
description: "Siga esta página para obter informações sobre o AEM Screens Feature Pack 202103 lançado em 5 de março de 2021."
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Notas de versão do Pacote de recursos 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para a plataforma AEM 6.3 Screens.

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 7.

Baixe o pacote de recursos mais recente do AEM Screens 6.5.7 na [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até **Adobe Experience Manager** e pesquisar **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP7**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 202103 é 5 de março de 2021.

### Novidades {#what-is-new}

* **Registro automático de players do AEM Screens**

   Registrar em massa milhares de jogadores manualmente é muito complicado e adiciona tempo e custo. Para simplificar esse processo, o recurso Registro automático de players permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um player por meio de um arquivo de configuração ou uma solução de Gerenciamento de dispositivo móvel (MDM).

   Consulte [Registro automático de players](/help/user-guide/auto-registration-players.md) para obter mais detalhes.


* **Provisionamento em massa do Android Player usando o Enterprise Mobility Management**

   Ao implantar o reprodutor Android em massa, é entediante registrar manualmente cada um dos reprodutores com AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management), como VMWare Airwatch, MobileIron ou Samsung Knox, para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android Player oferece suporte ao EMM AppConfig padrão do setor para permitir o provisionamento remoto.

   Consulte [Provisionamento em massa do Android Player usando o Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) para obter mais detalhes.


### Correções de erros {#bug-fixes}

* Desempenho aprimorado para computação `clientlib` e `asset hashes`.

* A migração SmartSync causaria uma falha no reprodutor se o cache não fosse invalidado.

* Caches offline não foram criados, se a Atribuição tivesse *OfflineConfig*.

* Atualizações no reprodutor Tizen que falharam porque a política do referenciador de origem estrita quando origem cruzada não é compatível.

* Alteração da programação do canal atribuído *Repetições* estava quebrando a interface do usuário.

* A atualização do conteúdo offline falhava com exceções de consulta.

* O atraso entre as transições durante a interação na experiência interativa agora é corrigido.

* Falha na solicitação de atualização de configuração, causando a tela em branco.

### Players do AEM Screens lançados {#released-aem-screens-players}

Os seguintes players de AEM Screens são lançados para AEM 6.5 Feature Pack 7:

* SO Chrome
* Windows
* Linux

#### Downloads do AEM Screens Player  {#aem-screens-player-downloads}

Para baixar o reprodutor AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
