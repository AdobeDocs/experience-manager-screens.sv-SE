---
title: Skapa och hantera kanaler
seo-title: Hantera kanaler
description: Följ den här sidan om du vill veta mer om hur du skapar och hanterar kanaler. Den förklarar även kanalkontrollpanelen och redigerar innehåll för en kanal.
seo-description: Följ den här sidan om du vill veta mer om hur du skapar och hanterar kanaler. Den förklarar även kanalkontrollpanelen och redigerar innehåll för en kanal.
uuid: cdf09ced-9089-4249-ba51-471d6fa0e507
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a8006686-8ee5-4971-ab79-0c7b01f108f2
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Skapa och hantera kanaler {#creating-and-managing-channels}

En kanal visar en sekvens med innehåll och visar bilder och videoklipp, men de kan också visa en webbplats eller ett ensidigt program.

På den här sidan visas hur du skapar och hanterar kanaler för skärmar.

**Krav**:

* [Konfigurera och distribuera skärmar](configuring-screens-introduction.md)
* [Skapa och hantera skärmsprojekt](creating-a-screens-project.md)

## Skapa en ny kanal {#creating-a-new-channel}

När du har skapat ett projekt för skärmar följer du stegen nedan för att skapa en ny kanal för ett skärmsprojekt:

1. Välj länken Adobe Experience Manager (överst till vänster) och sedan Skärmar. Du kan också gå direkt till: `https://localhost:4502/screens.html/content/screens`.
1. Navigera till Skärmprojekt och klicka på **Kanaler**.
1. Klicka på **Skapa** bredvid plusikonen i åtgärdsfältet. En guide öppnas (*mer information* finns i Kanaltyper).

1. Välj mallen i guiden och klicka på **Nästa**.
1. Ange egenskaperna för **Titel och Taggar**, **Fler titlar och beskrivningar**, **På/Av-tid** och **Vanity-URL**.

1. Klicka på **Skapa** så skapas kanalen och läggs till i kanalmappen.

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

I följande exempel visas hur du skapar en Sequence Channel (*ChannelOne*) för ett skärmsprojekt (*DemoProject*).

![demochannel](assets/demochannel.gif)

>[!NOTE]
>
>Du kan skapa olika zoner med hjälp av mallalternativen 1x2, 2x2 eller 2 till 3 delade skärmkanaler som nämns ovan.

***Viktigt***:

När du har skapat och lagt till innehåll i kanalen är nästa steg att skapa en plats följt av att skapa en skärm. Dessutom måste du tilldela den kanalen till en skärm. Läs mer i resurserna nedan i slutet av avsnittet.

## Arbeta med kanaler {#working-with-channels}

Du kan redigera, visa egenskaper och kontrollpanel, kopiera, förhandsgranska och ta bort en kanal.

>[!NOTE]
>
>Klicka på ikonen till vänster för att markera ett objekt. Klicka t.ex. på ikonen för kanal och utför följande åtgärder enligt bilden nedan.

![screen_shot_2019-07-24at103723am](assets/screen_shot_2019-07-24at103723am.png)

### Lägga till/redigera innehåll i en kanal {#adding-editing-content-to-a-channel}

Följ stegen nedan om du vill lägga till eller redigera innehåll i en kanal:

1. Klicka på den kanal som du vill redigera (se bilden ovan).
1. Klicka på **Redigera** i åtgärdsfältets övre vänstra hörn för att redigera kanalegenskaperna. Redigeraren öppnas och du kan lägga till resurser/komponenter i kanalen som du vill publicera.

>[!NOTE]
>
>Du kan lägga till komponenter i kanalen. Mer information finns i **[Lägga till komponenter i en kanal](adding-components-to-a-channel.md)**.

![demochannel1](assets/demochannel1.gif)

**Överföra videoklipp till kanalen** Följ stegen nedan för att överföra videoklipp till kanalen:

1. Markera kanalen där du vill överföra videon.
1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
1. Välj **Videofilmer** under Resurser och dra och släpp önskade videoklipp.

>[!NOTE]
>
>Om du får problem med att överföra videoklipp i din kanal kan du läsa [Felsöka videoklipp](troubleshoot-videos.md).

### Visningsegenskaper {#viewing-properties}

Följ stegen nedan om du vill visa eller redigera egenskaper för en kanal:

1. Klicka på den kanal som du vill redigera.
1. Klicka på **Egenskaper** i åtgärdsfältet för att visa/redigera kanalegenskaperna. På följande flikar kan du ändra alternativen.

![egenskaper](assets/properties.gif)

### Visa instrumentpanel {#viewing-dashboard}

Följ stegen nedan för att visa kontrollpanelen för en kanal:

1. Klicka på den kanal som du vill redigera.
1. Klicka på **Kontrollpanel** i åtgärdsfältet för att visa kontrollpanelen. Panelen **KANALINFORMATION**,**TILLDELADE VISAR** OCH **VÄNTANDE STARTOR** öppnas enligt bilden nedan:

![kontrollpanel](assets/dashboard.gif)

### Kanalinformation {#channel-information}

Panelen Kanalinformation beskriver kanalegenskaperna tillsammans med förhandsvisningen av kanalen. Dessutom innehåller det information om huruvida kanalen är offline eller online.

Klicka på (**...**) i åtgärdsfältet **Kanalinformation** för att visa egenskaper, redigera innehållet eller för att uppdatera cache-minnet (offlineinnehåll) för kanalen.

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

### Online- och offlinekanaler {#online-and-offline-channels}

>[!NOTE]
>
>Som standard är kanalen offline när du skapar en kanal.

När du skapar en kanal kan den antingen definieras som en online- eller offlinekanal.

En ***onlinekanal*** visar det uppdaterade innehållet i realtidsmiljön, medan en ***offlinekanal*** visar det cachelagrade innehållet.

Följ stegen nedan för att göra kanalen online:

1. Navigera till kanalen som **TestProject** —> **Channels** —> **TestChannel**.

   Markera kanalen.

   ![screen_shot_2019-08-01at31406pm](assets/screen_shot_2019-08-01at31406pm.png)

   Klicka på **Kontrollpanel** i åtgärdsfältet för att visa spelarens status. **CHANNEL INFORMATION **panel ger information om huruvida kanalen är online eller offline.

   ![screen_shot_2019-08-01at31458pm](assets/screen_shot_2019-08-01at31458pm.png)

1. Klicka på **Egenskaper** i åtgärdsfältet och navigera till fliken **Kanal** enligt nedan:

   ![screen_shot_2019-08-01at31542pm](assets/screen_shot_2019-08-01at31542pm.png)

1. Markera **Developer** **Mode (tvinga kanaler att vara online)** för att göra kanalen online.

   Klicka på **Spara och stäng** för att spara alternativet.

   ![screen_shot_2019-08-01at31658pm](assets/screen_shot_2019-08-01at31658pm.png)

   Gå tillbaka till kanalkontrollpanelen och nu visar panelen **KANALINFORMATION** spelarens onlinestatus.

   ![screen_shot_2019-08-01at31821pm](assets/screen_shot_2019-08-01at31821pm.png)

>[!NOTE]
>
>Om du vill konfigurera din kanal igen som offline avmarkerar du alternativet för utvecklarläge på fliken **Egenskaper** (vilket visas i steg 3) och klickar sedan på **Uppdatera offlineinnehåll** på panelen **KANALINFORMATION**, vilket visas i bilden nedan.

![dashboard2](assets/dashboard2.gif)

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
   <td><p>Konfigurationen har uppdaterats på <strong><i>enheten: Push-konfiguration</i></strong></p> <p>Eller</p> <p>Konfigurationen har uppdaterats på <strong><i>enheten: Starta om</i></strong></p> </td>
  </tr>
 </tbody>
</table>

### Tilldelade bildskärmar {#assigned-displays}

Den tilldelade visningspanelen visar den visning som är associerad med kanalen. Den innehåller en ögonblicksbild av den tilldelade visningen tillsammans med upplösningen.

De associerade skärmarna visas på panelen **Tilldelade skärmar** enligt nedan:

![chlimage_1-27](assets/chlimage_1-27.png)

>[!NOTE]
>
>Mer information om hur du skapar en visning på en plats finns i:
>
>* [Skapa och hantera platser](managing-locations.md)
>* [Skapa och hantera bildskärmar](managing-displays.md)
>



Klicka dessutom på visningen på panelen **TILLDELADE** VISNINGAR för att visa visningsinformationen enligt nedan:

![chlimage_1-28](assets/chlimage_1-28.png)

### Nästa steg {#the-next-steps}

Nästa steg när du har skapat en kanal och lagt till/redigerat innehåll i din kanal är att lära dig hur du skapar en plats och visar. Tilldela sedan en kanal till den visningen.

Se följande resurser för nästa steg:

* [Skapa och hantera kanaler](managing-channels.md)
* [Skapa och hantera platser](managing-locations.md)
* [Skapa och hantera bildskärmar](managing-displays.md)

