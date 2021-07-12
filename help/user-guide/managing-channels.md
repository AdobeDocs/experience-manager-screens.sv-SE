---
title: Skapa och hantera kanaler
seo-title: Hantera kanaler
description: Följ den här sidan om du vill veta mer om hur du skapar och hanterar kanaler. Den förklarar även kanalkontrollpanelen och redigerar innehåll för en kanal.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar och hanterar kanaler. Den förklarar även kanalkontrollpanelen och redigerar innehåll för en kanal.
feature: Redigeringsskärmar
role: Admin, Developer
level: Intermediate
exl-id: 7bbd211a-f54f-42b9-a1b3-516efe6fb579
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 0%

---

# Skapa och hantera kanaler {#creating-and-managing-channels}

En kanal visar en innehållssekvens (bilder och videoklipp) och visar även en webbplats eller ett enkelsidigt program.

På den här sidan visas hur du skapar och hanterar kanaler för AEM Screens.

**Krav**:

* [Konfigurera och distribuera skärmar](configuring-screens-introduction.md)
* [Skapa och hantera skärmsprojekt](creating-a-screens-project.md)

## Skapa en ny kanal {#creating-a-new-channel}

När du har skapat ditt projekt för AEM Screens följer du stegen nedan för att skapa en ny kanal för ditt projekt:

1. Klicka på länken Adobe Experience Manager (längst upp till vänster) och sedan på Skärmar. Du kan också navigera direkt till `https://localhost:4502/screens.html/content/screens`.

1. Navigera till ditt skärmsprojekt och välj mappen **Kanaler**.

1. Klicka på **Skapa** i åtgärdsfältet.

   ![demochannel](assets/create-channel1.png)

1. Välj mallen **Sekvenskanal** i guiden **Skapa** och klicka på **Nästa**.

   ![demochannel](assets/create-channel2.png)

1. Ange titeln som **ScreensChannel** och klicka på **Skapa**.

   ![demochannel](assets/create-project4.png)

1. En sekvenskanal har nu lagts till i mappen **Kanaler**.

### Kanaltyper {#channel-types}

Följande mallalternativ är tillgängliga när du använder guiden, till exempel:

| **Mallalternativ** | **Beskrivning** |
|---|---|
| Mappen Kanaler | Gör att du kan skapa en mapp för lagring av kanalsamlingar. |
| Sekvenskanal | Gör att du kan skapa en kanal som spelar upp komponenterna sekventiellt (en i taget i ett bildspel). |
| Programkanal | Gör att du kan visa ditt anpassade webbprogram i skärmspelaren. |
| 1x1 Delad skärmkanal | Gör att komponenten kan visas i en enda zon. |
| 1x2 Delad skärmkanal | Gör att resurserna kan visas i två zoner (delas vågrätt). |
| 2X1 Delad skärmkanal | Gör att resurserna kan visas i två zoner (lodrätt uppdelade). |
| 2x2 Delad skärmkanal | Gör det möjligt att visa resurserna i fyra zoner (dela vågrätt och lodrätt i en matris). |
| 2 till 3 kanaler för delad skärm | Gör att resurserna kan visas i två zoner (delas vågrätt) där en av zonerna är större än den andra. |
| Vänster eller höger L-streckkanal för delad skärm | Innehållsförfattare kan visa olika typer av resurser i zoner med lämplig storlek. |

>[!NOTE]
>
>Kanalerna för delad skärm delar upp visningen i flera zoner så att du kan spela upp flera upplevelser samtidigt, sida vid sida. Upplevelserna kan antingen vara statiska resurser/text eller inbäddade sekvenser.

>[!IMPORTANT]
>
> När du har skapat och lagt till innehåll i kanalen är nästa steg att skapa en plats följt av att skapa en skärm. Dessutom måste du tilldela den kanalen till en skärm. Läs mer i resurserna nedan i slutet av avsnittet.

## Arbeta med kanaler {#working-with-channels}

Du kan redigera, visa egenskaper och kontrollpanel, kopiera, förhandsgranska och ta bort en kanal.


