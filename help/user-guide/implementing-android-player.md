---
title: Implementera Android&trade; Player
description: Lär dig mer om implementeringen av Android&trade; Watchdog, en lösning som gör att du kan återställa Android&trade;-spelaren från krascher.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 0%

---

# Implementera Android™ Player {#implementing-android-player}

I det här avsnittet beskrivs hur du konfigurerar Android™-spelaren. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

Dessutom **Watchdog** är en lösning som återställer spelaren från krascher. Ett program måste registrera sig hos bevakningstjänsten och sedan regelbundet skicka meddelanden till tjänsten om att det är aktivt. Om bevakningstjänsten inte får ett meddelande om att enheten inte är vid liv inom en viss tid, försöker tjänsten starta om enheten för en ren återställning (om den har tillräcklig behörighet) eller starta om programmet.

## Installera Android™ Player {#installing-android-player}

Installera Android™ Player för AEM Screens för att implementera Android™ Player för AEM Screens.

Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) sida.

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Konfigurera en miljö för Android™-spelare om du använder AEM Screens 6.5.5 Service Pack.

Ange **Attributet SameSite för cookies för inloggningstoken** från **Lax** till **Ingen** från **Konfiguration av Adobe Experience Manager Web Console** på alla AEM författare och publiceringsinstanser.

Följ stegen nedan:

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** använda `http://localhost:4502/system/console/configMgr`.

1. Sök efter *Autentiseringshanterare för Adobe Granite-token*.

1. Ange **Attributet SameSite för cookies för inloggningstoken** från **Lax** till **Ingen**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Klicka **Spara**.


### Ad hoc-metod {#ad-hoc-method}

Med Ad-Hoc-metoden kan du installera den senaste Android™-spelaren (*.exe*). Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) sida.

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administratörspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM instansen som du vill ansluta till och klicka på **Spara**.

1. Navigera till **Enhet** **Registrering** på den vänstra åtgärdsmenyn så att du kan kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **Läge** är **REGISTRERAD** ser du att **Enhets-ID** fältet är ifyllt.
>
>Om **Läge** är **OREGISTRERAD** kan du använda **Token** för att registrera enheten.

## Implementera Android™-övervakning {#implementing-android-watchdog}

På grund av Android™-arkitekturen kräver omstart av enheten att programmet har systembehörighet. Det gör du genom att signera paketet med tillverkarens signeringsnycklar, annars startar övervakaren om spelarprogrammet och inte enheten startas om.

### Signage of Android™ `apks` använda Manufacturer Keys {#signage-of-android-apks-using-manufacturer-keys}

Få åtkomst till vissa privilegierade API:er i Android™, till exempel *PowerManager* eller *HDMIControlServices*, signera Android™ `apk` med tillverkarens nycklar.

>[!CAUTION]
>
>Krav:
>
>Android™ SDK bör vara installerat innan du utför följande steg.

Följ stegen nedan för att signera Android™-paketet med hjälp av tillverkarens tangenter:

1. Hämta appen från Google Play eller från [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/) page
1. Hämta plattformsknapparna från tillverkaren så att du kan få en *pk8* och *pem* fil

