---
title: Implementera Android&handel; Player
description: Lär dig mer om implementeringen av Android&trade; Watchdog, en lösning där du kan återställa Android&trade; player från krascher.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 0%

---

# Implementera Android™ Player {#implementing-android-player}

>[!CAUTION]
>Den Android-baserade AEM Screens Player är officiellt föråldrad. Användare rekommenderas att migrera till ett annat operativsystem som stöds av AEM Screens.

I det här avsnittet beskrivs hur du konfigurerar Android™ Player. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

Dessutom är **Watchdog** en lösning för att återställa spelaren från krascher. Ett program måste registrera sig hos bevakningstjänsten och sedan regelbundet skicka meddelanden till tjänsten om att det är aktivt. Om bevakningstjänsten inte får ett meddelande om att enheten inte hålls vid liv inom en viss tid, försöker tjänsten starta om enheten. Det gör det för en ren återställning (om den har tillräcklig behörighet) eller startar om programmet.

## Installera Android™ Player {#installing-android-player}

Installera Android™ Player för AEM Screens för att implementera Android™ Player för AEM Screens.

Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Konfigurera en miljö för Android™ Player om du använder AEM Screens 6.5.5 Service Pack.

Ange attributet **SameSite för inloggningstokencookies** från **Lax** till **None** från **Adobe Experience Manager Web Console Configuration** på alla AEM-författare och publiceringsinstanser.

Följ stegen nedan:

1. Navigera till **Adobe Experience Manager Web Console Configuration** med `http://localhost:4502/system/console/configMgr`.

1. Sök efter *Autentiseringshanterare för Adobe Granite-token*.

1. Ange attributet **SameSite för inloggningstokencookies** från **Lax** till **None**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Klicka på **Spara**.


### Ad hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste Android™ Player (*.exe*). Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administratörspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM-instans som du vill ansluta till och klicka på **Spara**.

1. Navigera till länken **Enhet** **Registrering** från den vänstra åtgärdsmenyn så att du kan kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **Läge** är **REGISTERED** kan du se att fältet **Enhets-ID** är ifyllt.
>
>Om **State** är **UNREGISTERED** kan du använda **Token** för att registrera enheten.

## Implementera Android™ Watchdog {#implementing-android-watchdog}

På grund av Android™-arkitekturen kräver omstart av enheten att programmet har systembehörighet. Signera appen med tillverkarens signeringsnycklar, annars kan övervakaren starta om spelarprogrammet och inte starta om enheten.

### Signage för Android™ `apks` med Manufacturer Keys {#signage-of-android-apks-using-manufacturer-keys}

Om du vill få tillgång till vissa privilegierade API:er för Android™, till exempel *PowerManager* eller *HDMIControlServices*, signerar du Android™ `apk` med hjälp av tillverkarens nycklar.

>[!CAUTION]
>
>Krav:
>
>Du bör ha Android™ SDK installerat innan du utför följande steg.

Följ stegen nedan för att signera Android™-paketet med hjälp av tillverkarens tangenter:

