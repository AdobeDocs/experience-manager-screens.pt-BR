---
title: REST APIs
seo-title: REST API
description: A AEM Screens fornece uma API RESTful simples que segue a especificação Siren. Siga esta página para saber como navegar pela estrutura de conteúdo e enviar comandos para dispositivos no ambiente.
seo-description: A AEM Screens fornece uma API RESTful simples que segue a especificação Siren. Siga esta página para saber como navegar pela estrutura de conteúdo e enviar comandos para dispositivos no ambiente.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# REST APIs{#rest-apis}

O AEM Screens fornece uma API RESTful simples que segue a especificação [Siren](https://github.com/kevinswiber/siren). Ele permite navegar pela estrutura de conteúdo e enviar comandos para dispositivos no ambiente.

A API pode ser acessada em [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Estrutura de conteúdo de navegação {#navigating-content-structure}

O JSON retornado pelas chamadas de API lista as entidades relacionadas ao recurso atual. Após o autolink listado, cada uma dessas entidades é novamente acessível como um recurso REST.

Por exemplo, para acessar as exibições em nosso local de sinalização de demonstração, você pode chamar:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

Ou usando curl:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

O resultado seria:

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

E, para acessar o Single Screen Display, você pode chamar:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Executando Ações no Recurso {#executing-actions-on-the-resource}

O JSON retornado pelas chamadas de API pode conter uma lista de ações disponíveis no recurso .

A exibição, por exemplo, lista uma ação *transmissão-comando* que permite enviar um comando para todos os dispositivos atribuídos a essa exibição.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

Ou usando curl:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Resultado:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

Para acionar essa ação, é necessário chamar:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Ou usando curl:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

