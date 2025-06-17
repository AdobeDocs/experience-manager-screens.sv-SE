---
title: Arbeta med AEM Screens Player
description: Lär dig hur du arbetar med AEM Screens Player, administratörsgränssnittet och kanalväljaren.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 1%

---

# Arbeta med AEM Screens Player

Du kan hantera kanalinnehållet och andra inställningar i AEM Screens Player.

>[!NOTE]
>
>Tryck på ***Ctrl+Cmd+F*** så att du kan avsluta helskärmsläget för OS X AEM Screens Player.

När du har tilldelat en kanal till en skärm visas innehållet i AEM Screens Player. Du kan antingen konfigurera inställningar för spelaren med hjälp av inställningarna för administratörsgränssnittet (från kontrollpanelen) eller från spelaren.

## Använda enhetskontrollpanelen {#using-the-device-dashboard}

Du kan konfigurera inställningar för enheten från enhetskontrollpanelen som du kommer åt via AEM-redigeringsinstansen.

1. Navigera till enhetens kontrollpanel från ditt projekt, till exempel ***Testa projekt*** > ***Enheter***.

   Klicka på **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Klicka på enheten så att du kan öppna enhetens kontrollpanel.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Kontrollera panelen **INSTÄLLNINGAR**. Du kan aktivera eller inaktivera **administratörsgränssnittet** och **kanalväljaren** för spelaren bland dessa två alternativ.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Användargränssnittet för administratörer {#the-admin-ui}

Om du aktiverar **administratörsgränssnittet** från inställningspanelen kan användaren öppna administratörsinställningarna från Screens Player. Om du inaktiverar det här alternativet från enhetens kontrollpanel kan användaren inte öppna administratörsgränssnittet från spelaren.

Om du vill visa administratörsgränssnittet från Screens Player trycker du länge på det övre vänstra hörnet för att öppna Admin-menyn, på den beröringsaktiverade AEM Screens Player eller med en mus. Informationen visas när registreringen är klar och kanalerna har lästs in.

>[!NOTE]
>
>Du kan även visa AEM Screens Player-appens drifttid för att kontrollera programmets hälsostatus.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Åtkomst till alternativen på menyn Konfiguration {#configuration-options}

Du kan uppdatera dina konfigurationer om du klickar på alternativet **Konfiguration** på sidomenyn, vilket visas i figuren nedan:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

På menyn Konfiguration kan du ändra följande inställningar:

* Återställ **firmware**, **Inställningar** eller **Till fabrik** i den här dialogrutan.

* Ange det maximala antalet loggfiler som du vill behålla för en AEM Screens Player i **Max antal. av loggfiler att behålla**.

* Aktivera eller inaktivera **Admin Menu**, **Channel Switcher** och **Activity UI** för Screens Player.

  Om **aktivitetsgränssnittet** är aktiverat på menyn **Konfiguration** visar AEM Screens Player *aktivitetsmeddelandena* i det övre högra hörnet av spelaren, vilket visas i figuren nedan.

  ![bild](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>Alternativet **Uppdatera inbyggd programvara** fungerar bara på Cordova, till exempel Android™-spelare.

>[!NOTE]
>
>Vi rekommenderar att **administratörsgränssnittet** inaktiveras i produktionsdistributioner.

#### Åtkomst till menyalternativ för innehållscache {#content-cache-options}

Du kan rensa cache för kanaler och program från administratörsgränssnittet i AEM Screens Player.

Klicka på **innehållscachen** i sidlisten så att du kan uppdatera cachen.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Kanalväxlaren {#the-channel-switcher}

Om du aktiverar **kanalväljaren** på panelen Inställningar kan användaren öppna kanalvalsinställningarna från Screens Player.

Om du inaktiverar det här alternativet från enhetspanelen kan användaren inte styra kanalinställningarna från Screens Player.

Du kan växla och styra inställningarna för kanalen från Screens Player.

Om du vill visa kanalväljaren från spelaren trycker du länge på det nedre vänstra hörnet för att öppna kanalväljaren som tillåter att kanaler och andra funktioner växlas.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Du kan också aktivera eller inaktivera admin-menyn och kanalväljaren för spelaren från Screens Player.
>
>(Se *Ändra inställningar från Screens Player* enligt avsnittet nedan.)

### Hantera inställningar från AEM Screens Player

Du kan också ändra inställningarna för administratörsgränssnittet och kanalväljaren från själva spelaren.

Så här ändrar du inställningar från spelaren:

1. Tryck länge på det övre vänstra hörnet i den inaktiva kanalen för att öppna administratörspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn.
1. Aktivera eller inaktivera konfigurationen för **administratörsgränssnittet** eller **kanalväxlaren**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Felsöka AEM Screens Player

Du kan felsöka olika problem som rör AEM Screens Player (maskinvara och programvara):

| **Problem** | **Rekommendationer** |
|---|---|
| Spelarlagringen är full | Eliminera onödiga filer |
| Spelaren förlorade nätverket | Använd Cat-5- eller Cat-6-kabel. För wifi ska du minska avståndet från routern till spelarenheten |
| AEM Screens Player kraschade | Vi rekommenderar att du har en app som kontrollerar att AEM Screens Player alltid körs |
| Inställningar för förlorad AEM Screens Player | Kontrollera anslutningen till AEM-servern |
| AEM Screens Player startar inte automatiskt när spelaren har startats om eller startats om | Kontrollera operativsystemets startmapp eller initieringsprocedur |
| AEM Screens Player visar fel eller gammalt innehåll | Kontrollera nätverksanslutning |

### Uppdateringar för AEM Screens Player

Det finns två typer av uppdateringar för AEM Screens Player:

| **Metod** | **Information** | **via fjärr** | **Automatiserad** | **0 driftstopp** |
|---|---|---|---|---|
| Uppdatering av inbyggd programvara | Används på befintliga installerade spelare med hjälp av fjärrkommando. Efter uppdateringen läses spelaren in automatiskt igen med det befintliga innehållet. | Ja | Egen | Nästan - 1-3 sekunder |
| Uppdateringar för spelargränssnitt | En ny körbar fil som distribueras på spelaren. Den här funktionen kräver att du fjärrkopierar den nya binärfilen på spelaren och stoppar den pågående körningen och startar den nya versionen. Det kan kräva att du hämtar förinläsningen av paketen igen. | Ja (via fjärrgränssnitt) | Egen | Nej |

## Riktlinjer för val av maskinvara för spelarenhet {#hardware-selection-guidelines-for-player-device}

Följande avsnitt innehåller riktlinjer för val av maskinvara för ett Screens-projekt:

* Källa alltid komponenter av typen ***Commercial*** eller ***Industrial*** för både PC Player och Display Panel eller Projector.

* Samarbeta alltid med leverantörer som levererar digitala signaturer.
* Ta alltid hänsyn till miljöfaktorer, som omgivningstemperatur och relativ luftfuktighet.
* Granska alltid effektkrav och energikonditionering.
* Granska noggrant prestandabehoven och I/O-portarna som krävs för programmet.

I följande tabell sammanfattas maskinvarukonfigurationerna med typiska användningsfall för ett AEM Screens-projekt:

<table>
 <tbody>
  <tr>
   <td>Spelarkonfiguration</td>
   <td>Processor</td>
   <td>Minne</td>
   <td>Lagring SSD</td>
   <td>GPU</td>
   <td>Visa</td>
   <td>I/O</td>
   <td>Vanliga användningsfall</td>
  </tr>
  <tr>
   <td>Grundläggande</td>
   <td>Intel® Atom-processor med dubbla kärnor, i3 eller fyra kärnor på ingångsnivå</td>
   <td><p>4 GB minne</p> <p>2 MB cache</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet/trådlös<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Standardloop i helskärmsläge<br /> </li>
     <li>Dag-parsning</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Intel® Core™ i5-processor med fyra kärnor</td>
   <td><p>8 GB minne</p> <p>4 MB cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst, <br /> 2x USB</td>
   <td>
    <ul>
     <li>Ett dynamiskt Source-innehåll</li>
     <li>Enkel interaktiv</li>
     <li>1-3 zonlayouter</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avancerat</td>
   <td>Intel® Core™ i7-processor med fyra kärnor och hypertrådning</td>
   <td><p>16 GB minne</p> <p>8 MB cache</p> </td>
   <td>256 GB</td>
   <td>Dedikerad grafikprocessor</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst, <br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 eller fler innehållszoner, samtidiga videouppspelningar</li>
     <li>Flersidig interaktiv</li>
     <li>Utlösare för flera Source-data</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
