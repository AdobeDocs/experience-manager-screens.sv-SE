---
title: Arbeta med AEM Screens Player
seo-title: Arbeta med skärmuppspelaren
description: Följ den här sidan om du vill veta mer om Screens Player. Det förklarar även administratörsgränssnittet och kanalväljaren.
seo-description: Följ den här sidan om du vill veta mer om Screens Player. Det förklarar även administratörsgränssnittet och kanalväljaren.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administrera skärmar
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 1%

---


# Arbeta med AEM Screens Player {#working-with-aem-screens-player}

Du kan hantera kanalinnehållet och andra inställningar i AEM Screens Player.

>[!NOTE]
>
>Tryck på ***Ctrl+Cmd+F*** för att avsluta helskärmsläget för OS X AEM Screens Player.

När du har tilldelat en kanal till en skärm visas innehållet i AEM Screens Player. Du kan antingen konfigurera inställningar för spelaren med hjälp av inställningarna för administratörsgränssnittet (från kontrollpanelen) eller från spelaren.

## Använda enhetskontrollpanelen {#using-the-device-dashboard}

Du kan konfigurera inställningar för enheten från enhetskontrollpanelen, som du kommer åt via AEM.

1. Navigera till enhetskonsolen från ditt projekt, till exempel ***Testa projekt*** —> ***Enheter***.

   Välj **Enheter** och **Enhetshanteraren** i åtgärdsfältet.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Klicka på enheten för att öppna enhetens kontrollpanel.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Kontrollera panelen **INSTÄLLNINGAR**. Du kan aktivera/inaktivera **Admin-gränssnittet** och **kanalväljaren** för spelaren bland dessa två alternativ.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### Administratörsgränssnittet {#the-admin-ui}

Om du aktiverar **administratörsgränssnittet** från inställningspanelen kan användaren öppna administratörsinställningarna från skärmspelaren. Om du inaktiverar det här alternativet från enhetspanelen kan användaren inte öppna administratörsgränssnittet från spelaren.

Om du vill visa administratörsgränssnittet från Skärmspelaren trycker du länge på det övre vänstra hörnet för att öppna Admin-menyn, på den pekaktiverade AEM Screens-spelaren eller med en mus. Den visar information när registreringen är klar och kanalerna har lästs in.

