---
title: Implementera Windows Player
description: Läs om hur du konfigurerar Windows Player i AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Implementera Windows Player {#implementing-windows-player}

I det här avsnittet beskrivs hur du konfigurerar Windows Player i AEM Screens. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

## Installerar Windows Player {#installing-windows-player}

Installera Windows Player för AEM Screens om du vill implementera Windows Player för AEM Screens.

Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

>[!NOTE]
>Det finns inget fönsterläge i Windows Player. Det är alltid i helskärmsläge.

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Konfigurera en miljö för Windows Player om du använder AEM Screens 6.5.5 Service Pack.

Ange attributet **SameSite för inloggningstokencookies** från **Lax** till **None** från **Adobe Experience Manager Web Console
Konfiguration** för alla AEM-författare och publiceringsinstanser.

Följ stegen nedan:

1. Navigera till **Adobe Experience Manager Web Console
Konfiguration** med `http://localhost:4502/system/console/configMgr` .

1. Sök efter *Autentiseringshanterare för Adobe Granite-token*.

1. Ange attributet **SameSite för inloggningstokencookies** från **Lax** till **None**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Klicka på **Spara**.

### Ad-Hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste Windows Player (*.exe*). Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administratörspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM-instans som du vill ansluta till och klicka på **Spara**.
1. Navigera till länken **Enhet** **Registrering** från den vänstra åtgärdsmenyn så att du kan kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **Läge** är **REGISTRERAT** bör du tänka på att fältet **Enhets-ID** är ifyllt.
>
>Om **State** är **UNREGISTERED** kan du använda **Token** för att registrera enheten.

## Namnge Windows Player {#name-windows}

Du kan tilldela ett användarvänligt enhetsnamn till Windows Player och på så sätt skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge Windows Player utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Windows Player:

1. Klicka på **start** > **run**.
1. Ange `system.cpl`.
1. Använd fliken Datornamn för att ange datorns värdnamn.

## Ändra standardalternativen i Windows Installer {#changing-default-options}

Följ det här avsnittet så får du lära dig hur du ändrar standardalternativen i Windows Installer och listan över tillgängliga anpassningar.

## Installation med CLI (PowerShell) {#install-powershell}

1. Skapa en anpassad plats **dedikerad** för Screens Player, till exempel:
   `C:\Users\User\screens-player`
1. Installera
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Öppna
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Exempel**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Massregistrering av Windows Player {#bulk-registration}

När du implementerar Windows Player behöver du inte konfigurera alla spelare manuellt. I stället kan du uppdatera JSON-konfigurationsfilen när den har testats och är klar för distribution.

Konfigurationen ser till att alla spelare pingar samma server som finns i konfigurationsfilen. Registrera varje spelare manuellt.

Följ stegen nedan för att konfigurera Windows 10 Player:

1. Installera Windows Player.
1. Hitta konfigurationsfilen under ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Uppdatera konfigurations-JSON med hjälp av informationen nedan och kopiera sedan samma mapp till alla system där spelaren finns.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:


| **Principnamn** | **Syfte** |
|---|---|
| server | URL till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Du bör ange värdet false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera så att du kan visa förloppet för aktiviteter, som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Windows Player ska ansluta till Screens as a Cloud Service. Anges till false för att ansluta till AMS eller lokal AEM. |
| cloudToken | Registreringstoken för registrering mot Screens as a Cloud Service. |

#### Exempel på princip-JSON-fil {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## Aktivera helskärmsläge {#enabling-kiosk-mode}

När du distribuerar Windows Player är det viktigt att aktivera ett Kiosk-läge så att andra program eller aktivitetsfältet inte visas på skrivbordet i Windows.

>[!CAUTION]
>
>Adobe rekommenderar en enhetshanteringslösning för att aktivera Kiosk för Windows. Följ stegen nedan om du inte har någon enhetshanteringslösning för att aktivera Kiosk-läget. Den här metoden använder Shell Launcher-funktionen som finns i Windows 10 Enterprise och Edu. Alla andra sätt som rekommenderas av Microsoft för icke-UWP-program kan också användas för att aktivera Kiosk, särskilt i andra utgåvor av Windows.

Aktivera Kiosk-läget genom att följa stegen nedan:

>[!NOTE]
>
>Innan du följer stegen nedan kontrollerar du att du använder Windows 10 Enterprise eller Education.

1. Aktivera Shell Launcher.

   Mer information finns på sidan ***Konfigurera Shell Launcher*** på sidan **[Shell Launcher](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/)** av Microsoft® Windows-stöd.

1. Skapa en icke-administrativ användare (om du inte redan har någon) som ska användas för Kiosk. Det kan vara en lokal användare eller en domänanvändare.
1. Installera Windows Player för den Kiosk-användaren från sidan [AEM Screens Player-hämtningar](https://download.macromedia.com/screens/).
1. Mer information finns i [Använd Shell Launcher för att skapa en Windows 10-kioskdator](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/?tabs=intune) för att ändra PowerShell-skriptet.

   Ändra PowerShell-skriptet så att du kan ersätta användarnamnet med det du skapade. Kontrollera att sökvägen till den körbara programfilen är korrekt. Detta anger det anpassade skalet som Windows Player-program för heltalsanvändaren och anger standardvärdet som explorer.exe för andra användare.

1. Kör PowerShell-skriptet som administratör.
1. Starta om och logga in som Kiosk-användare och uppspelningsprogrammet bör starta direkt.

### Felsökning {#troubleshooting}

Om du får en svart skärm när du har loggat in som Kiosk-användare betyder det att du felaktigt har angett sökvägen till den körbara Windows Player-filen. Logga in igen som administratör och verifiera och kör skriptet igen.

Standardinstallationssökvägen för Windows Player är:

***C:\Users\&lt;din användare>\AppData\Local\Programs\@aem-screensscreens-player-elektron\AEM Screens Player.exe***

Exempelskriptet i länkarna aktiverar och inaktiverar det anpassade skalet. Dela därför upp skriptet i två delar och aktivera/inaktivera nedanstående rader:

>[!NOTE]
>
>I vissa Windows-miljöer begränsas PowerShell-skript av en princip, särskilt om skripten är osignerade. Om du vill köra skriptet inaktiverar och aktiverar du den här begränsningen tillfälligt för att köra skriptet. Öppna ett PowerShell-fönster och använd dessa kommandon.
>
>*`set-executionpolicy unrestricted`* - om du vill ta bort begränsningar tillfälligt.
>
>*`set-executionpolicy restricted`* - för att återaktivera begränsning efter att skriptet har körts.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Använda Screens fjärrkontroll {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Screens fjärrkontroll](implementing-remote-control.md)