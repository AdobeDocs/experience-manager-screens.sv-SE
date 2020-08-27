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
translation-type: tm+mt
source-git-commit: 319a80a7fe3d68cbc16108eb302def390b445838
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---


# Implementera Android Player {#implementing-android-player}

I det här avsnittet beskrivs hur Android-spelaren konfigureras. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

Dessutom är **Watchdog** en lösning för att återställa spelaren från krascher. Ett program måste registrera sig själv hos bevakningstjänsten och sedan regelbundet skicka meddelanden till tjänsten om att det är aktivt. Om bevakningstjänsten inte får ett meddelande om att enheten inte är vid liv inom en viss tid, försöker tjänsten starta om enheten för en ren återställning (om den har tillräcklig behörighet) eller starta om programmet.

## Installera Android Player {#installing-android-player}

Installera Android Player för AEM Screens om du vill implementera Android Player för AEM Screens.

Gå till [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) .

### Setting up Environment for AEM Screens 6.5.5 Feature Pack and later {#fp-environment-setup}

Du måste konfigurera en miljö för Android-spelaren om du använder AEM Screens 6.5.5 Feature Pack.

Följ stegen nedan:

1. Navigera till **Adobe Experience Manager Web ConsoleConfiguration** med `http://localhost:4502/system/console/configMgr`.

1. Sök efter autentiseringshanterare för *Adobe Granite-token*.

1. Ange attributet **SameSite för inloggningstokencookies** från **Lax** till **None**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Click **Save**.


### Ad hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste Android Player (*.exe*). Gå till [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) .

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM instansen som du vill ansluta till och klicka på **Spara**.

1. Navigera till länken **Device** **Registration** (Enhetsregistrering) på den vänstra åtgärdsmenyn för att kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **läget** är **REGISTRERAT** kommer du att se att fältet **Enhets-ID** fylls i.
>
>Om **tillståndet** är **OREGISTRERAT** kan du använda **Token** för att registrera enheten.

## Implementera Android-övervakning {#implementing-android-watchdog}

På grund av Androids arkitektur måste programmet ha systembehörighet för att starta om enheten. För att göra detta måste du signera paketet med tillverkarens signeringsnycklar, annars startar övervakaren om spelarprogrammet och inte enheten startas om.

### Skylt för Android-appar med Manufacturer Keys {#signage-of-android-apks-using-manufacturer-keys}

Om du vill få tillgång till vissa privilegierade API:er för Android, som *PowerManager* eller *HDMIControlServices*, måste du signera android-paketet med hjälp av tillverkarens nycklar.

>[!CAUTION]
>
>Krav:
>
>Android SDK bör vara installerat innan du utför följande steg.

Följ stegen nedan för att signera android-paketet med hjälp av tillverkarens tangenter:

1. Hämta appen från Google Play eller från [AEM Screens Player Downloads](https://download.macromedia.com/screens/) page
1. Hämta plattformstangenterna från tillverkaren för att få en *pk8* - och en *pem* -fil

1. Leta reda på verktyget apksigner i android sdk med hjälp av sök ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Hitta sökvägen till ZIP-justeringsverktyget i android sdk
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installera ***aemscreensaligned.apk*** med adb install på enheten

## Android-övervakning {#android-watchdog-implementation}

Övervakningstjänsten för hela Android implementeras som ett plugin-program för cordova med *AlarmManager*.

I följande diagram visas implementeringen av tjänsten watchdog:

![chlimage_1-31](assets/chlimage_1-31.png)

**1. Initiering** När cordova-pluginprogrammet initieras kontrolleras behörigheterna för att se om vi har systembehörighet och därmed behörighet att starta om. Om dessa två villkor är uppfyllda skapas en väntande metod för omstart, annars skapas en väntande metod för att starta om programmet (baserat på dess startaktivitet).

**2. Keep Alive Timer** En Håll aktiv-timer används för att utlösa en händelse var femtonde sekund. I så fall måste du avbryta den befintliga väntande metoden (för att starta om eller starta om programmet) och registrera en ny väntande metod för samma 60 sekunder i framtiden (vilket i själva verket innebär att omstarten skjuts upp).

>[!NOTE]
>
>I Android används *AlarmManager* för att registrera *pendingIntents* som kan köras även om appen har kraschat och dess alarmleverans är inexakt från API 19 (Kitkat). Behåll mellanrum mellan timerns intervall och *AlarmManagers* *pendingIntents* larm.

**3. Programmet kraschar** Om en krasch inträffar återställs inte längre den pendingIntent för omstart som är registrerad med AlarmManager. Därför körs en omstart eller omstart av programmet (beroende på vilka behörigheter som är tillgängliga när cordova-pluginprogrammet initieras).
