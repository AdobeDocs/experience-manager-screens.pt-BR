---
title: Notas de versão do Pacote de recursos 201907
description: Saiba mais sobre o Pacote de recursos do AEM Screens 201907, lançado em 31 de julho de 2019.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
TQID: https://experienceleague.adobe.com/fbTrzAj52dW2JuRe-6InIkh-dT52Au9pGgoAEjR7WW8
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 378
ht-degree: 1%

---

# Notas de versão do Pacote de recursos 201907 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>A Adobe recomenda atualizar para a versão mais recente do Adobe Experience Manager (AEM). A AEM Screens fornece suporte de manutenção para a plataforma Screens do AEM 6.3.

A AEM Screens lançou o AEM 6.4.5 Feature Pack 5 e o AEM 6.5.1 Feature Pack 1 com os seguintes detalhes.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos 2019 do AEM Screens é 31 de julho de 2019.

### Novidades {#what-s-new}

* **O acionador de dados direciona a alteração de ativos em um canal do AEM Screens**

O reprodutor muda para um canal que mostra informações de emergência. O sistema de emergência envia essas informações quando recebe um evento. O canal é reproduzido exclusivamente até que a situação de emergência acabe.


Consulte o caso de uso [Canal de emergência](emergency-channel.md) para implementação.

* **Direcionamento ativado para componentes assíncronos

O direcionamento agora pode ser ativado para ativos usados no projeto do AEM Screens.

Para saber mais sobre como habilitar o direcionamento de ativos no projeto do AEM Screens, consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

Depois de configurar o ContextHub para seu projeto do AEM Screens, siga diferentes casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

**[Ativação Direcionada para Estoque de Varejo](retail-inventory-activation.md)**

**[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**

**[Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)**

* **Melhorias nos Manipuladores de Atualização**

O manipulador de atualização agora analisa os fragmentos de experiência e coleta qualquer imagem, vídeo ou produto associado a ele.

* **Lançamentos**

Os lançamentos permitem que os autores de conteúdo criem versões futuras dos canais. Com a ajuda de Lançamentos, os autores podem visualizar cada canal no lançamento e devem poder iniciar uma solicitação de revisão. O grupo de aprovadores recebe uma notificação e pode aprovar ou rejeitar a solicitação. Quando a data de ativação é atingida, o conteúdo é reproduzido nos dispositivos.
Consulte [Inicializações](launches.md) para obter mais detalhes.

* **Configurações offline em Fragmentos de experiência**

Agora é possível adicionar configurações offline (bibliotecas do lado do cliente e arquivos estáticos) ao configurar o Screens Experience Fragment. Consulte [Uso de fragmentos de experiência](experience-fragments-in-screens.md) para obter mais detalhes.

### Players do AEM Screens lançados

Os seguintes players do AEM Screens foram lançados para o Pacote de recursos 5 do AEM 6.4.5 e Pacote de recursos 1 do AEM 6.5.1:

* ChromeOS
* Windows
* Android™

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte [Downloads do AEM Screens Player](https://download.macromedia.com/screens/).
