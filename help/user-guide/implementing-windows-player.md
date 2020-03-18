---
title: Implementera Windows 10 Player
seo-title: Implementera Windows 10 Player
description: Följ den här sidan om du vill veta mer om hur du konfigurerar AEM Screens Windows 10 Player.
seo-description: Följ den här sidan om du vill veta mer om hur du konfigurerar AEM Screens Windows 10 Player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: 9e7c4ec77265c1b6927a19e0d9d39770b64db0fb

---


# Implementera Windows 10 Player {#implementing-windows-player}

I det här avsnittet beskrivs hur du konfigurerar AEM Screens Windows 10 Player. Den innehåller information om konfigurationsfilen, tillgängliga alternativ och rekommendationer om vilka inställningar som ska användas för utveckling och testning.

## Installerar Windows Player {#installing-windows-player}

Installera Windows Player för AEM-skärmar om du vill implementera Windows Player för AEM-skärmar.

Gå till [**sidan AEM 6.4 Player Downloads **](https://download.macromedia.com/screens/).

### Ad-Hoc-metod {#ad-hoc-method}

Med metoden Ad-Hoc kan du installera den senaste versionen av Windows Player (*.exe*). Besök [**sidan AEM 6.4 Player Downloads **](https://download.macromedia.com/screens/).

När du har hämtat programmet följer du stegen på spelaren för att slutföra ad hoc-installationen:

1. Tryck länge på det övre vänstra hörnet för att öppna administrationspanelen.
1. Navigera till **Konfiguration** på den vänstra åtgärdsmenyn och ange platsen (adressen) för den AEM-instans som du vill ansluta till och klicka på **Spara**.
1. Navigera till länken **Device** **Registration** (Enhetsregistrering) i den vänstra åtgärdsmenyn för att kontrollera status för enhetsregistreringsprocessen.

>[!NOTE]
>
>Om **läget** är **REGISTRERAT** kommer du att se att fältet **Enhets-ID** fylls i.
>
>Om **tillståndet** är **OREGISTRERAT** kan du använda **Token** för att registrera enheten.

### Konfiguration av massserver: Registrera flera Windows 10-spelare med en konfiguration {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

När du har installerat Windows Player kan du registrera flera spelare med en konfiguration.

>[!NOTE]
>
>**Massregistrering av Windows Player**
>
>När du implementerar Windows-spelaren behöver du inte konfigurera varje enskild spelare manuellt. I stället kan du uppdatera JSON-konfigurationsfilen när den har testats och är klar för distribution.
>
>Konfigurationen ser till att alla spelare pingar samma server som finns i konfigurationsfilen. Du måste fortfarande registrera varje spelare manuellt.

Följ stegen nedan för att konfigurera Windows 10 Player:

1. Installera Windows Player.
1. Hitta konfigurationsfilen under ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Uppdatera konfigurations-JSON med hjälp av informationen nedan och kopiera sedan samma mapp till alla system där spelaren finns.

### Principattribut {#policy-attributes}

I följande tabell sammanfattas principattributen med en exempelpolicy-JSON för referens:

| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till AEM-servern (Adobe Experience Manager). |
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
>Adobe rekommenderar en enhetshanteringslösning för att aktivera Kiosk för Windows. Följ stegen nedan om du inte har någon enhetshanteringslösning för att aktivera Kiosk-läget. Den här metoden använder Shell Launcher-funktionen som finns i Windows 10 Enterprise och Edu. Alla andra rekommenderade metoder från Microsoft för program som inte är UWP kan också användas för att aktivera Kiosk, särskilt i andra utgåvor av Windows.

Aktivera Kiosk-läget genom att följa stegen nedan:

>[!NOTE]
>
>Innan du följer stegen nedan kontrollerar du att du använder Windows 10 Enterprise eller Education.

1. Aktivera Shell Launcher.

   Mer information finns i avsnittet ***Konfigurera Shell Launcher*** på **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)**-sidan av Microsoft Windows-stöd.

1. Skapa en icke-administrativ användare (om du inte redan har någon) som ska användas för Kiosk. Detta kan vara en lokal användare eller en domänanvändare.
1. Installera Windows-spelaren för den Kiosk-användaren från [sidan AEM Screens Player Downloads](https://download.macromedia.com/screens/) .
1. Mer information finns i [Use Shell Launcher (Använd Shell Launcher) för att skapa en Windows 10-kioskdator](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) för att ändra PowerShell-skriptet.

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
>*set-execution policy unlimited* - för att tillfälligt ta bort begränsningar
>
>*set-execution policy limited* - för att återaktivera begränsning efter att skriptet har körts

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

