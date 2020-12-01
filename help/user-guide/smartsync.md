---
title: Transição do ContentSync para o SmartSync
seo-title: Transição do ContentSync para o SmartSync
description: Siga esta página para saber mais sobre o recurso SmartSync e como você pode transição de ContentSync para SmartSync.
seo-description: Siga esta página para saber mais sobre o recurso SmartSync e como você pode transição de ContentSync para SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 7832176cfb1e4647a49852ce382862978dddbfe2
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# Transição do ContentSync para o SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta seção fornece uma visão geral do recurso SmartSync e como ele minimiza a carga/armazenamento do servidor e o tráfego da rede para reduzir custos.

## Visão geral {#overview}

O SmartSync é o mecanismo mais recente usado pela AEM Screens. Ela serve como uma substituição do método atual usado para armazenar em cache canais offline e entregá-los ao player.

Ele é executado tanto no lado do servidor quanto no lado do cliente.

**No lado** do servidor:

* O conteúdo dos canais, incluindo ativos, é armazenado em cache em */var/contentsync*.
* O cache é exposto aos players por meio de um manifesto que descreve o conteúdo disponível para uma exibição.

**No lado** do cliente:

* O Player atualiza seu conteúdo com base no manifesto gerado acima.

### Benefícios do uso do SmartSync {#benefits-of-using-smartsync}

O recurso SmartSync oferece vários benefícios ao seu projeto AEM Screens. Permite

* Redução drástica do tráfego de rede e dos requisitos de armazenamento do lado do servidor
* O player baixa ativos de forma inteligente somente se o ativo estiver ausente ou alterado
* Otimizações de armazenamento do lado do servidor e do cliente

>[!NOTE]
>
>O Adobe recomenda enfaticamente o uso do SmartSync para projetos do AEM Screens.

## Migração de ContentSync para SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se você já instalou o AEM 6.3 Feature Pack 5 e o AEM 6.4 Feature Pack 3, é possível habilitar o SmartSync para ativos para melhorar o uso do espaço em disco. Para habilitar o SmartSync, siga a seção abaixo para transição de ContentSync para SmartSync, habilitando o SmartSync.
>
>O SmartSync está disponível para o Screens Player com servidores suportados AEM 6.4.3 FP3.
>
>Consulte [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) para baixar o player mais recente. A tabela a seguir descreve a versão mínima do player necessária para cada plataforma:

| **Plataforma** | **Versão Mínima Suportada do Player** |
|---|---|
| Android | 3,3,72 |
| Chrome OS | 1,0,136 |
| Windows | 1,0,136 |

Siga as etapas abaixo para transição de ContentSync para SmartSync:

1. A migração do ContentSync para o SmartSync requer a limpeza do cache do ContentSync antes de ativar o SmartSync.

   Navegue até o console ContentSync da sua instância usando o link ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e clique em **Limpar cache**, como mostrado na figura abaixo:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Todo o cache de conteúdo deve ser limpo antes de usar o SmartSync pela primeira vez.

1. Navegue até **Configuração do Adobe Experience Manager Web Console** por AEM instância —> ícone de martelo —> **Operações** —> **Console Web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **A** configuração do Adobe Experience Manager Web Console é aberta. Procure *offlinecontentservice*.

   Para pesquisar a propriedade **Screens Offline Content Service**, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Clique em **Salvar** para ativar a propriedade **Screens Offline Content Services** e, portanto, usar o SmartSync para AEM Screens.
1. Depois de habilitar o SmartSync, você deve navegar até o projeto e clicar em **Atualizar conteúdo offline** *(na barra de ações),* como mostrado na figura abaixo.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)