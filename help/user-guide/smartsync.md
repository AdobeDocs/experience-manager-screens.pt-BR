---
title: Transição do ContentSync para o SmartSync
description: Saiba mais sobre o recurso SmartSync e como fazer a transição de ContentSync para SmartSync.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Transição do ContentSync para o SmartSync {#transitioning-from-contentsync-to-smartsync}

Esta seção fornece uma visão geral do recurso SmartSync e como ele minimiza a carga/armazenamento do servidor e o tráfego de rede para reduzir o custo.

## Visão geral {#overview}

O SmartSync é o mecanismo mais recente usado pelo AEM Screens. Ele serve como uma substituição do método atual usado para armazenar canais offline em cache e entregá-los ao reprodutor.

Ele é executado no lado do servidor e no lado do cliente.

**No lado do servidor**

* O conteúdo dos canais, incluindo ativos, é armazenado em cache em *`/var/contentsync`*.
* O cache é exposto aos players por meio de um manifesto que descreve o conteúdo disponível para uma exibição.

**No lado do cliente**

* O reprodutor atualiza o conteúdo com base no manifesto gerado acima.

### Benefícios do uso do SmartSync {#benefits-of-using-smartsync}

O recurso SmartSync fornece vários benefícios para o seu projeto AEM Screens, como os seguintes:

* Redução drástica dos requisitos de tráfego de rede e armazenamento no lado do servidor.
* O reprodutor baixa ativos de forma inteligente somente se o ativo estiver ausente ou tiver sido alterado.
* Otimizações de armazenamento do lado do servidor e do lado do cliente.

>[!NOTE]
>
>A Adobe recomenda o uso do SmartSync em projetos AEM Screens.

## Migração de ContentSync para SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Se você já instalou o Pacote de recursos 5 do AEM 6.3 e o Pacote de recursos 3 do AEM 6.4, é possível habilitar o SmartSync para ativos a fim de melhorar o uso do espaço em disco. Para habilitar o SmartSync, siga a seção abaixo para fazer a transição de ContentSync para SmartSync, habilitando o SmartSync.
>
>O SmartSync está disponível para o Screens Player com servidores compatíveis AEM 6.4.3 FP3.
>
>Consulte a [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) para baixar o player mais recente. A tabela a seguir descreve a versão mínima do player necessária para cada plataforma:

| **Platform** | **Versão mínima suportada do reprodutor** |
|---|---|
| Android™ | 3.3.72 |
| SO Chrome | 1.0.136 |
| Windows | 1.0.136 |

Siga as etapas abaixo para fazer a transição de ContentSync para SmartSync:

1. A migração de ContentSync para SmartSync requer a limpeza do cache ContentSync antes da ativação do SmartSync.

   Navegue até o console ContentSync a partir da sua instância usando o link ***https://localhost:4502/libs/cq/contentsync/content/console.html*** e clique em **Limpar cache**, conforme mostrado na figura abaixo:

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Todo o cache de conteúdo deve ser limpo antes da primeira utilização do SmartSync.

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** por meio da instância AEM > ícone de martelo > **Operações** > **Console da Web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Configuração do console da Web do Adobe Experience Manager** é aberto. Pesquisar por *offlinecontentservice*.

   Para pesquisar o **Serviço de conteúdo offline do Screens** propriedade, pressione **Command+F** para **Mac**, e **Ctrl+F** para **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Clique em **Salvar** para habilitar o **Serviços de conteúdo offline do Screens** propriedade e, portanto, usar SmartSync para AEM Screens.
1. Quando tiver ativado o SmartSync, navegue até o projeto e clique em **Atualizar conteúdo offline** *(na barra de ações),* conforme mostrado na figura abaixo.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
