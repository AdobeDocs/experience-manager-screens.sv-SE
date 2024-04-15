---
title: Skapa och hantera skärmar
description: Lär dig hur du skapar en skärm- och enhetskonfiguration i AEM Screens. Lär dig även om kontrollpanelen för visning.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# Skapa och hantera skärmar {#creating-and-managing-displays}

En skärm är en virtuell gruppering av skärmar som är placerade bredvid varandra. Bildskärmen är permanent med avseende på en installation. Det här är det objekt som författare arbetar med och refererar alltid till som logisk visning i stället för deras fysiska räknardelar.

När du skapar en plats måste du skapa en visning för platsen.

På den här sidan visas hur du skapar och hanterar skärmar.

**Krav**:

* [Konfigurera och distribuera skärmar](configuring-screens-introduction.md)
* [Skapa och hantera skärmsprojekt](creating-a-screens-project.md)
* [Skapa och hantera kanaler](managing-channels.md)
* [Skapa och hantera platser](managing-locations.md)

## Skapa en ny visning {#creating-a-new-display}

>[!NOTE]
>
>Skapa en plats innan du skapar en visning. Se [Skapa och hantera platser](managing-locations.md) för mer information.

1. Navigera till lämplig plats, till exempel `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Välj din platsmapp och välj **Skapa** bredvid plusikonen i åtgärdsfältet.
1. Välj **Visa** från **Skapa** guide, välj **Nästa**.
1. Retur **Namn** och **Titel** för din visningsplats.
1. Under **Visa** väljer du information om layouten. Välj önskat **Upplösning**, till exempel **Full HD**. Välj antalet enheter vågrätt och lodrätt.
1. Välj **Skapa**.

Visningen (*StoreDisplay*) skapas och läggs till på platsen (*SanJose*).

![visa](assets/display.gif)

När du har visat på plats är nästa steg att skapa en enhetskonfiguration för den aktuella skärmen.

>[!NOTE]
>
>**Nästa steg**:
>
>När du skapar en visning för din plats tilldelar du en kanal till visningen för att använda innehållet.
>
>Se [Tilldela kanaler](channel-assignment.md) för att lära dig hur du tilldelar en kanal till visningen.

## Skapa en ny enhetskonfiguration {#creating-a-new-device-config}

En enhetskonfiguration fungerar som platshållare för en faktisk digital signeringsenhet som inte är installerad än.

1. Navigera till lämplig visning, till exempel `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Välj visningsmapp och välj **Visa instrumentpanel** i åtgärdsfältet.
1. Välj **+ Lägg till enhetskonfiguration** överst till höger på **Enheter** -panelen.

1. Välj **Enhetskonfiguration** som önskad mall och tryck/klicka **Nästa**.

1. Ange egenskaperna efter behov och tryck/klicka **Skapa**.

Enhetskonfigurationen skapas och läggs till i den aktuella skärmen (i följande exempel är den nya enhetskonfigurationen *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>När en enhetskonfiguration ställs in på din skärm på platsen blir nästa steg att tilldela en kanal till din skärm.
>
>Så som visas i figuren nedan, om enhetskonfigurationen visas som ej tilldelad i **ENHETER** om ingen kanal har tilldelats den aktuella enhetskonfigurationen.
>
>Du bör ha en förståelse för att skapa och hantera kanaler. Se [Skapa och hantera kanaler](managing-channels.md) för mer information.

![chlimage_1-9](assets/chlimage_1-9.png)

## Visa instrumentpanel {#display-dashboard}

På kontrollpanelen visas olika paneler för att hantera visningsenheter och enhetskonfigurationer för din enhet.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Du kan välja kontrollpanelslistor och aktivera massåtgärder för objekt, i stället för att gå igenom varje objekt individuellt.
>
>I följande bild visas hur du kan välja flera kanaler från kontrollpanelen.

![cqdoc9456](assets/cqdoc9456.gif)

### Visa informationspanel {#display-information-panel}

The **VISNINGSINFORMATION** Panelen innehåller visningsegenskaperna.

Klicka (**...**) i det övre högra hörnet i **VISNINGSINFORMATION** så att du kan visa egenskaperna och förhandsgranska visningen.


#### Visningsegenskaper {#viewing-properties}

Klicka **Egenskaper** så att du kan visa eller ändra egenskaperna för visningen.

Du kan även justera händelsens timervärde för den interaktiva kanalen i **Timeout för inaktivitet** egenskap under **Visa** -fliken. Standardvärdet är *300 sekunder*.

Använd **CRXDE Lite** för att få åtkomst till **idleTimeout** property, d.v.s. `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Panelen Tilldelade kanaler {#assigned-channels-panel}

The **TILLDELADE KANALER** visas de tilldelade kanalerna för den här enheten.


### Panelen Enheter {#devices-panel}

The **ENHETER** Panelen innehåller information om enhetskonfigurationerna.

Markera (**...**) i det övre högra hörnet i **ENHETER** så att du kan lägga till enhetskonfigurationer och uppdatera enheter.

Klicka också på enhetskonfigurationen för att visa egenskaper, tilldela en enhet eller ta bort den helt.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Nästa steg {#the-next-steps}

När du är klar med att skapa en visning för din plats tilldelar du en kanal för visningen.

Se [Tilldela kanaler](channel-assignment.md) för mer information.
