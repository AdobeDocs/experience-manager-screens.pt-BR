---
title: Instalar o reprodutor do Screens
description: Saiba como instalar um AEM Screens Player corretamente.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# Instalação do AEM Screens Player {#installing-player}

Esta página descreve como instalar o AEM Screens Player.

## Screens Player disponível {#available-players}

O AEM Screens Player está disponível para Android™, Chrome OS e Windows.

Para baixar o **AEM Screens Player**, visite a página [Downloads do AEM 6.5 Player](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Depois de baixar o Player mais recente (*.exe*), siga as etapas no player para concluir a instalação ad-hoc:
>
>1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
>1. Navegue até **Configuração** no menu de ações esquerdo e digite o endereço do local da instância do AEM no **Servidor** e clique em **Salvar**.
>1. Clique no link **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.

## Monitoramento básico de reprodução {#playback-monitoring}

O player relata várias métricas de reprodução a cada `ping` que assume o padrão de 30 segundos. Com base nessas métricas, é possível detectar vários casos de borda, como experiência travada, tela em branco e problemas de agendamento. Ele nos permite compreender e solucionar problemas no dispositivo e, portanto, agiliza uma investigação e medidas corretivas para você.

O monitoramento básico de reprodução em um AEM Screens Player permite que você:

* Monitorar remotamente se um player estiver reproduzindo conteúdo corretamente.

* Melhore a reatividade para telas em branco ou experiências com falha no campo.

* Diminui o risco de mostrar uma experiência quebrada ao usuário final.

### Noções básicas sobre propriedades {#understand-properties}

As seguintes propriedades estão incluídas em cada `ping`:

| Propriedade | Descrição |
|---|---|
| id {string} | o identificador do reprodutor |
| ativeChannel {string} | caminho de canal em execução no momento, ou nulo se nada estiver agendado |
| ativeElements {string} | strings separadas por vírgulas, elementos visíveis atualmente em todos os canais de sequência de reprodução (vários no há um layout de várias zonas) |
| isDefaultContent {boolean} | true se o canal de reprodução for considerado um canal padrão ou de fallback (ou seja, tiver prioridade 1 e nenhum agendamento) |
| hasContentChanged {boolean} | true se o conteúdo foi alterado nos últimos 5 minutos; caso contrário, false |
| lastContentChange {string} | carimbo de data e hora da última alteração de conteúdo |

>[!NOTE]
>
>Como opção, uma propriedade mais avançada pode ser ativada nas preferências do reprodutor (Ativar monitoramento de reprodução), ou seja:
>
>| Propriedade | Descrição |
>|---|---|
>| isContentRendering {boolean} | true se a GPU puder confirmar que está reproduzindo o conteúdo real (com base na análise de pixels) |

### Limitações {#limitations}

Algumas limitações para o monitoramento básico da reprodução estão listadas abaixo:

* O reprodutor relata seu próprio estado de reprodução ao servidor, portanto, requer uma conexão ativa.

* A propriedade `isContentRendering` que verifica a GPU consome muito mais recursos para ser habilitada por padrão e requer aceitação explícita das preferências do reprodutor. A Adobe recomenda que você não o use com vídeos em produção.

* Esse recurso é compatível apenas com canais de sequência e ainda não abrange o caso de uso de canais interativos (SPA).

* As métricas ainda não estão totalmente expostas aos clientes, mas a Adobe está trabalhando para ativar mecanismos de alerta e geração de relatórios semelhantes a painéis em breve.

### Outros recursos {#additional-resources}

Consulte os seguintes tópicos para obter informações detalhadas:

* Para baixar o Android™ Player, visite **Google Play**. Para saber mais sobre como implementar o Android™ Watchdog, consulte [Implementação do Android™ Player](implementing-android-player.md).

* Para implementar o Chrome OS Player, consulte [Console de Gerenciamento do Chrome](implementing-chrome-os-player.md) para obter mais informações.

* Para configurar o AEM Screens Windows Player, consulte [Implementação do Windows Player](implementing-windows-player.md).
