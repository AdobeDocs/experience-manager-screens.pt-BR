---
title: Notas de versão do Feature Pack 202103
description: '"Siga esta página para obter informações sobre o AEM Screens Feature Pack 202103 lançado em 05 de março de 2021."'
feature: Pacote de recursos
role: Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 3%

---


# Notas de versão do Feature Pack 202103 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para AEM plataforma do Screens 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou AEM 6.5 Feature Pack 7.

Você pode baixar o pacote de recursos mais recente da versão 6.5.7 do AEM Screens a partir do [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP7**.

## Data de lançamento {#release-date}

A data de lançamento do AEM Screens Feature Pack 202103 é 5 de março de 2021.

### Novidades {#what-is-new}

* **Registro automático de players do AEM Screens**

   O registro em massa de milhares de jogadores manualmente é muito complicado e aumenta o tempo e o custo. Para simplificar esse processo, o recurso Registro automático de players permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um player por meio de um arquivo de configuração ou uma solução de Gerenciamento de dispositivos móveis (MDM).

   Consulte [Registro automático de players](/help/user-guide/auto-registration-players.md) para obter mais detalhes.


* **Provisionamento em massa do Android Player usando o Gerenciamento de mobilidade empresarial**

   Ao implantar o reprodutor Android em massa, é entediante registrar manualmente cada reprodutor com AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron ou Samsung Knox para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android player é compatível com o EMM AppConfig padrão do setor para permitir provisionamento remoto.

   Consulte [Provisionamento em massa do Android Player usando o Enterprise Mobility Management](/help/user-guide/using-emm-bulkprovision-android-player.md) para obter mais detalhes.


### Correções de erros {#bug-fixes}

* Desempenho aprimorado para computação `clientlib` e `asset hashes`.

* A migração do SmartSync quebraria o reprodutor, se o cache não fosse invalidado.

* Os caches offline não foram criados, se a Atribuição tivesse *OfflineConfig*.

* Atualizações do Tizen player que ocorreram porque a política de referenciador de origem estrita quando origem cruzada não é suportada.

* Alterar o agendamento do canal atribuído *Repeates* estava quebrando a interface do usuário.

* A atualização do conteúdo offline falhava com exceções de consulta.

* O atraso de tempo entre transições durante a interação na experiência interativa agora é corrigido.

* Falha na solicitação de atualização de configuração, causando a tela em branco.

### Players AEM Screens liberados {#released-aem-screens-players}

Os seguintes Players do AEM Screens são lançados para o AEM 6.5 Feature Pack 7:

* Chrome OS
* Windows
* Linux

#### Downloads do Player do AEM Screens {#aem-screens-player-downloads}

Para baixar o reprodutor AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
