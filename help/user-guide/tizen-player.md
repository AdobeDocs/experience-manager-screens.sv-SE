---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 0%

---

# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Navigera till [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/) så att du kan ladda ned Tizen Player.

1. Installera Tizen Player *(.zip)* från den lokala datorn.

## Konfigurera http-servern {#setting-local-server}

>[!NOTE]
> Extrahera zip-filen och gör Tizen-spelaren tillgänglig via en `http server`. (Med `http server` måste inte vara lokal server eller Apache-server).

Följ stegen nedan:

1. Kopiera de två extraherade filerna som `AEMScreensPlayer.wgt` och `sssp_config.xml` till rotkatalogen för den lokala Apache-webbservern.

   >[!NOTE]
   >The `AEMScreensPlayer.wgt`är det faktiska Tizen-spelarprogrammet och `sssp_config.xml` innehåller information om kartan som hjälper dig att installera den på Tizen-enheten.

1. Hämta IP-adressen eller URL-adressen för den lokala HTTP-servern (och sökvägen till mappen som innehåller de extraherade filerna i steg 2 om de extraheras till en undermapp och inte till rotmappen).

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

### Namnge Tizen Player {#name-tizen}

Du kan tilldela din Tizen-spelare ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge din Tizen-spelare utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Tizen-spelaren:

1. Klicka på menyknappen på fjärrkontrollen.
1. Navigera till **nätverk** > **Enhetsnamn** så att du kan ge spelaren ett namn.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten så att du kan slutföra installationen av AEM Screens-spelaren på enheten:

1. Navigera till din Samsung-enhet och slå på.
1. Klicka på **MENY** från enhetens fjärrdator och rulla nedåt till **System** i det vänstra navigeringsfältet.
1. Bläddra nedåt och välj **Spela upp via** och ändra det till **URL Launcher** alternativ.
   ![bild](/help/user-guide/assets/tizen/rms-2.png)
1. När URL-startaren är inställd trycker du på **Startsida** från fjärrkontrollen.
1. Navigera till **Inställningar för URL-start** och ange IP-adressen till den lokala värdservern och klicka på **Klar**.

   >[!NOTE]
   >Tizen-spelaren bör kunna ansluta till http-servern.

1. AEM Screens Player installeras och startas automatiskt på din Samsung-enhet.

   >[!NOTE]
   >Både Tizen-enheten och `http` servern ska kunna ansluta till varandra, d.v.s. servern ska kunna nås till Tizen-spelaren.


## Undantag för användaragenter med samma webbplatsens cookie-problem {#exempting-user-agents}

>[!IMPORTANT]
>**Detta avsnitt gäller Adobe Experience Manager (AEM) 6.5.5 till AEM 6.5.7**
>
>Det finns vissa webbläsarmotorer som inte är kompatibla med *`SameSite=None`* attribut som används i inloggningstoken som utfärdas av AEM 6.5.5 till AEM 6.5.7. Vanligtvis kan du lösa problemet genom att uppgradera webbläsaren till den senaste tillgängliga versionen. Ibland är det inte möjligt att göra sådana uppgraderingar, till exempel med smarta skärmar, digitalboxar eller andra enheter med inbäddade webbläsarmotorer.

Följ stegen nedan för att undanta dessa inkompatibla klienter när du använder *SameSite=None*:

1. Uppgradera till Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. När AEM startat om går du till `/system/console/configMgr` och söka efter **Autentiseringshanterare för Adobe Granite-token**. Ange värdet för **SameSite** värde till **Ingen**.

