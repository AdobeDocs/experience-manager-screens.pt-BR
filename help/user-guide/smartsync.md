---
title: Transição do ContentSync para o SmartSync
seo-title: Transição do ContentSync para o SmartSync
description: Siga esta página para saber mais sobre o recurso SmartSync e como fazer a transição de ContentSync para SmartSync.
seo-description: Siga esta página para saber mais sobre o recurso SmartSync e como fazer a transição de ContentSync para SmartSync.
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# Transição do ContentSync para o SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta seção fornece uma visão geral do recurso SmartSync e como ele minimiza a carga/armazenamento do servidor e o tráfego da rede para reduzir custos.

## Visão geral {#overview}

O SmartSync é o mecanismo mais recente usado pelo AEM Screens. Ela serve como uma substituição do método atual usado para armazenar em cache canais offline e entregá-los ao player.

Ele é executado tanto no lado do servidor quanto no lado do cliente.

**No lado** do servidor:

* O conteúdo dos canais, incluindo ativos, é armazenado em cache em */var/contentsync*.
* O cache é exposto aos players por meio de um manifesto que descreve o conteúdo disponível para uma exibição.

**No lado** do cliente:

* O Player atualiza seu conteúdo com base no manifesto gerado acima.

### Benefícios do uso do SmartSync {#benefits-of-using-smartsync}

O recurso SmartSync oferece vários benefícios ao seu projeto do AEM Screens. Permite

* Redução drástica do tráfego de rede e dos requisitos de armazenamento do lado do servidor
* O player baixa ativos de forma inteligente somente se o ativo estiver ausente ou alterado
* Otimizações de armazenamento do lado do servidor e do cliente

>[!NOTE]
>
>A Adobe recomenda usar o SmartSync para projetos do AEM Screens.

## Migração de ContentSync para SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se você já tiver instalado o AEM 6.3 Feature Pack 5 e o AEM 6.4 Feature Pack 3, poderá habilitar o SmartSync para ativos para melhorar o uso do espaço em disco. Para habilitar o SmartSync, siga a seção abaixo para fazer a transição do ContentSync para o SmartSync, habilitando o SmartSync.
>
>O SmartSync está disponível para o Screens Player com servidores compatíveis com o AEM 6.4.3 FP3.
>
>Consulte Downloads [](https://download.macromedia.com/screens/) do AEM Screens Player para baixar o player mais recente. A tabela a seguir descreve a versão mínima do player necessária para cada plataforma:

| **Plataforma** | **Versão Mínima Suportada do Player** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Siga as etapas abaixo para fazer a transição de ContentSync para SmartSync:

1. A migração do ContentSync para o SmartSync requer a limpeza do cache do ContentSync antes de ativar o SmartSync.

   Navegue até o console ContentSync da sua instância usando o link ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e clique em **Limpar cache**, como mostrado na figura abaixo:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Todo o cache de conteúdo deve ser limpo antes de usar o SmartSync pela primeira vez.

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por meio da instância do AEM —&gt; ícone de martelo —&gt; **Operações** —&gt; Console **da** Web.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **A configuração do console da Web do Adobe Experience Manager **é aberta. Procure *offline econtentservices*.

   Para pesquisar a propriedade **Screens Offline Content Service** , pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Clique em **Salvar** para ativar a propriedade **Screens Offline Content Services** e, portanto, usar SmartSync para AEM Screens.
1. Depois de habilitar o SmartSync, você deve navegar até o projeto e clicar em **Atualizar conteúdo** offline *(na barra de ações),* conforme mostrado na figura abaixo.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)