---
title: REST APIs
seo-title: REST API
description: O AEM Screens fornece uma API RESTful simples que segue a especificação Siren. Siga esta página para saber como navegar na estrutura de conteúdo e enviar comandos para dispositivos no ambiente.
seo-description: O AEM Screens fornece uma API RESTful simples que segue a especificação Siren. Siga esta página para saber como navegar na estrutura de conteúdo e enviar comandos para dispositivos no ambiente.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# REST APIs{#rest-apis}

O AEM Screens fornece uma API RESTful simples que segue a especificação [Siren](https://github.com/kevinswiber/siren) . Ele permite navegar pela estrutura do conteúdo e enviar comandos para dispositivos no ambiente.

A API pode ser acessada em [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navegação na estrutura do conteúdo {#navigating-content-structure}

O JSON retornado pelas chamadas de API lista as entidades relacionadas ao recurso atual. Após o autolink listado, cada uma dessas entidades é novamente acessível como um recurso REST.

Por exemplo, para acessar as exibições em nosso local de sinalização de demonstração, você pode chamar:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

Ou usando a curva:

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

E então para acessar a tela única, você pode chamar:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Execução de ações no recurso {#executing-actions-on-the-resource}

O JSON retornado pelas chamadas de API pode conter uma lista de ações disponíveis no recurso.

A exibição, por exemplo, lista uma ação de comando *de* transmissão que permite enviar um comando para todos os dispositivos atribuídos a essa exibição.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

Ou usando a curva:

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

Para acionar esta ação, você chamaria:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Ou usando a curva:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