1. Du bör se ett nytt alternativ *`User agents to be exempted from samesite attribute`*. Fyll i detta med en regex som motsvarar användaragenten som är inkompatibel med *SameSite=None* -attribut.

   >[!NOTE]
   >
   >Se [SameSite=None: Kända inkompatibla klienter](https://www.chromium.org/updates/same-site/incompatible-clients) för mer information. För Tizen-spelaren använder du regex: `(.*)Tizen(.*)`.

1. Registrera Tizen-spelaren mot din AEM 6.5.5 och senare och registrera och visa innehåll normalt.

## Fjärrprovisionering av Tizen Player {#remote-provisioning}

Genom att fjärrdistribuera Tizen Player kan du utan ansträngning driftsätta hundratals och tusentals Samsung Tizen-skärmar. Det undviker manuella försök att konfigurera varje spelare med server-URL och bulkregistreringskod, eller andra parametrar. Och om det finns AEM Screens as a Cloud Service, för att konfigurera molnläge och molntoken.

Med den här funktionen kan du fjärrkonfigurera Tizen-spelaren och även uppdatera dessa konfigurationer centralt, om det behövs. Allt du behöver är `HTTP` server som används som värd för Tizen-programmet `(wgt and xml file)` och en textredigerare för att spara `config.json` med lämpliga parametrar.

Kontrollera att du har konfigurerat startadressen för URL-adressen på enheten Tizen, det vill säga, Hemknapp > Inställningar för URL-start.
På `HTTP` server som är värd för Tizen-programmet, montera filen `config.json` på samma plats som `wgt` -fil. Filnamnet måste vara `config.json`.
Tizen-spelaren installeras och vid start (och varje omstart) kontrolleras och används inställningarna i `config.json` -fil.

### Exempel på JSON-princip {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Policyattribut och syfte {#policy-attributes}

I följande tabell sammanfattas profilerna med deras funktioner.

>[!NOTE]
>Principkonfigurationer används strikt och åsidosätts inte manuellt i spelarens administratörsgränssnitt. Om du vill tillåta manuell spelarkonfiguration för en viss princip ska du inte ange principen i principkonfigurationen.
>Om du till exempel vill tillåta manuell konfiguration för omstartsschema ska du inte ange nyckeln `rebootSchedule` i principkonfigurationen. Principkonfigurationer läses upp varje gång spelaren läses in igen.

| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt för att användare ska kunna växla kanaler på enheten. Överväg att ställa in på false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera så att du kan visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Tizen-spelaren ska ansluta till skärmar as a Cloud Service. Ange som false om du vill ansluta till AMS eller AEM. |
| cloudToken | Registreringstoken för registrering mot skärmar as a Cloud Service. |


## Registrera den tizen-enheten på Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Följ stegen nedan för att registrera Tizen-enheten till Samsung Remote Management Service (RMS) och fjärrkonfigurera URL-startprogrammet:

>[!NOTE]
>Kontrollera nätverksinställningarna och övervakaren.

1. Navigera till **Meny** -> **Nätverk** -> **Inställningar för servernätverk** och tryck **Retur**.

1. Navigera till Serveradress och skriv in MagicInfo URL-åtkomst och tryck på **Klar**.

1. Konfigurera TLS, om det behövs. Navigera till porten och markera portnumret på servern och markera **Spara**.

1. Navigera till **Enhet** och leta efter den enhet som du har konfigurerat. När en enhet hittas markerar du kryssrutan och väljer **Godkänn**.

   >![bild](/help/user-guide/assets/tizen/rms-3.png)

1. Fyll i nödvändig information och välj en enhetsgrupp. Välj **OK**.

   >![bild](/help/user-guide/assets/tizen/rms-7.png)

1. När enheten har godkänts visas den i enhetslistan. Välj *Information* i enhetens ruta enligt följande.

   >![bild](/help/user-guide/assets/tizen/rms-6.png)

1. Dialogrutan för enhetsinformation visas. Välj **Enhetsinfo** och markera **Redigera**.

   >![bild](/help/user-guide/assets/tizen/rms-5.png)

1. Redigera enhetsalternativen och välj **Inställningar** -fliken. Navigera till **URL Launcher** och ange webbadress som är värd för widgeten och `SSSP config file` så att du kan installera en `SSSP` som i bilden nedan.

   ![bild](/help/user-guide/assets/tizen/rms-9.png)

1. Välj **Spara**.

### Använda fjärrkontrollen till skärmar {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Fjärrkontroll för skärmar](implementing-remote-control.md)
