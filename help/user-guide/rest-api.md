---
title: REST API:er
description: Läs om hur AEM Screens tillhandahåller ett enkelt RESTful-API som följer Siren-specifikationen. Lär dig även hur du navigerar i innehållsstrukturen och skickar kommandon till enheter i miljön.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: ac01935a-c3ff-485a-b60e-227fb94c75b0
source-git-commit: 43e89ddc3eb6baffca75d730a978e60e234aaee4
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# REST API:er{#rest-apis}

AEM Screens tillhandahåller ett enkelt RESTful-API som följer [Siren](https://github.com/kevinswiber/siren) -specifikation. Du kan navigera i innehållsstrukturen och skicka kommandon till enheter i miljön.

API:t finns på [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Navigera i innehållsstrukturen {#navigating-content-structure}

Den JSON som returneras av API-anropen listar entiteter som är relaterade till den aktuella resursen. Efter den listade självlänken är dessa enheter tillgängliga igen som en REST-resurs.

Om du till exempel vill komma åt skärmarna på demoflaggans plats kan du anropa följande:

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

## Köra åtgärder på resursen {#executing-actions-on-the-resource}

Den JSON som returneras av API-anropen kan innehålla en lista över åtgärder som är tillgängliga för resursen.

Visningen visar till exempel en *broadcast-command* åtgärd som gör att du kan skicka ett kommando till alla enheter som är tilldelade den visningen.

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

Om du vill aktivera den här åtgärden anropar du följande:

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Eller använd vändning:

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
