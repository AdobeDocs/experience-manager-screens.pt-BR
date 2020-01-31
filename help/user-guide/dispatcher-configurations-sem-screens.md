---
title: Configurações do Dispatcher para telas AEM
seo-title: Configurações do Dispatcher para telas AEM
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: dbc20693481e6f6f379eb93bbf40ed9961589d00

---


# Configurações do Dispatcher para telas AEM{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar o dispatcher para um projeto do AEM Screens.

>[!NOTE]
>Se um dispatcher estiver disponível, as conexões com o servlet de registro podem ser impedidas filtrando nas regras do dispatcher.
>Se não houver despachante, desative o servlet de registro na lista de componentes OSGi.

## Pré-requisitos {#pre-requisites}

Antes de configurar o dispatcher para um projeto do AEM Screens, você deve ter conhecimento prévio do Dispatcher.

Consulte [Configuração do Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obter mais detalhes.

## Configurando o Dispatcher {#configuring-dispatcher}

Siga as etapas abaixo para configurar o dispatcher para um projeto do AEM Screens.

### Etapa 1: Configurando cabeçalhos do cliente {#step-configuring-client-headers}

Adicionar o seguinte à `/clientheaders` seção

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Etapa 2: Configuração de filtros de tela {#step-configuring-screens-filters}

Para configurar os filtros de Telas, adicione o seguinte a ***/filtre ***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Etapa 3: Desabilitando o Cache do Dispatcher {#step-disabling-dispatcher-cache}

Desative o cache do dispatcher para ***/content/screens path ***.