>[!NOTE]
>
>Dessutom kan du visa AEM Screens Player-appens drifttid för att kontrollera programmets hälsostatus.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Åtkomst till alternativen på konfigurationsmenyn {#configuration-options}

Du kan uppdatera dina konfigurationer om du väljer alternativet **Konfiguration** på sidomenyn, vilket visas i bilden nedan:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

På menyn Konfiguration kan du ändra följande inställningar:

* Återställ **Firmware**, **Inställningar** eller **Till fabrik** från den här dialogrutan.

* Ange det maximala antalet loggfiler som ska behållas för en AEM Screens-spelare i **Max antal. av loggfiler som ska sparas**.

* Aktivera eller inaktivera **Admin Menu**, **Channel Switcher** och **Activity UI** för skärmspelaren.

   Om **Aktivitetsgränssnittet** är aktiverat på menyn **Konfiguration**, visar AEM Screens-spelaren *aktivitetsmeddelanden* i det övre högra hörnet av spelaren, vilket visas i figuren nedan.

   ![bild](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>Alternativet **Uppdatera inbyggd programvara** fungerar bara på cordova, till exempel Android-spelare.

>[!NOTE]
>
>Vi rekommenderar att användargränssnittet **för administratörer** inaktiveras i produktionsdistributioner.

#### Åtkomst till menyalternativen för innehållscache {#content-cache-options}

Du kan rensa cache för kanaler och program från administratörsgränssnittet i AEM Screens Player.

Välj **innehållscachen** från sidospåret för att uppdatera cacheminnet.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### Kanalväxlaren {#the-channel-switcher}

Om du aktiverar **kanalväljaren** från panelen Inställningar kan användaren öppna kanalvalet/inställningarna från skärmspelaren.

Om du inaktiverar det här alternativet från enhetspanelen kan användaren inte styra kanalinställningarna från Skärmspelaren.

Du kan växla och styra inställningarna för kanalen från skärmspelaren.

Om du vill visa kanalväljaren från spelaren trycker du länge på det nedre vänstra hörnet för att öppna kanalväljaren som tillåter växling av kanaler och andra funktioner.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Du kan också aktivera eller inaktivera admin-menyn och kanalväljaren för spelaren från skärmspelaren.
>
>(Se *Ändra inställningar från Skärmspelaren* enligt avsnittet nedan.)

### Hantera inställningar från AEM Screens Player {#managing-preferences-from-the-aem-screens-player}

Du kan också ändra inställningarna för administratörsgränssnittet och kanalväljaren från själva spelaren.

Följ de här stegen för att ändra inställningarna för spelaren:

1. Tryck länge på det övre vänstra hörnet i den inaktiva kanalen för att öppna administrationspanelen.
1. Navigera till **Konfiguration** från den vänstra åtgärdsmenyn.
1. Aktivera/inaktivera konfiguration för **Admin-användargränssnitt** eller **kanalväxlare**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Felsökning av AEM Screens Player {#troubleshooting-aem-screens-player}

Du kan felsöka olika problem som rör AEM Screens Player (maskinvara och programvara):

| **Problem** | **Recommendations** |
|---|---|
| Spelarlagringen är full | Eliminera onödiga filer |
| Spelaren förlorade nätverket | Använd katt-5/katt-6-kabel. För wifi ska du minska avståndet från routern till spelarenheten |
| AEM Screens Player kraschade | Vi rekommenderar att du har en övervakningsapp som ser till att AEM Screens Player alltid körs |
| Inställningar för förlorad AEM Screens Player | Kontrollera anslutning till AEM server |
| AEM Screens Player startar inte automatiskt efter omstart/omstart av spelaren | Kontrollera operativsystemets startmapp eller initieringsprocedur |
| AEM Screens Player visar fel/gammalt innehåll | Kontrollera nätverksanslutning |

### Uppdateringar för AEM Screens Player {#updates-for-aem-screens-player}

Det finns två typer av uppdateringar för AEM Screens Player:

| **Metod** | **Information** | **via fjärranslutning** | **Automatiserad** | **0 Driftavbrott** |
|---|---|---|---|---|
| Uppdatering av inbyggd programvara | Används på befintliga installerade spelare via fjärrkommando. Efter uppdateringen läses Player in automatiskt igen med det befintliga innehållet. | Ja | Anpassat | Nästan - 1-3 sekunder |
| Uppdateringar för spelargränssnitt | Det här är en ny körbar fil som ska distribueras på spelaren. Detta kräver att du fjärrkopierar en ny binär fil i spelaren och stoppar den pågående körningen och startar den nya versionen. Detta kan kräva att du hämtar förinläsningen av paketen igen. | Ja (via fjärrgränssnitt) | Anpassat | Nej |

## Riktlinjer för val av maskinvara för spelarenhet {#hardware-selection-guidelines-for-player-device}

Följande avsnitt innehåller riktlinjer för val av maskinvara för ett skärmsprojekt:

* Källa alltid ***Commercial*** eller ***Industrial*** Grade-komponenter för både PC Player och Display Panel eller Projector.

* Samarbeta alltid med leverantörer som levererar digitala signaturer.
* Ta alltid hänsyn till miljöfaktorer som omgivningstemperatur och relativ luftfuktighet.
* Granska alltid effektkrav och energikonditionering.
* Granska noggrant prestandabehov och I/O-portar som krävs för programmet.

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
   <td>Vanliga användningsområden</td>
  </tr>
  <tr>
   <td>Grundläggande</td>
   <td>Intel® Atom-processor med dubbla kärnor, i3 eller fyra kärnor på ingångsnivå</td>
   <td><p>4 GB minne</p> <p>2 MB cache</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI,<br /> Ethernet/trådlöst,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Standardrepetition i helskärmsläge<br /> </li>
     <li>Dag-parsning</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Processor med fyra kärnor, Intel® Core i5</td>
   <td><p>8 GB minne</p> <p>4 MB cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Dynamiskt innehåll med en källa</li>
     <li>Enkel interaktiv</li>
     <li>1-3 zonlayouter</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avancerat</td>
   <td>Intel® Core i7-processor med fyra kärnor och hypertrådning</td>
   <td><p>16 GB minne</p> <p>8 MB cache</p> </td>
   <td>256 GB</td>
   <td>Dedikerad grafikprocessor</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst,<br /> 4x USB</td>
   <td>
    <ul>
     <li>4 eller fler innehållszoner, samtidiga videouppspelningar</li>
     <li>Interaktiv flersidig</li>
     <li>Datautlösare med flera källor</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
