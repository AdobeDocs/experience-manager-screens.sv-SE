---
title: Implementera Chrome OS Player
description: Lär dig mer om implementeringen av Chrome OS Player med Chrome Management Console.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Implementera Chrome OS Player  {#implementing-chrome-os-player}

I det här avsnittet beskrivs hur du implementerar Chrome OS Player med Chrome Management Console.

## Använda Chrome Management Console {#using-chrome-management-console}

Följ stegen nedan för att konfigurera en kromhanteringskonsol:

1. Registrera dig för Chrome Management Console. Du måste skaffa en licens för Chrome Management Console. Kontakt [Google Support](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) om du vill ha mer information om hur du hanterar Chrome-enhetsinställningar.
1. Registrera din Chrome OS-enhet i domänen och vänta i 15 minuter på att enheten ska synkroniseras med Chrome Management Console. Om du vill veta mer om att registrera en enhet för fönsterstandard klickar du på [här](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. Chrome Player finns i Chrome Web Store.

>[!NOTE]
>
>En enhetshanteringslösning som Chrome Management Console rekommenderas för driftsättning och hantering av enheter med Chrome OS. Även om det här dokumentet innehåller implementering för Chrome Management Console finns det andra leverantörer som hävdar att de tillhandahåller liknande funktioner. Kontakta leverantören av enhetshanteringsprogrammet.

## Namnge Chrome OS Player {#name-chrome}

Du kan tilldela din Chrome-spelare ett användarvänligt enhetsnamn och på så sätt skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge Chrome-spelaren utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Chrome Player:

1. Du kan också tillåta att ljud-/videointegratörer eller IT-administratörer ställer in resurs-ID och plats som en del av företagsregistreringen.

   ![bild](/help/user-guide/assets/chrome-device/chrome1.png)

1. Alternativen visas när du kan registrera enheten.

   ![bild](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Du kan ange resurs-ID som en del av företagsregistrering och i Chrome Management Console.

   ![bild](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome Players måste registreras i företagsregistrering och Chrome Player måste distribueras via Chrome Management Console, annars returneras resurs-ID tomt (till exempel Chrome som ett tillägg). Enhetsnamnet registreras endast vid registreringen. Framtida ändringar hämtas inte upp av Adobe Experience Manager (AEM).

### Aktivera helskärmsläge {#enabling-kiosk-mode}

Aktivera Kiosk-läget genom att följa stegen nedan:

1. Logga in på Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Bläddra till **Enhetshantering** > **Chrome Management** > **Enhetsinställningar**.
1. Bläddra nedåt till **Kiosk-inställningar** och klicka **Hantera Kiosk-program**.

   ![kiosk](assets/kiosk.png)

1. Välj AEM Screens Player från Chrome Web Store.

   >[!NOTE]
   >
   >En nyligen publicerad app kan ta ca 15 minuter att visa i den här listan.

1. Välj **AEM Screens Player** från **Starta Kiosk-appen automatiskt** nedrullningsbar meny.

   Det kan ta några minuter beroende på nätverket för att ändringarna ska börja gälla. Omstart rekommenderas.

#### Kontrollerar status för fjärrenhet {#checking-remote-device-status}

1. Logga in på Chrome Developer Console.
1. Bläddra till **Enhetshantering** > **Chrome Devices** och välj den enhet som du vill styra.
1. Klicka **Systemaktivitet och felsökning**.
1. Kontrollera **Starta om enhet** och **Skärminspelning** egenskaper för enheten. Du kan även kontrollera enhetsstatus och hälsoinformation.

>[!NOTE]
>
>Dessa inställningar kan aktiveras flera minuter efter att enheten har registrerats. Varje alternativ kan aktiveras över tid.

### Konfigurera fjärrkonfiguration av Chrome OS-spelare {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player är ett program som stöder Kiosk och som även aktiverar Remote Policy Configuration för Chrome OS-spelare.

Följ stegen nedan för att konfigurera olika alternativ för spelaren:

1. Logga in på Chrome Management Console.
1. Klicka **Enhetshantering** > **Chrome Management** > **Apphantering**. AEM Screens Player visas i listan.
1. Klicka på programmet **AEM Screens Player**.
1. Klicka **Kiosk-inställningar** och välj organisation (*om en testmiljö används*).
1. Klicka **överför konfigurationsfil** och överför konfigurationsprincipen (*JSon-fil*).
1. Klicka **Spara**. Starta om enheten så att du kan synkronisera principen.

>[!NOTE]
>
>Starta om enheten så att du kan synkronisera principändringar.

#### Exempel på princip-JSON-fil {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Policyattribut och syfte {#policy-attributes-and-purpose}

I följande tabell sammanfattas profilerna med deras funktioner.

| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt för att användare ska kunna växla kanaler på enheten. Överväg att ställa in på false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera så att du kan visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Chrome Player ska ansluta till skärmar as a Cloud Service. Ange som false om du vill ansluta till AMS eller AEM. |
| cloudToken | Registreringstoken för registrering mot skärmar as a Cloud Service. |

>[!NOTE]
>
>Principkonfigurationer används strikt och åsidosätts inte manuellt i spelarens administratörsgränssnitt. Om du vill tillåta manuell spelarkonfiguration för en viss princip ska du inte ange principen i ***principkonfiguration***. Om du till exempel vill tillåta manuell konfiguration för omstartsschema ska du inte ange nyckeln ***rebootSchedule*** i principkonfigurationen.

### Använda fjärrkontrollen till skärmar {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Fjärrkontroll för skärmar](implementing-remote-control.md)
