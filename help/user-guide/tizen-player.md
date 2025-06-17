---
title: Tizen player
description: Läs om hur du installerar och arbetar med Tizen-spelaren.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---

# Implementera Tizen Player {#tizen-player}

## Installerar Tizen-spelare {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen-spelaren för AEM Screens:

1. Gå till sidan [AEM Screens Player Downloads](https://download.macromedia.com/screens/) så att du kan hämta Tizen-spelaren.

1. Installera Tizen-spelaren *(.zip)* från den lokala datorn.

## Konfigurera http-servern {#setting-local-server}

>[!NOTE]
> Extrahera zip-filen och gör Tizen-spelaren tillgänglig via en `http server`. (`http server` måste inte vara en lokal server eller Apache-server).

Följ stegen nedan:

1. Kopiera de två extraherade filerna som `AEMScreensPlayer.wgt` och `sssp_config.xml` till rotkatalogen på den lokala Apache-webbservern.

   >[!NOTE]
   >`AEMScreensPlayer.wgt` är det faktiska Tizen-spelarprogrammet och `sssp_config.xml` innehåller information om kartan som hjälper dig att installera den på Tizen-enheten.

1. Hämta den lokala HTTP-serverns IP-adress eller URL-adress (och sökvägen till mappen som innehåller de extraherade filerna i steg 2 om de extraheras till en undermapp och inte till en rotmapp).

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

### Namnge Tizen-spelare {#name-tizen}

Du kan tilldela din Tizen-spelare ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Med den här funktionen kan du inte bara namnge din Tizen-spelare utan även enkelt tilldela rätt innehåll.

>[!NOTE]
>Du kan bara välja spelarnamnet före registreringen. När spelaren har registrerats går det inte att ändra spelarens namn längre.

Följ stegen nedan för att konfigurera namnet i Tizen-spelaren:

1. Klicka på menyknappen på fjärrkontrollen.
1. Navigera till **Nätverk** > **Enhetsnamn** så att du kan tilldela spelaren ett namn.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens Player på enheten:

1. Navigera till din Samsung-enhet och slå på.
1. Klicka på knappen **MENU** på enhetens fjärrdator och bläddra nedåt till **System** i det vänstra navigeringsfältet.
1. Bläddra nedåt och klicka på alternativet **Spela upp med** och ändra det till alternativet **URL-start**.
   ![bild](/help/user-guide/assets/tizen/rms-2.png)
1. När URL-startaren är inställd trycker du på knappen **Home** på fjärrkontrollen.
1. Navigera till **URL-startinställningarna** och ange IP-adressen för den lokala värdservern och klicka på **Klar**.

   >[!NOTE]
   >Tizen-spelaren bör kunna ansluta till HTTP-servern.

1. AEM Screens Player installeras och startas automatiskt på din Samsung-enhet.

   >[!NOTE]
   >Både Tizen-enheten och `http`-servern ska kunna ansluta till varandra, det vill säga servern ska kunna nås till Tizen-spelaren.


## Undantag för användaragenter med samma webbplatsens cookie-problem {#exempting-user-agents}

>[!IMPORTANT]
>**Det här avsnittet gäller Adobe Experience Manager (AEM) 6.5.5 till AEM 6.5.7**
>
>Det finns webbläsarmotorer som är inkompatibla med attributet *`SameSite=None`* som används i inloggningstoken som utfärdas av AEM 6.5.5 till AEM 6.5.7. Vanligtvis kan du lösa problemet genom att uppgradera webbläsaren till den senaste tillgängliga versionen. Ibland är det inte möjligt att göra sådana uppgraderingar, till exempel med smarta skärmar, digitalboxar eller andra enheter med inbäddade webbläsarmotorer.

Följ stegen nedan för att undanta de här inkompatibla klienterna när du använder *SameSite=None*:

1. Uppgradera till Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. När AEM har startat om går du till `/system/console/configMgr` och söker efter **Autentiseringshanteraren för Adobe Granite-token**. Ange värdet **Ingen** för värdet **SameSite**.

1. Du bör se det nya alternativet *`User agents to be exempted from samesite attribute`*. Fyll i det här alternativet med en regex som motsvarar användaragenten som är inkompatibel med attributet *SameSite=None* .

   >[!NOTE]
   >
   >Mer information finns i [SameSite=None: Kända inkompatibla klienter](https://www.chromium.org/updates/same-site/incompatible-clients). Använd regex för Tizen-spelaren: `(.*)Tizen(.*)`.

1. Registrera Tizen-spelaren mot AEM 6.5.5 och senare och registrera och visa innehåll normalt.

## Fjärrprovisionera Tizen-spelaren {#remote-provisioning}

Genom att fjärrdistribuera Tizen-spelaren kan du utan ansträngning driftsätta hundratals och tusentals Samsung Tizen-skärmar. Det undviker manuella försök att konfigurera varje spelare med server-URL och bulkregistreringskod, eller andra parametrar. Och om det finns AEM Screens as a Cloud Service, för att konfigurera molnläge och molntoken.

Med den här funktionen kan du fjärrkonfigurera Tizen-spelaren och även uppdatera dessa konfigurationer centralt, om det behövs. Allt du behöver är `HTTP`-servern som används som värd för Tizen-programmet `(wgt and xml file)` och en textredigerare som sparar `config.json` med rätt parametrar.

Kontrollera att du har konfigurerat URL-startadressen på Tizen-enheten. Klicka på knappen Hem > Inställningar för URL-start.
På servern `HTTP` som är värd för Tizen-programmet placerar du filen `config.json` på samma plats som filen `wgt`. Filnamnet måste vara `config.json`.
Tizen-spelaren installerar och kontrollerar och tillämpar inställningarna i filen `config.json` vid start (och vid varje omstart).

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
>Spelarens Admin UI-principkonfigurationer används strikt och åsidosätts inte manuellt. Om du vill tillåta manuell spelarkonfiguration för en viss princip ska du inte ange principen i principkonfigurationen.
>&#x200B;>Om du till exempel vill tillåta manuell konfiguration för omstartsschema ska du inte ange nyckeln `rebootSchedule` i principkonfigurationen. Principkonfigurationer läses upp varje gång spelaren läses in igen.

| **Principnamn** | **Syfte** |
|---|---|
| server | URL till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Du bör ange värdet false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera så att du kan visa förloppet för aktiviteter, som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Tizen-spelaren ska ansluta till Screens as a Cloud Service. Anges till false för att ansluta till AMS eller lokal AEM. |
| cloudToken | Registreringstoken för registrering mot Screens as a Cloud Service. |


## Registrera den tizen-enheten på Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Följ stegen nedan för att registrera Tizen-enheten till Samsung Remote Management Service (RMS) och fjärrkonfigurera URL-startprogrammet:

>[!NOTE]
>Kontrollera nätverksinställningarna och övervakaren.

1. Navigera till **Meny** -> **Nätverk** -> **Inställningar för servernätverk** och tryck på **Retur**.

1. Navigera till serveradressen och skriv in MagicInfo URL-åtkomsten och tryck på **Done**.

1. Konfigurera TLS, om det behövs. Navigera till porten och klicka på portnumret på servern och klicka på **Spara**.

1. Navigera till fliken **Enhet** och sök efter den enhet som du har konfigurerat. När en enhet hittas klickar du i kryssrutan och sedan på **Godkänn**.

   >![bild](/help/user-guide/assets/tizen/rms-3.png)

1. Fyll i nödvändig information och klicka på en enhetsgrupp. Klicka på **OK**.

   >![bild](/help/user-guide/assets/tizen/rms-7.png)

1. När enheten har godkänts visas den i enhetslistan. Klicka på *Information* i enhetsrutan enligt följande.

   >![bild](/help/user-guide/assets/tizen/rms-6.png)

1. Dialogrutan för enhetsinformation visas. Klicka på fliken **Enhetsinformation** och klicka på **Redigera**.

   >![bild](/help/user-guide/assets/tizen/rms-5.png)

1. Redigera enhetsalternativen och klicka på fliken **Inställningar**. Navigera till avsnittet **URL Launcher** och ange webbadress som är värd för widgeten och `SSSP config file` så att du kan installera ett `SSSP`-program, vilket visas i bilden nedan.

   ![bild](/help/user-guide/assets/tizen/rms-9.png)

1. Klicka på **Spara**.

### Använda Screens fjärrkontroll {#using-remote-control}

AEM Screens tillhandahåller fjärrstyrningsfunktioner. Läs mer om den här funktionen här: [Screens fjärrkontroll](implementing-remote-control.md)
