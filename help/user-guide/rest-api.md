---
title: REST API:er
seo-title: REST API
description: AEM Screens tillhandahåller ett enkelt RESTful-API som följer Siren-specifikationen. Följ den här sidan om du vill lära dig hur du navigerar i innehållsstrukturen och skickar kommandon till enheter i miljön.
seo-description: AEM Screens tillhandahåller ett enkelt RESTful-API som följer Siren-specifikationen. Följ den här sidan om du vill lära dig hur du navigerar i innehållsstrukturen och skickar kommandon till enheter i miljön.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: Utveckla skärmar
role: Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# REST API:er{#rest-apis}

AEM Screens tillhandahåller ett enkelt RESTful-API som följer specifikationen [Siren](https://github.com/kevinswiber/siren). Det gör att du kan navigera i innehållsstrukturen och skicka kommandon till enheter i miljön.

API:t finns på [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navigera i innehållsstrukturen {#navigating-content-structure}

Den JSON som returneras av API-anropen listar entiteter som är relaterade till den aktuella resursen. Efter den listade självlänken är var och en av dessa enheter tillgängliga som en REST-resurs igen.

Om du till exempel vill komma åt skärmarna på vår demoflaggplats kan du ringa:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

Eller använd vändning:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

Resultatet skulle se ut så här:

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

Sedan kan du ringa:

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Kör åtgärder på resursen {#executing-actions-on-the-resource}

Den JSON som returneras av API-anropen kan innehålla en lista över åtgärder som är tillgängliga för resursen.

Visningen innehåller till exempel en *broadcast-command*-åtgärd som gör att du kan skicka ett kommando till alla enheter som är tilldelade den visningen.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

Eller använd vändning:

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Resultat:***

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

Om du vill utlösa den här åtgärden anropar du:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Eller använd vändning:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

