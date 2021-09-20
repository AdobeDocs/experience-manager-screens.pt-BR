---
title: Instalar o reprodutor do Screens
seo-title: Installing Screens Player
description: Siga esta página para saber mais sobre a instalação do AEM Screens Player disponível.
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Instalação do AEM Screens Player {#installing-player}

Esta página descreve como instalar o AEM Screens player.

## Player do Screens disponível {#available-players}

O player do AEM Screens está disponível para Android, Chrome OS e Windows.

Para baixar o **AEM Screens Player**, visite a página [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/).

>[!NOTE]
>
>Depois de baixar o Player mais recente (*.exe*), siga as etapas no player para concluir a instalação ad-hoc:
>
>1. Pressione e segure no canto superior esquerdo para abrir o painel do administrador.
>1. Navegue até **Configuration** no menu de ação esquerdo e insira o endereço de localização da instância de AEM em **Server** e clique em **Save**.
>1. Clique no link **Registration** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.


## Monitoramento básico da reprodução {#playback-monitoring}

O reprodutor relata várias métricas de reprodução com cada `ping` padrão de 30 segundos. Com base nessas métricas, podemos detectar vários casos de borda, como experiência paralisada, tela em branco e problemas de agendamento. Isso nos permite entender e solucionar problemas no dispositivo e, portanto, acelerar uma investigação e medidas corretivas.

O monitoramento básico da reprodução em um reprodutor AEM Screens permite:

* Monitore remotamente, se um reprodutor estiver reproduzindo o conteúdo corretamente.

* Melhore a reatividade em telas em branco ou em experiências quebradas no campo .

* Diminui o risco de mostrar uma experiência quebrada para o usuário final.

### Como entender as propriedades {#understand-properties}

As seguintes propriedades estão incluídas em cada `ping`:

| Propriedade | Descrição |
|---|---|
| id {string} | o identificador do reprodutor |
| ativeChannel {string} | no momento, reproduzindo o caminho do canal, ou nulo se nada estiver agendado |
| ativeElements {string} | sequência separada por vírgulas, elementos atualmente visíveis em todos os canais de sequência de reprodução (vários no caso de um layout de várias zonas) |
| isDefaultContent {boolean} | true se o canal de reprodução for considerado um canal padrão ou de fallback (ou seja, tem prioridade 1 e sem agendamento) |
| hasContentChanged {boolean} | true se o conteúdo tiver sido alterado nos últimos 5 minutos; caso contrário, false |
| lastContentChange {string} | carimbo de data e hora da última alteração de conteúdo |

>[!NOTE]
>Como opção, uma propriedade mais avançada pode ser ativada nas preferências do reprodutor (Ativar monitoramento de reprodução), ou seja:
>|Propriedade|Descrição|
>|—|—|
>|isContentRendering {boolean}|true se a GPU puder confirmar que está reproduzindo conteúdo real (com base na análise de pixel)|

### Limitações           {#limitations}

Abaixo estão listadas algumas limitações do monitoramento básico da reprodução:

* O reprodutor relata seu próprio estado de reprodução no servidor para que ele exija uma conexão ativa.

* A propriedade `isContentRendering` que verifica a GPU atualmente exige muitos recursos para ser ativada por padrão e requer aceitação explícita das preferências do reprodutor. É recomendável não usá-lo juntamente com vídeos em produção.

* Esse recurso é compatível apenas para canais de sequência e ainda não cobre o caso de uso dos canais interativos (SPA).

* As métricas ainda não estão totalmente expostas aos nossos clientes, estamos trabalhando duro para ativar o mecanismo de relatório e alerta semelhante ao painel em um futuro próximo.

### Recursos adicionais {#additional-resources}

Consulte os seguintes tópicos para obter informações detalhadas:

* Para baixar o Android Player, visite **Google Play**. Para saber mais sobre a implementação do Android Watchdog, consulte [Implementação do Android player](implementing-android-player.md).

* Para implementar o Player do Chrome OS, consulte [Console de Gerenciamento do Chrome](implementing-chrome-os-player.md) para obter mais informações.

* Para configurar o player do AEM Screens Windows, consulte [Implementação do Windows Player](implementing-windows-player.md).
