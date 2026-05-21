---
title: Notas de versão do Pacote de recursos 202103
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202103, lançado em 5 de março de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
TQID: https://experienceleague.adobe.com/x7dgY8u-SdWo2JRK1W2uqRWtHy2wtXdAnIcS0gRoxiY
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 407
ht-degree: 4%

---

# Notas de versão do Pacote de recursos 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>A Adobe recomenda atualizar para a versão mais recente do Adobe Experience Manager (AEM). A AEM Screens fornece suporte de manutenção para a plataforma Screens do AEM 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou o Pacote de recursos 7 do AEM 6.5.

Você pode baixar o Feature Pack mais recente para a versão AEM Screens 6.5.7 do [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure **Screens** para obter o Feature Pack mais recente denominado **AEM 6.5 Screens FP7**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 202103 é 5 de março de 2021.

### Novidades {#what-is-new}

* **Registro automático de players do AEM Screens**

  Registrar em massa milhares de jogadores manualmente é complicado e adiciona tempo e custo. Para simplificar esse processo, o recurso Registro automático de players permite especificar uma chave pré-compartilhada no AEM. Essa chave pode ser provisionada em um player por meio de um arquivo de configuração ou de uma solução de Gerenciamento de dispositivos móveis (MDM).

  Consulte [Registro automático de players](/help/user-guide/auto-registration-players.md) para obter mais detalhes.


* **Provisionamento em massa do Android™ Player usando o Enterprise Mobility Management**

  Ao implantar o Android™ player em massa, é entediante registrar cada player manualmente com o AEM. É altamente recomendável usar uma solução de EMM (Enterprise Mobility Management), como o `VMWare Airwatch`, `MobileIron` ou `Samsung Knox`, para provisionar e gerenciar a implantação remotamente. O AEM Screens Android™ player oferece suporte ao EMM AppConfig padrão do setor para permitir o provisionamento remoto.

  Consulte [Provisionamento em massa do Android™ Player usando o Enterprise Mobility Management](/help/user-guide/implementing-android-player.md#implementation) para obter mais detalhes.


### Correções de erros {#bug-fixes}

* Desempenho aprimorado para computação `clientlib` e `asset hashes`.

* A migração SmartSync causaria uma falha no reprodutor se o cache não fosse invalidado.

* Os caches offline não foram criados, se a Atribuição tivesse *OfflineConfig*.

* Atualizações para o player `Tizen` que falharam porque não há suporte para política de referenciador strict-origin-when-cross-origin.

* A alteração do campo de programação *Repetições* do canal atribuído estava quebrando a interface do usuário.

* A atualização do conteúdo offline falhava com exceções de consulta.

* O atraso entre as transições durante a interação em uma experiência interativa agora é corrigido.

* Uma solicitação de atualização de configuração com falha causou telas em branco.

### Players do AEM Screens lançados

Os seguintes players de AEM Screens foram lançados para o Feature Pack 7 do AEM 6.5:

* SO CHROME
* Windows
* Linux®

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