![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Lägga till/redigera innehåll i en kanal {#adding-editing-content-to-a-channel}

Följ stegen nedan om du vill lägga till eller redigera innehåll i en kanal:

1. Markera kanalen som du vill redigera (se bilden ovan).
1. Klicka på **Redigera** i det övre vänstra hörnet av åtgärdsfältet för att redigera kanalegenskaperna. Redigeraren öppnas och du kan lägga till resurser/komponenter i kanalen som du vill publicera.

>[!NOTE]
>Du kan lägga till komponenter i kanalen. Mer information finns i **[Lägga till komponenter i en kanal](adding-components-to-a-channel.md)**.

![demochannel1](assets/demochannel1.gif)

**Överföra videoklipp till kanalen**

Följ stegen nedan för att överföra videoklipp till din kanal:

1. Markera kanalen där du vill överföra videon.
1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
1. Välj **Videofilmer** under Resurser och dra och släpp önskade videoklipp.

>[!NOTE]
>Om du får problem med att överföra videoklipp i din kanal kan du läsa [Felsöka videoklipp](troubleshoot-videos.md).

### Visningsegenskaper {#viewing-properties}

Följ stegen nedan om du vill visa eller redigera egenskaper för en kanal:

1. Klicka på den kanal som du vill redigera.
1. Klicka på **Egenskaper** i åtgärdsfältet för att visa/redigera kanalegenskaperna. På följande flikar kan du ändra alternativen.

![egenskaper](assets/properties.gif)

### Visa instrumentpanel {#viewing-dashboard}

Följ stegen nedan för att visa kontrollpanelen för en kanal:

1. Markera kanalen som du vill redigera.
1. Klicka på **Kontrollpanel** i åtgärdsfältet för att visa instrumentpanelen. Panelen **KANALINFORMATION**,**TILLDELADE VISNINGAR** och **VÄNTANDE LAUNCHES** öppnas, vilket visas i figuren nedan:

![kontrollpanel](assets/dashboard.gif)

### Kanalinformation {#channel-information}

Panelen Kanalinformation beskriver kanalegenskaperna tillsammans med förhandsvisningen av kanalen. Dessutom innehåller det information om huruvida kanalen är offline eller online.

Klicka på (**)..**) i **KANALINFORMATION**-åtgärdsfältet om du vill visa egenskaper, redigera innehållet eller uppdatera cache (offlineinnehåll) för kanalen.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

#### Visa manifestet {#view-manifest}

Du kan visa manifestet från kanalkontrollpanelen.

>[!IMPORTANT]
>Det här alternativet är endast tillgängligt med AEM 6.4 Feature Pack 8 eller AEM 6.5 Feature Pack 4.

Följ de här stegen för att aktivera det här alternativet från kanalkontrollpanelen:

1. **Ange att kanalen ska vara offline**
   1. Markera kanalen och välj **Egenskaper** i åtgärdsfältet
   1. Navigera till fliken **Kanal** och se till att du avmarkerar alternativet **Utvecklarläge (framtvinga att kanalen är online)**
   1. Klicka på **Spara och stäng**
1. **Uppdatera offlineinnehåll**
   1. Markera kanalen och välj **Kontrollpanel** i åtgärdsfältet
   1. Navigera till panelen **KANALINFORMATION** och klicka på *..*
   1. Klicka **Uppdatera offlineinnehåll**

Du kan visa alternativet **Visa manifest** på panelen **KANALINFORMATION** på kontrollpanelen Kanal.

![image1](assets/channel-one.png)


### Online- och offlinekanaler {#online-and-offline-channels}

>[!NOTE]
>När du skapar en kanal är den som standard offline.

När du skapar en kanal kan den antingen definieras som en online- eller offlinekanal.

En ***onlinekanal*** visar det uppdaterade innehållet i realtidsmiljön medan en ***offlinekanal*** visar det cachelagrade innehållet.

Följ stegen nedan för att göra kanalen online:

1. Navigera till kanalen som **TestProject** —> **Kanaler** —> **TestChannel**.

   Markera kanalen.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Klicka på **Kontrollpanel** i åtgärdsfältet för att visa spelarens status. Panelen **KANALINFORMATION** innehåller information om huruvida kanalen är online eller offline.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Klicka på **Egenskaper** i åtgärdsfältet och navigera till fliken **Kanal** enligt nedan:

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Kontrollera **utvecklarläget** **(tvinga kanalen att vara online)** för att göra kanalen online.

   Klicka på **Spara och stäng** för att spara alternativet.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Gå tillbaka till kanalkontrollpanelen och nu visar panelen **KANALINFORMATION** spelarens onlinestatus.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>Om du vill konfigurera din kanal igen som offline avmarkerar du alternativet Utvecklarläge på fliken **Egenskaper** (som i steg 3) och klickar sedan på **KANALINFORMATION** på panelen **Uppdatera offlineinnehåll**, som i bilden nedan.

![kontrollpanel2](assets/dashboard2.gif)

#### Automatiska eller manuella uppdateringar från enhetskontrollpanelen {#automatic-versus-manual-updates-from-the-device-dashboard}

I följande tabell sammanfattas de händelser som är associerade med de automatiska och manuella uppdateringarna från kontrollpanelen för enheter.

<table>
 <tbody>
  <tr>
   <td><strong>Händelse</strong></td>
   <td><strong>Automatisk uppdatering av enhet</strong></td>
   <td><strong>Manuell uppdatering av enhet</strong></td>
  </tr>
  <tr>
   <td>Ändring i onlinekanal</td>
   <td>Innehåll uppdateras automatiskt</td>
   <td><p>Innehåll uppdaterat på "Enhet: Push Config"</p> <p>Eller</p> <p>Innehåll uppdaterat på <strong><i>enhet: Starta om</i></strong></p> </td>
  </tr>
  <tr>
   <td>Ändring i offlinekanal, men kanalen "push-innehåll" aktiveras INTE (inget offlinepaket återskapas)</td>
   <td>Ingen innehållsuppdatering</td>
   <td>Ingen innehållsuppdatering</td>
  </tr>
  <tr>
   <td>Ändringen i offlinekanalen och kanalen "push-innehåll" aktiveras (nytt offlinepaket)</td>
   <td>Innehåll uppdateras automatiskt</td>
   <td><p>Innehåll uppdaterat på <strong><i>enhet: Push-konfiguration</i></strong></p> <p>Eller</p> <p>Innehåll uppdaterat på <strong><i>enhet: Starta om</i></strong></p> </td>
  </tr>
  <tr>
   <td><p>Ändringar i konfiguration</p>
    <ul>
     <li>Visning (tvingad kanal)</li>
     <li>Enhet</li>
     <li>Kanaltilldelningar (ny kanal, borttagen kanal)</li>
     <li>Kanaltilldelning (roll, händelse, planering)</li>
    </ul> </td>
   <td>Konfigurationen uppdateras automatiskt</td>
   <td><p>Konfigurationen har uppdaterats på <strong><i>Enhet: Push-konfiguration</i></strong></p> <p>Eller</p> <p>Konfigurationen har uppdaterats på <strong><i>Enhet: Starta om</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Tilldelade bildskärmar {#assigned-displays}

Den tilldelade visningspanelen visar den visning som är associerad med kanalen. Den innehåller en ögonblicksbild av den tilldelade visningen tillsammans med upplösningen.

De associerade skärmarna visas på panelen **Tilldelade skärmar** enligt nedan:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>Mer information om hur du skapar en visning på en plats finns i:
>
>* [Skapa och hantera platser](managing-locations.md)
* [Skapa och hantera bildskärmar](managing-displays.md)



Klicka dessutom på visningen på panelen **TILLDELADE VISNINGAR** för att visa visningsinformationen enligt nedan:

![chlimage_1-28](assets/chlimage_1-28.png)

### Nästa steg {#the-next-steps}

Nästa steg när du har skapat en kanal och lagt till/redigerat innehåll i din kanal är att lära dig hur du skapar en plats och visar. Tilldela sedan en kanal till den visningen.

Se följande resurser för nästa steg:

* [Skapa och hantera kanaler](managing-channels.md)
* [Skapa och hantera platser](managing-locations.md)
* [Skapa och hantera bildskärmar](managing-displays.md)
