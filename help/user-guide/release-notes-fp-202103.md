---
title: Notas de versão do Pacote de recursos 202103
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202103, lançado em 5 de março de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 2%

---

# Notas de versão do Pacote de recursos 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>A Adobe recomenda que você atualize para a versão mais recente do Adobe Experience Manager (AEM). O AEM Screens fornece suporte de manutenção para a plataforma AEM 6.3 Screens.

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 7.

Baixe o Feature Pack mais recente do AEM Screens 6.5.7 na [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a **Adobe Experience Manager** e pesquisar **Screens** para obter o Feature Pack mais recente denominado como **AEM 6.5 Screens FP7**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 202103 é 5 de março de 2021.

### Novidades {#what-is-new}

* **Registro automático de players do AEM Screens**

  Registrar em massa milhares de jogadores manualmente é complicado e adiciona tempo e custo. Para simplificar esse processo, o recurso Registro automático de players permite especificar uma chave pré-compartilhada no AEM. Essa chave pode ser provisionada em um player por meio de um arquivo de configuração ou de uma solução de Gerenciamento de dispositivos móveis (MDM).

  Consulte [Registro automático de players](/help/user-guide/auto-registration-players.md) para obter mais detalhes.


* **Provisionamento em massa do Android™ Player usando o Enterprise Mobility Management**

  Ao implantar o Android™ player em massa, é entediante registrar cada player manualmente com AEM. É altamente recomendável usar uma solução de EMM (Enterprise Mobility Management, Gerenciamento de mobilidade corporativa) como `VMWare Airwatch`, `MobileIron`ou `Samsung Knox` para provisionar e gerenciar a implantação remotamente. O AEM Screens Android™ player oferece suporte ao EMM AppConfig padrão do setor para permitir o provisionamento remoto.

  Consulte [Provisionamento em massa do Android™ Player usando o Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) para obter mais detalhes.


### Correções de erros {#bug-fixes}

* Desempenho aprimorado para computação `clientlib` e `asset hashes`.

* A migração SmartSync causaria uma falha no reprodutor se o cache não fosse invalidado.

* Caches offline não foram criados, se a Atribuição tivesse *OfflineConfig*.

* Atualizações para `Tizen` player que foi interrompido porque não há suporte para política de referenciador de origem estrita quando origem cruzada.

* Alteração da programação do canal atribuído *Repetições* estava quebrando a interface do usuário.

* A atualização do conteúdo offline falhava com exceções de consulta.

* O atraso entre as transições durante a interação em uma experiência interativa agora é corrigido.

* Uma solicitação de atualização de configuração com falha causou telas em branco.

### Players do AEM Screens lançados

Os seguintes players de AEM Screens são lançados para AEM 6.5 Feature Pack 7:

* SO Chrome
* Windows
* Linux®

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