1. Hämta appen från Google Play eller från sidan [AEM Screens Player Downloads](https://download.macromedia.com/screens/)
1. Hämta plattformstangenterna från tillverkaren så att du kan hämta en *pk8* - och en *pem* -fil

1. Leta reda på verktyget `apksigner` i Android™ SDK med hjälp av sök `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Hitta sökvägen till ZIP-justeringsverktyget i Android™ SDK
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. Installera ***aemscreensaligned.apk*** med adb install på enheten

## Förstå Android™ Watchdog Services {#android-watchdog-services}

Övervakningstjänsten mellan Android™ implementeras som ett Cordova-plugin-program med *AlarmManager*.

I följande diagram visas implementeringen av tjänsten watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initiering** - Vid initieringen av Cordova-plugin-programmet kontrolleras behörigheter för att se om du har systembehörighet och därmed behörighet att starta om. Om dessa två villkor är uppfyllda skapas en väntande metod för omstart, annars skapas en väntande metod för att starta om programmet (baserat på dess startaktivitet).

**2. Keep Alive Timer** - en håll kvar vid liv-timer används för att utlösa en händelse var femtonde sekund. Om så är fallet avbryter du den befintliga väntande metoden (för att starta om eller starta om programmet) och registrerar en ny väntande metod för samma 60 sekunder i framtiden (vilket i själva verket innebär att omstarten skjuts upp).

>[!NOTE]
>
>I Android™ används *AlarmManager* för att registrera *pendingIntents* som kan köras även om appen har kraschat och dess alarmleverans är inexakt från API 19 (Kitkat). Behåll mellanrum mellan timerns intervall och larmet *AlarmManager* *pendingIntents*.

**3. Programkrasch** - Om en krasch inträffar återställs inte längre pendingIntent for Reboot som är registrerad med AlarmManager. Därför körs en omstart eller omstart av programmet (beroende på vilka behörigheter som är tillgängliga när Cordova-pluginprogrammet initieras).

## Massetablering av Android™ Player {#bulk-provision-android-player}

När du distribuerar Android™-spelaren i grupp måste du etablera spelaren så att den pekar på en AEM-instans och konfigurerar andra egenskaper utan att ange dem manuellt i administratörsgränssnittet.

>[!NOTE]
>Den här funktionen är tillgänglig från Android™ Player 42.0.372.

Följ stegen nedan för att tillåta massetablering i Android™-spelaren:

1. Skapa en JSON-konfigurationsfil med namnet `player-config.default.json`.
Se en [Exempel på JSON-princip](#example-json) och en tabell som beskriver användningen av de olika [principattributen](#policy-attributes).

1. Använd en MDM- eller ADB- eller Android™ Studio-filutforskare för att släppa denna JSON-principfil i mappen *sdcard* på Android™-enheten.

1. När filen distribueras använder du MDM-modulen för att installera spelarprogrammet.

1. När spelarprogrammet startas läses den här konfigurationsfilen in och pekar på den AEM-server där den är registrerad och sedan styrs.

   >[!NOTE]
   >Den här filen är *skrivskyddad* första gången som programmet startas och kan inte användas för efterföljande konfigurationer. Om spelaren startas innan konfigurationsfilen släpps avinstallerar och installerar du om programmet på enheten.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:

| **Principnamn** | **Syfte** |
|---|---|
| *server* | URL till Adobe Experience Manager-servern. |
| *upplösning* | Enhetens upplösning. |
| *rebootSchedule* | Schemat för omstart gäller alla plattformar. |
| *enableAdminUI* | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Ange *false* när den är helt konfigurerad och i produktion. |
| *enableOSD* | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Du bör ange det till *false* när det är fullständigt konfigurerat och i produktion. |
| *enableActivityUI* | Aktivera om du vill visa förloppet för aktiviteter, som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
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
>Alla Android™-enheter har en `*sdcard*`-mapp oavsett om en faktisk `*sdcard*` infogas eller inte. Den här filen är på samma nivå som mappen Hämtningar när den distribueras. Vissa MDM-moduler, som Samsung Knox, kan se den här *sdcard*-mapplatsen som *Intern lagring*.

## Massetablering av Android™ Player med Enterprise Mobility Management {#bulk-provisioning}

När du distribuerar Android™-spelaren i grupp blir det jobbigt att registrera alla spelare manuellt i AEM. Använd en EMM-lösning (Enterprise Mobility Management) som [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), MobileIron eller Samsung Knox så att du kan fjärraktivera och hantera din distribution. AEM Screens Android™-spelaren stöder den branschledande EMM AppConfig för fjärrprovisionering.

## Namnge Android™ Player {#name-android}

Du kan tilldela Android™-spelaren ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till AEM (Adobe Experience Manager). Med den här funktionen kan du inte bara namnge Android™-spelaren utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Android™-spelaren:

1. Navigera till **inställningar** > **Om enhet**
1. Redigera och ange enhetsnamnet för din Android™-spelare

### Implementera massetablering av Android™ Player med Enterprise Mobility Management {#implementation}

Följ stegen nedan för att tillåta massetablering i Android™ Player:

1. Se till att din Android™-enhet stöder Google Play tjänster.
1. Registrera dina Android™-spelarenheter med din EMM-lösning som stöder AppConfig.
1. Logga in på EMM-konsolen och hämta AEM Screens Player från Google Play.
1. Klicka på den hanterade konfigurationen eller det relaterade alternativet.
1. Nu bör du se en lista med spelaralternativ som kan konfigureras, till exempel kod för server- och massregistrering.
1. Konfigurera de här parametrarna, spara och distribuera principen till enheterna.

   >[!NOTE]
   >Enheterna bör ta emot programmet tillsammans med konfigurationen. Den bör peka på rätt AEM-server med den valda konfigurationen. Om du väljer att konfigurera gruppregistreringskoden och behåller den som den konfigurerats i AEM, bör spelaren kunna registrera sig automatiskt. Om du har konfigurerat en standardskärm kan den även hämta och visa visst standardinnehåll (som senare kan ändras efter behov).

Du bör även höra med din EMM-leverantör om AppConfig-stöd. De flesta populära, till exempel [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) och [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm), stöder den här branschstandarden.

### Använda Screens fjärrkontroll {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Screens fjärrkontroll](implementing-remote-control.md)
