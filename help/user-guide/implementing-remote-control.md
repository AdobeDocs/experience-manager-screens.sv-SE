---
title: Implementera fjärrkontrollen
seo-title: Impementing the Remote Control
description: Följ den här sidan om du vill veta mer om funktionen Fjärrkontroll för skärmar.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: a256f624c4b647deb4cee7668665ad7b576932e7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Använda fjärrkontrollen till skärmar  {#implementing-remote-control}

Fjärrstyrningsfunktionen gör det enklare att komma åt administratörsgränssnittet, kanalväljaren eller funktioner som Rensa cache och Läs in igen. Dessutom får du en metod för att se den lokala versionen av den inbyggda programvaran och systeminformationen om spelaren. Detta är särskilt användbart eftersom det kan vara svårt att ansluta en mus och arbeta på produktionsenheter som är utom räckhåll och ännu mer om spelaren tappar kontakten med AEM. Detta är också användbart när du använder Samsung RMS eftersom upplösningsskillnaden kan göra det mycket svårt att hitta och öppna administratörsgränssnittet med en mus.

## Vanliga tangentkombinationer för fjärrstyrning {#using-common-remote-control}

På alla spelare kan du använda följande tangentkombinationer i Fjärrstyrning för skärmar:

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

## Ytterligare användningsinformation {#using-additional-remote-control}

1. När administratörsgränssnittet är öppet kan du använda upp- och nedpilarna för att navigera mellan flikarna och visa information på flikarna.
1. När kanalväljaren är öppen kan du använda upp- och nedpilarna för att navigera i kanalerna och du kan trycka på Retur-tangenten (eller knappen i mitten av pilarna på fjärrkontrollen) för att växla kanaler.

I följande diagram visas nyckelanvändningen på en Samsung-fjärrdator:
![image](assets/tizen/remote.png)

>[!NOTE]
>Om du anger enhetskonfigurationsvärdena för enableAdminUI och/eller enableOSD till false växlar inte fjärråtkomstgränssnittet och kanalväljaren. Du kan inte heller använda piltangenterna för att navigera i administratörens gränssnitt eller kanaler. Du kan dock fortfarande rensa cache och läsa in spelaren igen. Du kan inaktivera fjärrkontrollsfunktionen om någon av tangentbordskombinationerna hamnar i konflikt med ditt interaktiva innehåll med den här koden:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