1. Leta reda på `apksigner` verktyg i Android™ sdk med hjälp av sök `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Hitta sökvägen till ZIP-justeringsverktyget i Android™ sdk
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Installera ***aemscreensaligned.apk*** med adb-installation på enheten

## Förstå övervakningstjänsterna för Android™ {#android-watchdog-services}

Tjänsten för övervakning mellan Android implementeras som ett Cordova-plugin-program med *AlarmManager*.

I följande diagram visas implementeringen av tjänsten watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initiering** - När Cordova-pluginprogrammet initieras kontrolleras behörigheterna för att se om du har systembehörighet och därmed behörighet att starta om. Om dessa två villkor är uppfyllda skapas en väntande metod för omstart, annars skapas en väntande metod för att starta om programmet (baserat på dess startaktivitet).

**2. Behåll livetid** - En håll kvar vid liv-timer används för att utlösa en händelse var 15:e sekund. I så fall avbryter du den befintliga väntande metoden (för att starta om eller starta om programmet) och registrerar en ny väntande metod för samma 60 sekunder i framtiden (i princip uppskjuten omstart).

>[!NOTE]
>
>I Android™ finns *AlarmManager* används för att registrera *pendingIntents* som kan köras även om appen har kraschat och larmleveransen är inexakt från API 19 (Kitkat). Behåll mellanrum mellan timerns intervall och *AlarmManagers* *pendingIntent&#39;s* larm.

**3. Programkrasch** - Om en krasch inträffar återställs inte längre pendingIntent för omstart som är registrerad med AlarmManager. Därför körs en omstart eller omstart av programmet (beroende på vilka behörigheter som är tillgängliga när Cordova-pluginprogrammet initieras).

## Massetablering av Android™ Player {#bulk-provision-android-player}

När du distribuerar Android™-spelaren i grupp behöver du etablera spelaren så att den pekar på en AEM och konfigurerar andra egenskaper utan att manuellt ange dem i administratörsgränssnittet.

>[!NOTE]
>Den här funktionen är tillgänglig från Android™ Player 42.0.372.

Följ stegen nedan för att tillåta massetablering i Android™-spelaren:

1. Skapa en JSON-konfigurationsfil med namnet `player-config.default.json`.
Se en [Exempel på JSON-princip](#example-json) och en tabell som beskriver hur de olika [Principattribut](#policy-attributes).

1. Använd en MDM- eller ADB- eller Android™ Studio-filutforskare för att släppa denna JSON-principfil i *sdcard* på Android™-enheten.

1. När filen distribueras använder du MDM-modulen för att installera spelarprogrammet.

1. När spelarprogrammet startas läses den här konfigurationsfilen in och pekar på den tillämpliga AEM där den är registrerad och sedan styrd.

   >[!NOTE]
   >Filen är *skrivskyddad* första gången som programmet startas och inte kan användas för efterföljande konfigurationer. Om spelaren startas innan konfigurationsfilen släpptes avinstallerar och installerar du om programmet på enheten.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:

| **Principnamn** | **Syfte** |
|---|---|
| *server* | URL till Adobe Experience Manager-servern. |
| *upplösning* | Enhetens upplösning. |
| *rebootSchedule* | Schemat för omstart gäller alla plattformar. |
| *enableAdminUI* | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Ange till *false* när den är helt konfigurerad och i produktion. |
| *enableOSD* | Aktivera kanalväljarens användargränssnitt för att användare ska kunna växla kanaler på enheten. Överväg att ställa in på *false* när den är helt konfigurerad och i produktion. |
| *enableActivityUI* | Aktivera om du vill visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| *enableNativeVideo* | Aktivera om du vill använda inbyggd maskinvaruacceleration för videouppspelning (endast Android™). |

### Exempel på JSON-princip {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>Alla Android™-enheter har en `*sdcard*` mapp om en faktisk `*sdcard*` infogas eller inte. Den här filen är på samma nivå som mappen Hämtningar när den distribueras. Vissa MDM-moduler, som Samsung Knox, kan se detta *sdcard* mappsökväg som *Intern lagring*.

## Massetablering av Android™ Player med Enterprise Mobility Management {#bulk-provisioning}

När du distribuerar Android™-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar starkt att du använder en EMM-lösning (Enterprise Mobility Management) som [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron eller Samsung Knox för att fjärraktivera och hantera driftsättningen. AEM Screens Android™-spelaren har stöd för den branschledande EMM AppConfig som tillåter fjärretablering.

## Namnge Android™ Player {#name-android}

Du kan tilldela Android™-spelaren ett användarvänligt enhetsnamn och på så sätt skicka det tilldelade enhetsnamnet till AEM (Adobe Experience Manager). Med den här funktionen kan du inte bara namnge Android™-spelaren utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Android™-spelaren:

1. Navigera till **inställningar** > **Om enhet**
1. Redigera och ange enhetsnamnet för Android™-spelaren

### Implementera massetablering av Android™ Player med Enterprise Mobility Management {#implementation}

Följ stegen nedan för att tillåta massetablering i Android™ Player:

1. Se till att din Android™-enhet har stöd för Google Play tjänster.
1. Registrera dina Android™-spelarenheter med din EMM-favoritlösning som stöder AppConfig.
1. Logga in på EMM-konsolen och hämta AEM Screens Player från Google Play.
1. Välj hanterad konfiguration eller relaterat alternativ.
1. Nu bör du se en lista med spelaralternativ som kan konfigureras, till exempel kod för server- och massregistrering.
1. Konfigurera de här parametrarna, spara och distribuera principen till enheterna.

   >[!NOTE]
   >Enheterna bör ta emot programmet tillsammans med konfigurationen och peka på rätt AEM med den valda konfigurationen. Om du väljer att konfigurera gruppregistreringskoden och behåller den som den konfigurerats i AEM, bör spelaren kunna registrera sig automatiskt. Om du har konfigurerat en standardskärm kan den även hämta och visa visst standardinnehåll (som senare kan ändras efter behov).

Du bör även höra med din EMM-leverantör om AppConfig-stöd. De populäraste som [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)och [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) bland annat stöder den här branschstandarden.

### Använda fjärrkontrollen till skärmar {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Fjärrkontroll för skärmar](implementing-remote-control.md)
