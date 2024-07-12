---
title: Implementera fjärrkontrollen
description: Läs mer om Screens fjärrkontrollsfunktion i AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 6cb2705e-83e6-46f3-bd71-6688d7edc11f
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Använda Screens fjärrkontroll {#implementing-remote-control}

Fjärrstyrningsfunktionen gör det enklare att komma åt administratörsgränssnittet, kanalväljaren eller funktioner som Rensa cache och Läs in igen. Den ger dig även en metod för att se den lokala versionen av den inbyggda programvaran och systeminformationen om spelaren. Den här möjligheten är särskilt användbar eftersom det kan vara svårt att ansluta en mus. Du kan också använda enheter som är utom räckhåll och ännu mer om spelaren tappar kontakten med AEM. Det är också användbart när du använder Samsung RMS eftersom upplösningsskillnaden kan göra det svårt att hitta och öppna administratörsgränssnittet med en mus.

## Vanliga tangentkombinationer för fjärrstyrning {#using-common-remote-control}

På alla spelare kan du använda följande tangentkombinationer i Screens Remote Control:

1. Växla administratörsgränssnitt - CTRL + 1
1. Växla kanalväljare - CTRL + 2
1. Rensa cache - CTRL + ALT + 3
1. Ladda om spelare - CTRL + 4

## Tizen specific Remote Control Key combinations {#using-tizen-remote-control}

Specifikt för Tizen-spelaren kan du använda antingen maskinvarans fjärr- eller programvarans fjärranslutning i Samsung RMS för att få åtkomst till dessa funktioner:

1. A - Växla administratörsgränssnitt
1. B - Växla kanalväljare
1. C - Rensa cache
1. D - Läs in spelare igen

## Mer användningsinformation {#using-additional-remote-control}

1. När administratörsgränssnittet är öppet kan du använda upp- och nedpilarna för att navigera mellan flikarna och visa information på flikarna.
1. När kanalväljaren är öppen kan du använda upp- och nedpilarna för att navigera i kanalerna. Du kan också växla kanaler genom att trycka på tangenten `Enter` (eller knappen i mitten av pilarna på fjärrkontrollen).

I följande diagram visas nyckelanvändningen på en Samsung-fjärrdator:
![bild](assets/tizen/remote.png)

>[!NOTE]
>Om du anger enhetskonfigurationsvärdena för enableAdminUI och/eller enableOSD till false växlar inte fjärråtkomstgränssnittet och kanalväljaren. Du kan inte använda piltangenterna för att navigera i administratörens gränssnitt eller kanaler. Du kan dock rensa cacheminnet och läsa in spelaren igen. Du kan inaktivera fjärrkontrollsfunktionen om någon av tangentbordskombinationerna hamnar i konflikt med ditt interaktiva innehåll med den här koden:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
