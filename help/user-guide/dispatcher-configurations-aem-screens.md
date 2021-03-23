---
title: Configurações do Dispatcher para AEM Screens
seo-title: Configurações do Dispatcher para AEM Screens
description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.
seo-description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.
feature: Administração do Screens
role: Desenvolvedor, profissional de negócios
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 6%

---


# Configurações do Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar o dispatcher para um projeto do AEM Screens.

>[!NOTE]
>
>Se um dispatcher estiver disponível, as conexões com o servlet de registro poderão ser evitadas filtrando nas regras do dispatcher.
>
>Se não houver dispatcher, desative o servlet de registro na lista de componentes OSGi.

## Pré-requisitos {#pre-requisites}

Antes de configurar o dispatcher para um projeto do AEM Screens, você deve ter conhecimento prévio do Dispatcher.

Consulte [Configuração do Dispatcher](https://docs.adobe.com/content/help/pt-BR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obter mais detalhes.

## Configurando o Dispatcher {#configuring-dispatcher}

Os players/dispositivos AEM Screens usam uma sessão autenticada para acessar os recursos nas instâncias de publicação também. Portanto, quando você tem várias instâncias de publicação, as solicitações devem sempre ir para a mesma instância de publicação, para que a sessão autenticada seja válida para todas as solicitações provenientes de players/dispositivos AEM Screens.

Siga as etapas abaixo para configurar o dispatcher para um projeto do AEM Screens.

### Ativar Sessões Aderentes {#enable-sticky-session}

Se quiser usar várias instâncias de publicação diante de um único dispatcher, será necessário atualizar o arquivo `dispatcher.any` para ativar a adesão

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se você tiver uma instância de publicação encaminhada por um dispatcher, ativar a adesão no dispatcher não ajudará, pois o balanceador de carga pode enviar cada solicitação ao dispatcher. Nesse caso, clique em **Enable** no campo **Stickiness** para ativá-lo no nível do balanceador de carga, conforme mostrado na figura abaixo:

![imagem](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por exemplo, se estiver usando o AWS ALB, consulte [Grupos de destino para seus Application Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para ativar a adesão no nível ALB. Ativar a adesão por 1 dia.

### Etapa 1: Configuração dos Cabeçalhos do Cliente {#step-configuring-client-headers}

Adicione o seguinte à seção `/clientheaders`:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Etapa 2: Configuração dos filtros do Screens {#step-configuring-screens-filters}

Para configurar os filtros do Screens, adicione o seguinte a ***/filter***.

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

Desative o armazenamento em cache do dispatcher para ***/content/screens path***.

Os players do Screens usam sessão autenticada, de modo que o dispatcher não armazena em cache nenhuma solicitação dos players de tela para `channels/assets`.

Para ativar o cache dos ativos para que os ativos sejam disponibilizados a partir do cache do dispatcher, você deve:

* Adicionar `/allowAuthorization 1` na seção `/cache`
* Adicione as regras abaixo à seção `/rules` de `/cache`

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
