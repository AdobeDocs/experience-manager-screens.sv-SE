---
title: Implementera Android Player
seo-title: Implementering av Android Player
description: Följ den här sidan för att lära dig implementering av Android Watchdog, en lösning för att återställa spelaren från krascher.
seo-description: Följ den här sidan för att lära dig implementering av Android Watchdog, en lösning för att återställa spelaren från krascher.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administrera skärmar, Android Player
role: Administrator
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 0%

---


# Implementera Android Player {#implementing-android-player}

I det här avsnittet beskrivs hur Android-spelaren konfigureras. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

Dessutom är **Watchdog** en lösning för att återställa spelaren från krascher. Ett program måste registrera sig själv hos bevakningstjänsten och sedan regelbundet skicka meddelanden till tjänsten om att det är aktivt. Om bevakningstjänsten inte får ett meddelande om att enheten inte är vid liv inom en viss tid, försöker tjänsten starta om enheten för en ren återställning (om den har tillräcklig behörighet) eller starta om programmet.

## Installerar Android Player {#installing-android-player}

Installera Android Player för AEM Screens om du vill implementera Android Player för AEM Screens.

Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Du måste konfigurera en miljö för Android-spelaren om du använder AEM Screens 6.5.5 Service Pack.

Ange **SameSite-attributet för inloggningstokencookies** från **Lax** till **Ingen** från **Adobe Experience Manager Web Console Configuration** för alla AEM författare- och publiceringsinstanser.

Följ stegen nedan:

1. Navigera till **Adobe Experience Manager Web Console Configuration** med `http://localhost:4502/system/console/configMgr`.

1. Sök efter *Autentiseringshanterare för Adobe Granite-token*.

1. Ange **SameSite-attributet för inloggningstokencookies** från **Lax** till **Ingen**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Klicka på **Spara**.


### Ad-hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste Android-spelaren (*.exe*). Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/)-sidan.

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM instansen som du vill ansluta till och klicka på **Spara**.

1. Navigera till länken **Enhet** **Registrering** på den vänstra åtgärdsmenyn för att kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **State** är **REGISTRERAD** kommer du att märka att fältet **enhets-ID** fylls i.
>
>Om **State** är **UNREGISTERED** kan du använda **Token** för att registrera enheten.

## Implementera Android-övervakning {#implementing-android-watchdog}

På grund av Androids arkitektur måste programmet ha systembehörighet för att starta om enheten. För att göra detta måste du signera paketet med tillverkarens signeringsnycklar, annars startar övervakaren om spelarprogrammet och inte enheten startas om.

### Skylt för Android-appar med Manufacturer Keys {#signage-of-android-apks-using-manufacturer-keys}

Om du vill komma åt vissa privilegierade API:er för Android, till exempel *PowerManager* eller *HDMIControlServices*, måste du signera android-paketet med hjälp av tillverkarens nycklar.

>[!CAUTION]
>
>Krav:
>
>Android SDK bör vara installerat innan du utför följande steg.

Följ stegen nedan för att signera android-paketet med hjälp av tillverkarens tangenter:

