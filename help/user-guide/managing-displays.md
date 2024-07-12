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
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# Skapa och hantera skärmar {#creating-and-managing-displays}

En skärm är en virtuell gruppering av skärmar som är placerade bredvid varandra. Bildskärmen är permanent med avseende på en installation. Det är det objektinnehåll som författare arbetar med och refererar alltid till som logisk visning i stället för deras fysiska motdelar.

När du skapar en plats måste du skapa en visning för platsen.

På den här sidan visas hur du skapar och hanterar visningar för Screens.

**Krav**:

* [Konfigurera och distribuera Screens](configuring-screens-introduction.md)
* [Skapa och hantera Screens Project](creating-a-screens-project.md)
* [Skapa och hantera kanaler](managing-channels.md)
* [Skapa och hantera platser](managing-locations.md)

## Skapa en ny visning {#creating-a-new-display}

>[!NOTE]
>
>Skapa en plats innan du skapar en visning. Mer information finns i [Skapa och hantera platser](managing-locations.md).

1. Navigera till lämplig plats, till exempel `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Klicka på din platsmapp och klicka på **Skapa** som finns bredvid plusikonen i åtgärdsfältet.
1. Klicka på **Visa** i guiden **Skapa** och klicka sedan på **Nästa**.
1. Ange ditt **namn** och **titel** som visningsplats.
1. Välj information om layouten på fliken **Visning**. Välj önskad **upplösning**, till exempel **Full HD**. Välj antalet enheter vågrätt och lodrätt.
1. Klicka på **Skapa**.

Visningen (*StoreDisplay*) skapas och läggs till på platsen (*SanJose*).

![visa](assets/display.gif)

När du har en skärm på plats är nästa steg att skapa en enhetskonfiguration för den aktuella skärmen.

>[!NOTE]
>
>**Nästa steg**:
>
>När du skapar en visning för din plats tilldelar du en kanal till visningen för att använda innehållet.
>
>I avsnittet [Tilldela kanaler](channel-assignment.md) finns mer information om hur du tilldelar en kanal till visningen.

## Skapa en ny enhetskonfiguration {#creating-a-new-device-config}

En enhetskonfiguration fungerar som platshållare för en faktisk digital signeringsenhet som inte är installerad än.

1. Navigera till lämplig visning, till exempel `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Klicka på din visningsmapp och klicka på **Visa instrumentpanel** i åtgärdsfältet.
1. Klicka på **+ Lägg till enhetskonfiguration** i det övre högra hörnet på panelen **Enheter**.

1. Klicka på **Enhetskonfigurationen** som önskad mall och klicka sedan på **Nästa**.

1. Ange egenskaperna efter behov och klicka på **Skapa**.

Enhetskonfigurationen skapas och läggs till i den aktuella skärmen (i följande demonstration är den nya enhetskonfigurationen *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>När en enhetskonfiguration ställs in på din skärm på platsen blir nästa steg att tilldela en kanal till din skärm.
>
>Så som visas i figuren nedan, om enhetskonfigurationen visas som ej tilldelad på panelen **DEVICES**, om ingen kanal har tilldelats den aktuella enhetskonfigurationen.
>
>Du bör ha en förhandsförståelse för att skapa och hantera kanaler. Mer information finns i [Skapa och hantera kanaler](managing-channels.md).

![chlimage_1-9](assets/chlimage_1-9.png)

## Visa instrumentpanel {#display-dashboard}

På kontrollpanelen visas olika paneler för att hantera visningsenheter. Du kan även konfigurera enheten.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Du kan klicka på kontrollpanelens listor och aktivera massåtgärder för objekt, i stället för att gå igenom varje objekt individuellt.
>
>I följande bild visas hur du kan klicka på flera kanaler från kontrollpanelen.

![cqdoc9456](assets/cqdoc9456.gif)

### Visa informationspanel {#display-information-panel}

Panelen **VISNINGSINFORMATION** innehåller visningsegenskaperna.

Klicka på (**..**) i det övre högra hörnet på panelen **VISNINGSINFORMATION** så att du kan visa egenskaperna och förhandsgranska visningen.


#### Visningsegenskaper {#viewing-properties}

Klicka på **Egenskaper** så att du kan visa eller ändra egenskaperna för visningen.

Du kan även justera händelsens timervärde för den interaktiva kanalen på fliken **Visning**. Standardvärdet är *300 sekunder*.

Använd **CRXDE Lite** för att komma åt egenskapen **idleTimeout**, det vill säga `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### Panelen Tilldelade kanaler {#assigned-channels-panel}

På panelen **TILLDELADE KANALER** visas de tilldelade kanalerna för den här enheten.


### Panelen Enheter {#devices-panel}

Panelen **ENHETER** innehåller information om enhetskonfigurationerna.

Klicka på (**..**) i det övre högra hörnet på panelen **ENHETER** så att du kan lägga till enhetskonfigurationer och uppdatera enheter.

Klicka också på enhetskonfigurationen för att visa egenskaper, tilldela en enhet eller ta bort den helt.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Nästa steg {#the-next-steps}

När du är klar med att skapa en visning för din plats tilldelar du en kanal för visningen.

Mer information finns i [Tilldela kanaler](channel-assignment.md).
