---
title: Configurações do Dispatcher para o AEM Screens
description: Esta página destaca as diretrizes para configurar uma Dispatcher para um projeto do AEM Screens.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Configurações do Dispatcher para o AEM Screens{#dispatcher-configurations-for-aem-screens}

O Dispatcher é a ferramenta de armazenamento em cache, balanceamento de carga ou ambos do Adobe Experience Manager.

A página a seguir fornece as diretrizes para configurar uma Dispatcher para um projeto do AEM Screens.

>[!NOTE]
>
>Se uma Dispatcher estiver disponível, as conexões com o servlet de registro podem ser evitadas ao filtrar as regras do Dispatcher.
>
>Se não houver Dispatcher, desative o servlet de registro na lista de componentes OSGi.

Antes de configurar o Dispatcher para um projeto do AEM Screens, tenha conhecimento prévio do Dispatcher.
Consulte [Configurando o Dispatcher](https://experienceleague.adobe.com/br/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration) para obter mais detalhes.

## Configuração do Dispatcher para a versão de manifesto v2 {#configuring-dispatcher}

>[!IMPORTANT]
>As configurações do Dispatcher a seguir se aplicam somente à versão Manifest v2. Consulte [Configurações do Dispatcher para a versão do Manifesto v3](#configuring-dispatcherv3) para a versão do Manifesto v3.

Os players ou dispositivos da AEM Screens usam uma sessão autenticada para acessar os recursos nas instâncias de publicação também. Quando você tem várias instâncias de publicação, as solicitações devem sempre ir para a mesma instância de publicação para que a sessão autenticada seja válida para todas as solicitações provenientes de players ou dispositivos do AEM Screens.

Siga as etapas abaixo para configurar a Dispatcher para um projeto do AEM Screens.

### Ativar sessões adesivas {#enable-sticky-session}

Se quiser usar várias instâncias de publicação com base em um único Dispatcher, atualize o arquivo `dispatcher.any` para habilitar a adesão.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Se você tiver uma instância de publicação frente a uma Dispatcher, ativar a adesão no Dispatcher não ajuda, pois o balanceador de carga pode enviar cada solicitação para o Dispatcher. Nesse caso, clique no campo **Habilitar** em **Fixação** para ativá-lo no nível do balanceador de carga, conforme mostrado na figura abaixo:

![imagem](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Por exemplo, se você estiver usando o AWS ALB, consulte [Grupos de destino para seus Balanceadores de Carga de Aplicativo](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) para ativar a adesão no nível ALB. Ative a aderência por um dia.

### Etapa 1: Configurar Cabeçalhos do Cliente {#step-configuring-client-headers}

Adicionar o seguinte à seção `/clientheaders`:

**X-Solicitado-Com**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Etapa 2: configuração de filtros do Screens {#step-configure-screens-filters}

Para configurar filtros Screens, adicione o seguinte a ***`/filter`***.

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

### Etapa 3: desabilitação do cache do Dispatcher {#step-disabling-dispatcher-cache}

Desabilite o cache do Dispatcher para ***/content/screens path***.

Os players do Screens usam sessões autenticadas, portanto, o Dispatcher não armazena em cache nenhuma solicitação de players de telas para `channels/assets`.

Para ativar o cache dos ativos para que os ativos sejam fornecidos pelo cache do Dispatcher, faça o seguinte:

* Adicionar `/allowAuthorization 1` na seção `/cache`
* Adicionar as regras abaixo à seção `/rules` de `/cache`

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

## Configuração do Dispatcher para a versão de manifesto v3{#configuring-dispatcherv3}

Permita esses filtros e regras de cache nos dispatchers que lidam com as instâncias de publicação para o funcionamento do Screens.

### Pré-requisitos para a versão Manifest v3{#prerequisites3}

Siga estes dois pré-requisitos antes de configurar um Dispatcher (versão manifest v3) para o AEM Screens:

* Verifique se você está usando o `v3 manifests`. Navegue até `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` e certifique-se de que `Enable ContentSync Cache` esteja desmarcado.

* Verifique se o agente de liberação do Dispatcher está configurado em `/etc/replication/agents.publish/dispatcher1useast1Agent` na instância de publicação.

  ![imagem](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![imagem](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtros {#filter-v3}

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

* Adicionar `/allowAuthorized "1"` à seção `/cache` em `publish_farm.any`.

* Todos os players do AEM Screens usam uma sessão autenticada para se conectar ao AEM (autor/publicação). Por padrão, uma Dispatcher não armazena em cache esses URLs, portanto, você deve ativá-los.

* Adicionar `statfileslevel "10"` à seção `/cache` em `publish_farm.any`
Essa regra oferece suporte ao armazenamento em cache de até dez níveis do docroot do cache e à invalidação apropriada quando o conteúdo é publicado, em vez de invalidar tudo. Você pode alterar esse nível com base na profundidade da estrutura do conteúdo

* Adicionar o seguinte a `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Adicionar as seguintes regras à seção `/rules` em `/cache` em `publish_farm.any` ou em um arquivo incluído de `publish_farm.any`:

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

Se você estiver usando campanhas direcionadas com o AEM Screens, o `segments.js file` distribuído pela Dispatcher deverá ser invalidado, à medida que você adiciona e publica novos segmentos no AEM. Sem essa regra de invalidação, as novas campanhas direcionadas não funcionarão no AEM Screens Player (ele mostra o conteúdo padrão).

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

* Esta regra garante que o arquivo `segments.js` seja invalidado e a última regra seja buscada quando modificado.
