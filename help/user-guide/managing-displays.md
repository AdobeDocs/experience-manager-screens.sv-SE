---
title: Skapa och hantera skärmar
seo-title: Hantera skärmar
description: Följ den här sidan om du vill veta mer om hur du skapar en ny skärm- och enhetskonfiguration. Lär dig dessutom om kontrollpanelen för visning.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar en ny skärm- och enhetskonfiguration. Lär dig dessutom om kontrollpanelen för visning.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Skapa och hantera skärmar {#creating-and-managing-displays}

En skärm är en virtuell gruppering av skärmar som vanligtvis placeras bredvid varandra. Bildskärmen är vanligtvis permanent när det gäller en installation. Detta blir det objekt som författare ska arbeta med och alltid referera till som logisk visning i stället för deras fysiska räknardel.

När du har skapat en plats måste du skapa en ny visning för platsen.

På den här sidan visas hur du skapar och hanterar skärmar.

**Krav**:

* [Konfigurera och distribuera skärmar](configuring-screens-introduction.md)
* [Skapa och hantera skärmsprojekt](creating-a-screens-project.md)
* [Skapa och hantera kanaler](managing-channels.md)
* [Skapa och hantera platser](managing-locations.md)

## Skapa en ny visning {#creating-a-new-display}

>[!NOTE]
>
>Du måste skapa en plats innan du skapar en visning. Mer information om hur du skapar en plats finns i [Skapa och hantera platser](managing-locations.md) .

Följ stegen nedan för att skapa en ny visning på din plats:

1. Navigera till lämplig plats, till exempel `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Välj din platsmapp och tryck/klicka på **Skapa** bredvid plusikonen i åtgärdsfältet. En guide öppnas.
1. Välj **Visning** i guiden **Skapa** och klicka på **Nästa**.

1. Ange **namn** och **titel** för visningsplatsen.

1. Välj information om layouten på fliken **Visa** . Välj önskad **upplösning** (till exempel som **Full HD**). Dessutom kan du välja antalet enheter vågrätt och lodrätt.

1. Klicka på **Skapa**.

Visningen (*StoreDisplay*) skapas och läggs till på platsen (*SanJose*).

![visa](assets/display.gif)

När du har visat på plats är nästa steg att skapa en enhetskonfiguration för den aktuella skärmen. Följ avsnittet nedan för att skapa en ny enhetskonfiguration.

>[!NOTE]
>
>**Nästa steg**:
>
>När du har skapat en visning för din plats måste du tilldela en kanal till din skärm för att kunna utnyttja innehållet.
>
>Mer information om hur du tilldelar en kanal till visningen finns i avsnittet [Tilldela kanaler](channel-assignment.md) .

## Skapa en ny enhetskonfiguration {#creating-a-new-device-config}

En enhetskonfiguration fungerar som platshållare för en faktisk digital signeringsenhet som inte är installerad än.

Följ stegen nedan för att skapa en ny enhetskonfiguration:

1. Navigera till lämplig visning, till exempel `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Markera visningsmappen och tryck/klicka på **Visa instrumentpanel** i åtgärdsfältet.
1. Tryck/klicka på **+ Lägg till enhetskonfiguration** högst upp till höger på panelen **Enheter** .

1. Välj **enhetskonfigurationen** som önskad mall och tryck/klicka på **Nästa**.

1. Ange egenskaperna efter behov och tryck/klicka på **Skapa**.

Enhetskonfigurationen skapas och läggs till i den aktuella skärmen (i följande demonstration är den nya enhetskonfigurationen *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

När en enhetskonfiguration är inställd på din skärm på platsen blir nästa steg att tilldela en kanal till din skärm.

>[!NOTE]
>
>När en enhetskonfiguration är inställd på din skärm på platsen blir nästa steg att tilldela en kanal till din skärm.
>
>Så som visas i figuren nedan, om enhetskonfigurationen visas som ej tilldelad på **enhetspanelen** , om ingen kanal har tilldelats den aktuella enhetskonfigurationen.
>
>Du bör ha en förståelse för att skapa och hantera kanaler. Mer information finns i [Skapa och hantera kanaler](managing-channels.md) .

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

Panelen **VISNINGSINFORMATION** innehåller visningsegenskaperna.

Klicka på (**...**) i det övre högra hörnet i panelen **VISNINGSINFORMATION **för att visa egenskaperna och förhandsgranska visningen.

![chlimage_1-10](assets/chlimage_1-10.png)

#### Visningsegenskaper {#viewing-properties}

Klicka på **Egenskaper** för att visa eller ändra egenskaperna för visningen.

Dessutom kan du justera händelsens timervärde för den interaktiva kanalen i **Inaktiv timeout **property under **fliken Display** . Standardvärdet är *300 sekunder*.

Använd **CRXDE Lite** för att komma åt egenskapen **idleTimeout** , d.v.s. `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### Panelen Tilldelade kanaler {#assigned-channels-panel}

På panelen **TILLDELADE KANALER** visas de tilldelade kanalerna för den här enheten.

![chlimage_1-11](assets/chlimage_1-11.png)

### Panelen Enheter {#devices-panel}

Panelen **ENHETER** innehåller information om enhetskonfigurationerna.

Klicka på (**...**) i det övre högra hörnet i panelen **DEVICES **för att lägga till enhetskonfigurationer och uppdatera enheter.

![chlimage_1-12](assets/chlimage_1-12.png)

Klicka dessutom på enhetskonfigurationen för att visa egenskaper, tilldela en enhet eller ta bort den helt.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Nästa steg {#the-next-steps}

När du är klar med att skapa en visning för din plats måste du tilldela en kanal för din visning.

Mer information finns i [Tilldela kanaler](channel-assignment.md) .