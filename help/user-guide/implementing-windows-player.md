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
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 0%

---

# Implementera Windows Player {#implementing-windows-player}

I det här avsnittet beskrivs hur du konfigurerar Windows Player i AEM Screens. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

## Installerar Windows Player {#installing-windows-player}

Installera Windows Player för AEM Screens om du vill implementera Windows Player för AEM Screens.

Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) sida.

>[!NOTE]
>Det finns inget fönsterläge i Windows Player. Det är alltid i helskärmsläge.

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Konfigurera en miljö för Windows Player om du använder AEM Screens 6.5.5 Service Pack.

Ange **Attributet SameSite för cookies för inloggningstoken** från **Lax** till **Ingen** från **Konfiguration av Adobe Experience Manager Web Console** på alla AEM författare och publiceringsinstanser.

Följ stegen nedan:

1. Navigera till **Konfiguration av Adobe Experience Manager Web Console** använda `http://localhost:4502/system/console/configMgr`.

1. Sök efter *Autentiseringshanterare för Adobe Granite-token*.

1. Ange **Attributet SameSite för cookies för inloggningstoken** från **Lax** till **Ingen**.
   ![bild](/help/user-guide/assets/granite-updates.png)

1. Klicka **Spara**.

### Ad-Hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste Windows Player (*.exe*). Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) sida.

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administratörspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM instansen som du vill ansluta till och klicka på **Spara**.
1. Navigera till **Enhet** **Registrering** på den vänstra åtgärdsmenyn så att du kan kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **Läge** är **REGISTRERAD** lägger du märke till att **Enhets-ID** fältet är ifyllt.
>
>Om **Läge** är **OREGISTRERAD** kan du använda **Token** för att registrera enheten.

## Namnge Windows Player {#name-windows}

Du kan tilldela ett användarvänligt enhetsnamn till Windows Player och på så sätt skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge Windows Player utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Windows Player:

1. Klicka **start** > **run**.
1. Retur `system.cpl`.
1. Använd fliken Datornamn för att ange datorns värdnamn.

## Ändra standardalternativen i Windows Installer {#changing-default-options}

Följ det här avsnittet så får du lära dig hur du ändrar standardalternativen i Windows Installer och listan över tillgängliga anpassningar.

## Installation med CLI (PowerShell) {#install-powershell}

1. Skapa en egen plats **dedikerad** för Screens Player, till exempel:
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
1. Sök efter konfigurationsfilen under ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Uppdatera konfigurations-JSON med hjälp av informationen nedan och kopiera sedan samma mapp till alla system där spelaren finns.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:


| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Överväg att ställa in på false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera så att du kan visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Windows Player ska ansluta till skärmar as a Cloud Service. Ange som false om du vill ansluta till AMS eller AEM. |
| cloudToken | Registreringstoken för registrering mot skärmar as a Cloud Service. |

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

   Se ***Konfigurera Shell Launcher*** in **[Shell Launcher](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/customize/shell-launcher)** sida med Microsoft® Windows-stöd för ytterligare information.

1. Skapa en icke-administrativ användare (om du inte redan har någon) som ska användas för Kiosk. Det kan vara en lokal användare eller en domänanvändare.
1. Installera Windows Player för den Kiosk-användaren från [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/) sida.
1. Se [Använd Shell Launcher för att skapa en dator med Windows 10](https://learn.microsoft.com/en-us/windows/configuration/assigned-access/shell-launcher/?tabs=intune) om du vill ändra PowerShell-skriptet för mer information.

   Ändra PowerShell-skriptet så att du kan ersätta användarnamnet med det du skapade. Kontrollera att sökvägen till den körbara programfilen är korrekt. Detta anger det anpassade skalet som Windows Player-program för heltalsanvändaren och anger standardvärdet som explorer.exe för andra användare.

1. Kör PowerShell-skriptet som administratör.
1. Starta om och logga in som Kiosk-användare och uppspelningsprogrammet bör starta direkt.

### Felsökning {#troubleshooting}

Om du får en svart skärm när du har loggat in som Kiosk-användare betyder det att du felaktigt har angett sökvägen till den körbara Windows Player-filen. Logga in igen som administratör och verifiera och kör skriptet igen.

Standardinstallationssökvägen för Windows Player är:

***C:\Users\&lt;your user=&quot;&quot;>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

Exempelskriptet i länkarna aktiverar och inaktiverar det anpassade skalet. Dela därför upp skriptet i två delar och aktivera/inaktivera nedanstående rader:

>[!NOTE]
>
>I vissa Windows-miljöer kan PowerShell-skript begränsas av en princip (särskilt osignerade skript). Om du vill köra skriptet inaktiverar och aktiverar du den här begränsningen tillfälligt för att köra skriptet. Öppna ett PowerShell-fönster och använd dessa kommandon.
>
>*`set-executionpolicy unrestricted`* - för att tillfälligt ta bort begränsningar.
>
>*`set-executionpolicy restricted`* - för att återaktivera begränsning efter att skriptet har körts.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Använda fjärrkontrollen till skärmar {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Fjärrkontroll för skärmar](implementing-remote-control.md)