1. Hämta appen från Google Play eller från [AEM Screens Player Downloads](https://download.macromedia.com/screens/)-sidan
1. Hämta plattformstangenterna från tillverkaren för att hämta en *pk8* och en *pem*-fil

1. Leta reda på verktyget apksigner i android sdk med hjälp av sök ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Hitta sökvägen till ZIP-justeringsverktyget i android sdk
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installera ***aemscreensaligned.apk*** med adb install på enheten

## Förstå övervakningstjänsterna för Android {#android-watchdog-services}

Övervakningstjänsten mellan Android-enheter implementeras som ett plugin-program för cordova med *AlarmManager*.

I följande diagram visas implementeringen av tjänsten watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initiering** Vid tidpunkten för initieringen av cordova-plugin-programmet kontrolleras behörigheter för att se om vi har systembehörighet och därmed behörighet att starta om. Om dessa två villkor är uppfyllda skapas en väntande metod för omstart, annars skapas en väntande metod för att starta om programmet (baserat på dess startaktivitet).

**2. Keep Alive Timer** En håll kvar vid liv-timer används för att utlösa en händelse var femtonde sekund. I så fall måste du avbryta den befintliga väntande metoden (för att starta om eller starta om programmet) och registrera en ny väntande metod för samma 60 sekunder i framtiden (vilket i själva verket innebär att omstarten skjuts upp).

>[!NOTE]
>
>I Android används *AlarmManager* för att registrera *pendingIntents* som kan köras även om appen har kraschat och dess alarmleverans är inexakt från API 19 (Kitkat). Behåll mellanrum mellan timerns intervall och *AlarmManagers* *pendingIntents*-larm.

**3. Programmet kraschar** Om en krasch inträffar återställs inte längre den pendingIntent för omstart som är registrerad med AlarmManager och en omstart eller omstart av programmet utförs (beroende på vilka behörigheter som är tillgängliga när cordova-pluginprogrammet initieras).

## Massetablering av Android Player {#bulk-provision-android-player}

När du distribuerar Android-spelaren i grupp behöver du etablera spelaren så att den pekar på en AEM och konfigurera andra egenskaper utan att ange dem manuellt i administratörsgränssnittet.

>[!NOTE]
>Den här funktionen är tillgänglig från Android Player 42.0.372.

Följ stegen nedan för att tillåta massetablering i Android-spelaren:

1. Skapa en konfigurations-JSON-fil med namnet `player-config.default.json`.
Se en [JSON-princip](#example-json) och en tabell som beskriver hur de olika [principattributen](#policy-attributes) används.

1. Använd en MDM- eller ADB- eller Android Studio-filutforskare för att släppa denna princip-JSON-fil i *sdcard*-mappen på Android-enheten.

1. När filen har distribuerats använder du MDM-modulen för att installera spelarprogrammet.

1. När spelarprogrammet startas läses den här konfigurationsfilen in och pekar på den tillämpliga AEM där det kan registreras och sedan kontrolleras.

   >[!NOTE]
   >Filen är *skrivskyddad* första gången programmet startas och kan inte användas för efterföljande konfigurationer. Om spelaren startas innan konfigurationsfilen släpptes avinstallerar och installerar du om programmet på enheten.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:

| **Principnamn** | **Syfte** |
|---|---|
| *server* | URL:en till Adobe Experience Manager-servern. |
| *upplösning* | Enhetens upplösning. |
| *rebootSchedule* | Schemat för omstart gäller alla plattformar. |
| *enableAdminUI* | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Ange *false* när den är helt konfigurerad och i produktion. |
| *enableOSD* | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Överväg att ställa in på *false* när den är helt konfigurerad och i produktion. |
| *enableActivityUI* | Aktivera om du vill visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| *enableNativeVideo* | Aktivera det här alternativet om du vill använda inbyggd maskinvaruacceleration för videouppspelning (endast Android). |

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
>Alla Android-enheter har en *sdcard*-mapp oavsett om ett riktigt *sdcard* är isatt eller inte. Den här filen är på samma nivå som mappen Hämtningar när den distribueras. Vissa MDM-moduler som Samsung Knox kan referera till denna *sdcard*-mapplats som *Intern lagring*.

## Massetablering av Android Player med Enterprise Mobility Management {#bulk-provisioning}

När du distribuerar Android-spelaren i grupp blir det omständligt att manuellt registrera alla spelare med AEM. Vi rekommenderar att du använder en EMM-lösning (Enterprise Mobility Management), som VMWare Airwatch, MobileIron eller Samsung Knox, för att fjärrdistribuera och hantera distributionen. AEM Screens Android-spelaren har stöd för den branschledande EMM AppConfig som tillåter fjärretablering.

## Namnge Android Player {#name-android}

Du kan tilldela Android-spelaren ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge Android-spelaren utan även enkelt tilldela rätt innehåll.

Följ stegen nedan för att konfigurera namnet i Android-spelaren:

1. Navigera till **inställningar** —> **Om enhet**
1. Redigera och ange namnet på din Android-spelare

### Implementera massetablering av Android Player med Enterprise Mobility Management {#implementation}

Följ stegen nedan för att tillåta massetablering i Android Player:

1. Kontrollera att din Android-enhet har stöd för Google Play-tjänster.
1. Registrera dina Android-enheter med din EMM-favoritlösning som stöder AppConfig.
1. Logga in på EMM-konsolen och hämta AEM Screens Player från Google Play.
1. Välj hanterad konfiguration eller relaterat alternativ.
1. Nu bör du se en lista med spelaralternativ som kan konfigureras, till exempel kod för server- och massregistrering.
1. Konfigurera de här parametrarna, spara och distribuera principen till enheterna.

   >[!NOTE]
   >Enheterna bör ta emot programmet tillsammans med konfigurationen och peka på rätt AEM med den valda konfigurationen. Om du väljer att konfigurera gruppregistreringskoden och behåller den som den konfigurerats i AEM, bör spelaren kunna registrera sig automatiskt. Om du har konfigurerat en standardskärm kan den även hämta och visa visst standardinnehåll (som senare kan ändras efter behov).

Dessutom bör du höra med din EMM-leverantör om AppConfig-stöd. De vanligaste är till exempel [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) och [Samsung Knox a11/> stöder bland annat denna branschstandard.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)
