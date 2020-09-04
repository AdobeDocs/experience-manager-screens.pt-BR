---
title: Configurações do Dispatcher para AEM Screens
seo-title: Configurações do Dispatcher para AEM Screens
description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto da AEM Screens.
seo-description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto da AEM Screens.
translation-type: tm+mt
source-git-commit: 4a1fb81fa343983093590c36ccb6a4fd110cdad2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 9%

---


# Configurações do Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar o dispatcher para um projeto da AEM Screens.

>[!NOTE]
>
>Se um dispatcher estiver disponível, as conexões com o servlet de registro podem ser impedidas filtrando nas regras do dispatcher.
>
>Se não houver despachante, desative o servlet de registro na lista de componentes OSGi.

## Pré-requisitos {#pre-requisites}

Antes de configurar o dispatcher para um projeto da AEM Screens, você deve ter conhecimento prévio do Dispatcher.

Consulte [Configuração do Dispatcher](https://docs.adobe.com/content/help/pt-BR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obter mais detalhes.

## Configurando o Dispatcher {#configuring-dispatcher}

Siga as etapas abaixo para configurar o dispatcher para um projeto da AEM Screens.

### Habilitar Sessões Aderentes {#enable-sticky-session}

Se você quiser usar mais de uma instância de publicação com o dispatcher, será necessário atualizar o `dispatcher.any` arquivo.

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### Etapa 1: Configurando cabeçalhos do cliente {#step-configuring-client-headers}

Adicione o seguinte à `/clientheaders`seção:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Etapa 2: Configuração de Filtros do Screens {#step-configuring-screens-filters}

Para configurar filtros do Screens, adicione o seguinte a ***/filtre***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Etapa 3: Desabilitando o Cache do Dispatcher {#step-disabling-dispatcher-cache}

Desative o cache do dispatcher para ***/content/screens path***.

Os players de telas usam uma sessão autenticada, de modo que o dispatcher não armazena em cache nenhuma solicitação dos players de telas para `channels/assets`.

Para ativar o cache dos ativos para que os ativos sejam servidos do cache do dispatcher, você deve:

* Adicionar `/allowAuthorization 1` na `/cache` seção
* Adicione as regras abaixo à `/rules` seção de `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
