---
title: Configurações do Dispatcher para o AEM Screens
seo-title: Dispatcher Configurations for AEM Screens
description: Esta página destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.
seo-description: This page highlights guidelines for configuring dispatcher for an AEM Screens project.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Configurações do Dispatcher para o AEM Screens{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar o dispatcher para um projeto do AEM Screens.

>[!NOTE]
>
>Se um dispatcher estiver disponível, as conexões com o servlet de registro podem ser evitadas filtrando as regras do dispatcher.
>
>Se não houver um dispatcher, desative o servlet de registro na lista de componentes OSGi.

Antes de configurar o Dispatcher para um projeto do AEM Screens, você deve ter conhecimento prévio do Dispatcher.
Consulte [Configuração do Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) para obter mais detalhes.

## Configuração do Dispatcher para Versão de Manifesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>As seguintes configurações do Dispatcher se aplicam somente à versão Manifest v2. Consulte [Configurações do Dispatcher para a versão Manifest v3](#configuring-dispatcherv3) para a versão do manifesto v3.

Os players ou dispositivos da AEM Screens usam a sessão autenticada para acessar os recursos nas instâncias de publicação também. Portanto, quando você tem várias instâncias de publicação, as solicitações devem sempre ir para a mesma instância de publicação, para que a sessão autenticada seja válida para todas as solicitações provenientes de players/dispositivos do AEM Screens.

Siga as etapas abaixo para configurar o dispatcher para um projeto do AEM Screens.

### Ativar sessões adesivas {#enable-sticky-session}

Se quiser usar várias instâncias de publicação com um único dispatcher, será necessário atualizar o `dispatcher.any` arquivo para ativar a adesão

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se você tiver uma instância de publicação com um dispatcher, ativar a adesão no dispatcher não ajudará, pois o balanceador de carga poderá enviar cada solicitação para o dispatcher. Nesse caso, clique em **Ativar** in **Fixação** para ativá-lo no nível do balanceador de carga, conforme mostrado na figura abaixo:

![imagem](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por exemplo, se estiver usando o AWS ALB, consulte [Grupos alvo para seus Balanceadores de carga de aplicativo](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para permitir a adesão ao nível ALB. Ative a aderência por 1 dia.

### Etapa 1: Configurar Cabeçalhos do Cliente {#step-configuring-client-headers}

Adicione o seguinte a `/clientheaders`seção:

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Etapa 2: configuração dos filtros do Screens {#step-configuring-screens-filters}

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

### Etapa 3: Desabilitação do cache do Dispatcher {#step-disabling-dispatcher-cache}

Desativar o cache do dispatcher para ***Caminho de /content/screens***.

Os players do Screens usam uma sessão autenticada, de modo que o dispatcher não armazena em cache nenhuma solicitação de players do Screens `channels/assets`.

Para ativar o cache dos ativos de forma que os ativos sejam fornecidos pelo cache do Dispatcher, você deve:

* Adicionar `/allowAuthorization 1` in `/cache` seção
* Adicione as regras abaixo a `/rules` seção de `/cache`

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

## Configuração do Dispatcher para Versão de Manifesto v3{#configuring-dispatcherv3}

Permita esses filtros e regras de cache nos dispatchers que antecedem as instâncias de publicação para o funcionamento do Screens.

### Pré-requisitos para a versão Manifest v3{#prerequisites3}

Siga estes dois pré-requisitos antes de configurar o Dispatcher (versão do manifesto v3) para o AEM Screens:

* Verifique se você está usando `v3 manifests`. Navegue até `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e assegurar que `Enable ContentSync Cache` está desmarcada.

* Verifique se o agente de limpeza do dispatcher está configurado em `/etc/replication/agents.publish/dispatcher1useast1Agent` na instância de publicação.

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

* Adicionar `/allowAuthorized "1"` para `/cache` seção em `publish_farm.any`.

* Todos os players do Screens usarão uma sessão autenticada para se conectar ao AEM (autor/publicação). O Dispatcher pronto para uso não armazena em cache esses urls, portanto, devemos habilitá-los.

* Adicionar `statfileslevel "10"` para `/cache` seção em `publish_farm.any`
Isso suportará o armazenamento em cache de até 10 níveis do docroot do cache e a invalidação será realizada de acordo quando o conteúdo for publicado, em vez de invalidar tudo. Você pode alterar esse nível com base na profundidade da estrutura do conteúdo

* Adicione o seguinte a `/invalidate section in publish_farm.any`

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Adicione as seguintes regras a `/rules` seção em `/cache` in `publish_farm.any` ou em um arquivo incluído de `publish_farm.any`:

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

### Adicionar regra de invalidação para segments.js {#invalidsegmentjs}

Se você estiver usando campanhas direcionadas com o AEM Screens, a variável `segments.js file` distribuído pelo dispatcher precisa ser invalidado, à medida que você adiciona e publica novos segmentos no AEM. Sem essa regra de invalidação, as novas campanhas direcionadas não funcionarão no reprodutor do Screens (em vez disso, ele mostrará o conteúdo padrão).

* Adicionar uma regra de invalidação a `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Esta é a regra a ser adicionada:

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Essa regra garante a `segments.js` o arquivo é invalidado e o último é buscado quando modificado.
