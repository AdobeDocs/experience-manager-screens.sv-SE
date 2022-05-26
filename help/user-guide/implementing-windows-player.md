---
title: Implementera Windows 10 Player
seo-title: Implementing Windows 10 Player
description: Följ den här sidan om du vill veta mer om hur du konfigurerar AEM Screens Windows 10 Player.
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 97bc64ce3c01ac2de301b17bf9f8610662d45f88
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 0%

---

# Implementera Windows 10 Player {#implementing-windows-player}

I det här avsnittet beskrivs hur du konfigurerar AEM Screens Windows 10 Player. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

## Installerar Windows Player {#installing-windows-player}

Installera Windows Player för AEM Screens om du vill implementera Windows Player för AEM Screens.

Besök [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) sida.

>[!NOTE]
>Det finns inget fönsterläge i Windows Player. Det är alltid helskärmsläge.

### Konfigurera miljö för AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Du måste konfigurera en miljö för Windows Player om du använder AEM Screens 6.5.5 Service Pack.

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

1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM instansen som du vill ansluta till och klicka på **Spara**.
1. Navigera till **Enhet** **Registrering** på den vänstra åtgärdsmenyn för att kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **Läge** är **REGISTRERAD** kommer du att lägga märke till **Enhets-ID** fältet fylls i.
>
>Om **Läge** är **OREGISTRERAD** kan du använda **Token** för att registrera enheten.

## Namnge Windows Player {#name-windows}

Du kan tilldela din Windows-spelare ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge Windows-spelaren utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Windows Player:

1. Klicka på **start** —> **run**
1. Retur `system.cpl`
1. Använd fliken Datornamn för att ange datorns värdnamn

## Ändra standardalternativen i Windows Installer {#changing-default-options}

Följ det här avsnittet för att lära dig hur du ändrar standardalternativen i Windows Installer och listan över tillgängliga anpassningar.

## Installation med CLI (PowerShell) {#install-powershell}

1. Skapa en egen plats **dedikerad** för Screens Player, till exempel:
   `C:\Users\User\screens-player`)
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

När du implementerar Windows-spelaren behöver du inte konfigurera varje enskild spelare manuellt. I stället kan du uppdatera JSON-konfigurationsfilen när den har testats och är klar för distribution.

Konfigurationen ser till att alla spelare pingar samma server som finns i konfigurationsfilen. Du måste fortfarande registrera varje spelare manuellt.

Följ stegen nedan för att konfigurera Windows 10 Player:

1. Installera Windows Player.
1. Sök efter konfigurationsfilen under ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Uppdatera konfigurations-JSON med hjälp av informationen nedan och kopiera sedan samma mapp till alla system där spelaren finns.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:

| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till Adobe Experience Manager-servern (AEM). |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Överväg att ställa in på false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera om du vill visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |

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

När du distribuerar Windows-spelaren är det viktigt att aktivera ett Kiosk-läge så att andra program eller aktivitetsfältet inte visas på Windows-skrivbordet.

>[!CAUTION]
>
>Adobe rekommenderar en enhetshanteringslösning för att aktivera Kiosk för Windows. Följ stegen nedan om du inte har någon enhetshanteringslösning för att aktivera Kiosk-läget. Den här metoden använder Shell Launcher-funktionen som finns i Windows 10 Enterprise och Edu. Alla andra av Microsoft rekommenderade metoder för icke-UWP-program kan också användas för att aktivera Kiosk, särskilt i andra utgåvor av Windows.

Aktivera Kiosk-läget genom att följa stegen nedan:

>[!NOTE]
>
>Innan du följer stegen nedan kontrollerar du att du använder Windows 10 Enterprise eller Education.

1. Aktivera Shell Launcher.

   Se avsnittet ***Konfigurera Shell Launcher*** in **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** sida med Microsoft Windows-stöd för mer information.

1. Skapa en icke-administrativ användare (om du inte redan har någon) som ska användas för Kiosk. Detta kan vara en lokal användare eller en domänanvändare.
1. Installera Windows-spelaren för den Kiosk-användaren från [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/) sida.
1. Se [Använd Shell Launcher för att skapa en Windows 10-kioskdator](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) om du vill ändra PowerShell-skriptet för mer information.

   Ändra PowerShell-skriptet så att användarnamnet ersätts med det du skapade. Kontrollera att sökvägen till den körbara programfilen är korrekt. Detta anger det anpassade skalet som Windows-spelarprogram för heltalsanvändaren och anger standardinställningen som explorer.exe för andra användare.

1. Kör PowerShell-skriptet som administratör.
1. Starta om och logga in som Kiosk-användare och uppspelningsprogrammet bör starta direkt.

### Felsökning {#troubleshooting}

Om du får en svart skärm när du loggar in som Kiosk-användare betyder det att du felaktigt har angett sökvägen till den körbara Windows-spelaren. Logga in igen som administratör och verifiera och kör skriptet igen.

Standardinstallationssökvägen för Windows Player är:

***C:\Users\&amp;lt;din användare>\AppData\Local\Programs\@aem-screensscreens-player-electron\AEM Screens Player.exe***

Exempelskriptet i länkarna aktiverar och inaktiverar det anpassade skalet. Därför kan du behöva dela upp skriptet i två delar och aktivera/inaktivera nedanstående tillämpliga rader:

>[!NOTE]
>
>I vissa Windows-miljöer kan PowerShell-skript begränsas av en princip (särskilt osignerade skript). Om du vill köra skriptet kan du behöva inaktivera och aktivera den här begränsningen tillfälligt igen för att köra skriptet. Öppna ett PowerShell-fönster och använd dessa kommandon.
>
>*exekveringsprincip utan begränsningar* - för att tillfälligt ta bort begränsningar
>
>*exekveringsprincip begränsad* - för att återaktivera begränsning efter att skriptet har körts

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Använda fjärrkontrollen till skärmar {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Fjärrkontroll för skärmar](implementing-remote-control.md)