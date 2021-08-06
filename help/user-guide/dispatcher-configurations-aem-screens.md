---
title: Configurações do Dispatcher para AEM Screens
seo-title: Configurações do Dispatcher para AEM Screens
description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.
seo-description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.
feature: Administração do Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 0f32fc015729685c724176c25920da6f07707c00
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 4%

---

# Configurações do Dispatcher para AEM Screens{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar o dispatcher para um projeto do AEM Screens.

>[!NOTE]
>
>Se um dispatcher estiver disponível, as conexões com o servlet de registro poderão ser evitadas filtrando nas regras do dispatcher.
>
>Se não houver dispatcher, desative o servlet de registro na lista de componentes OSGi.

Antes de configurar o dispatcher para um projeto do AEM Screens, você deve ter conhecimento prévio do Dispatcher.
Consulte [Configuração do Dispatcher](https://docs.adobe.com/content/help/pt-BR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obter mais detalhes.

## Configuração do Dispatcher para Versão do Manifesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>As seguintes configurações do Dispatcher se aplicam somente à versão do Manifesto v2. Consulte [Configurações do Dispatcher para a versão do Manifesto v3](#configuring-dispatcherv3) para obter a versão do manifesto v3.

Os players ou dispositivos AEM Screens usam uma sessão autenticada para acessar os recursos nas instâncias de publicação também. Portanto, quando você tem várias instâncias de publicação, as solicitações devem sempre ir para a mesma instância de publicação, para que a sessão autenticada seja válida para todas as solicitações provenientes de players/dispositivos AEM Screens.

Siga as etapas abaixo para configurar o dispatcher para um projeto do AEM Screens.

### Ativar sessões adesivas {#enable-sticky-session}

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

## Configurar o Dispatcher para a Versão de Manifesto v3{#configuring-dispatcherv3}

Certifique-se de permitir esses filtros e regras de cache em dispatchers que encaminham as instâncias de publicação para o funcionamento do Screens.

### Pré-requisitos para a versão do manifesto v3{#prerequisites3}

Siga estes dois pré-requisitos antes de configurar o Dispatcher (versão de manifesto v3) para o AEM Screens:

* Verifique se você está usando `v3 manifests`. Navegue até `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e verifique se `Enable ContentSync Cache` está desmarcado.

* Verifique se o agente de liberação do dispatcher está configurado em `/etc/replication/agents.publish/dispatcher1useast1Agent` na instância de publicação.

   ![imagem](/help/user-guide/assets/dispatcher/dispatcher-1.png)

   ![imagem](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtros  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Regras de cache {#cache-rules-v3}

* Adicione `/allowAuthorized "1"` à seção `/cache` em `publish_farm.any`.

* Todos os players do Screens usarão uma sessão autenticada para se conectar a AEM (criar/publicar). O Dispatcher pronto para uso não armazena esses urls em cache, portanto, devemos ativá-los.

* Adicionar `statfileslevel "10"` à seção `/cache` em `publish_farm.any`
Isso oferecerá suporte ao armazenamento em cache de até 10 níveis a partir do docroot do cache e invalidará adequadamente quando o conteúdo for publicado, em vez de invalidar tudo. Você pode alterar esse nível com base no quão profunda sua estrutura de conteúdo é

* Adicione o seguinte a `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Adicione as seguintes regras à seção `/rules` em `/cache` em `publish_farm.any` ou em um arquivo incluído de `publish_farm.any`:

   ```
   ## Don't cache CSRF login tokens
   /0001
       {
       /glob "/libs/granite/csrf/token.json"
       /type "deny"
       }
   ## Allow Dispatcher Cache for Screens channels
   /0002
       {
           /glob "/content/screens/*.html"
           /type "allow"
       }
   ## Allow Dispatcher Cache for Screens offline manifests
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   ## Allow Dispatcher Cache for Assets
   /0004
       {
   
       /glob "/content/dam/*"
       /type "allow"
       }
   ## Disable Dispatcher Cache for Screens devices json
   /0005
       {
       /glob "/home/users/screens/*.json"
       /type "deny"
       }
   ## Disable Dispatcher Cache for Screens svc json
   /0006
       {
       /glob "/content/screens/svc.json"
       /type "deny"
       }
   ```
