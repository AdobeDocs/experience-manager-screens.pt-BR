---
title: Instalar o reprodutor do Screens
description: Saiba como instalar corretamente um AEM Screens Player.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# Instalação do AEM Screens Player {#installing-player}

Esta página descreve como instalar o AEM Screens player.

## Player do Screens disponível {#available-players}

O AEM Screens player está disponível para Android™, Chrome OS e Windows.

Para baixar **AEM Screens Player**, visite o [Downloads do reprodutor AEM 6.5](https://download.macromedia.com/screens/) página.

>[!NOTE]
>
>Depois de baixar o Player mais recente (*.exe*), siga as etapas no reprodutor para concluir a instalação ad-hoc:
>
>1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
>1. Navegue até **Configuração** no menu de ações à esquerda e insira o endereço do local da instância do AEM em **Servidor** e clique em **Salvar**.
>1. Clique em **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.

## Monitoramento básico de reprodução {#playback-monitoring}

O reprodutor relata várias métricas de reprodução com cada `ping` que o padrão é 30 segundos. Com base nessas métricas, é possível detectar vários casos de borda, como experiência travada, tela em branco e problemas de agendamento. Isso nos permite entender e solucionar problemas no dispositivo e, portanto, agiliza uma investigação e medidas corretivas com você.

O monitoramento básico da reprodução em um reprodutor AEM Screens permite:

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
>Como opção, uma propriedade mais avançada pode ser ativada nas preferências do reprodutor (Ativar monitoramento de reprodução), ou seja:
>
>| Propriedade | Descrição |
>|---|---|
>| isContentRendering {boolean} | true se a GPU puder confirmar que está reproduzindo o conteúdo real (com base na análise de pixels) |

### Limitações {#limitations}

Algumas limitações do monitoramento básico de reprodução estão listadas abaixo:

* O reprodutor relata seu próprio estado de reprodução ao servidor, portanto, requer uma conexão ativa.

* A variável `isContentRendering` propriedade que verifica se a GPU consome muitos recursos para ser habilitada por padrão e requer aceitação explícita das preferências do reprodutor. A Adobe recomenda que você não o use com vídeos em produção.

* Esse recurso é compatível apenas com canais de sequência e ainda não abrange o caso de uso de canais interativos (SPA).

* As métricas ainda não estão totalmente expostas aos clientes. O Adobe está trabalhando para ativar mecanismos de alerta e geração de relatórios semelhantes a painéis em breve.

### Outros recursos {#additional-resources}

Consulte os seguintes tópicos para obter informações detalhadas:

* Para baixar o Android™ Player, visite **Google Play**. Para saber mais sobre como implementar o Android™ Watchdog, consulte [Implementação do Android™ player](implementing-android-player.md).

* Para implementar o Chrome OS Player, consulte [Console de gerenciamento do Chrome](implementing-chrome-os-player.md) para obter mais informações.

* Para configurar o AEM Screens Windows Player, consulte [Implementação do Windows Player](implementing-windows-player.md).
