---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
feature: Administrera skärmar, spelare
role: Administrator
level: Intermediate
source-git-commit: ee731bc5169d2c76665bbfa18e3b8529619d83ce
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till sidan [AEM Screens Player Downloads](https://download.macromedia.com/screens/) för att hämta Tizen Player.

1. Installera Tizen-spelaren *(.zip)*-filen från den lokala datorn.

## Konfigurera den lokala servern och extraherar zip-filer {#setting-local-server}

>[!NOTE]
> Extrahera zip-filen och gör Tizen-spelaren tillgänglig via en `http server`. (`http server` behöver inte vara lokal server eller Apache-server).

Följ stegen nedan:

1. Kopiera de två extraherade filerna som `AEMScreensPlayer.wgt` och `sssp_config.xml` till rotkatalogen för den lokala Apache-webbservern.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`är det faktiska Tizen-spelarprogrammet och `sssp_config.xml` innehåller information om kartan som hjälper dig att installera den på Tizen-enheten.

1. Hämta IP-adressen eller URL-adressen för den lokala HTTP-servern (och sökvägen till mappen som innehåller de extraherade filerna i steg 2 om de extraheras till en undermapp och inte till rotmappen)

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

### Namnge Tizen Player {#name-tizen}

Du kan tilldela din Tizen-spelare ett användarvänligt enhetsnamn och därmed skicka det tilldelade enhetsnamnet till Adobe Experience Manager (AEM). Den här funktionen gör det inte bara möjligt att namnge Tizen-spelaren, utan även att du enkelt kan tilldela rätt innehåll.

Följ stegen nedan för att konfigurera namnet i Tizen-spelaren:

1. Klicka på menyknappen på fjärrkontrollen.
1. Navigera till **nätverk** —> **Enhetsnamn** för att tilldela spelaren ett namn.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens-spelaren på enheten:

1. Navigera till din Samsung-enhet och aktivera.

1. Klicka på knappen **MENU** på enhetens fjärr och bläddra nedåt till **System** i det vänstra navigeringsfältet.

1. Bläddra nedåt och välj alternativet **Spela upp via** och ändra det till **URL Launcher**.
   ![bild](/help/user-guide/assets/tizen/rms-2.png)

1. När URL-startaren har angetts trycker du på **Home**-knappen på fjärrkontrollen.

1. Navigera till **URL Launcher Settings** och ange IP-adressen för den lokala värdservern och klicka på **Done**.
   >[!NOTE]
   >Tizen-spelaren bör kunna ansluta till http-servern.

1. AEM Screens Player bör nu installeras och startas automatiskt på din Samsung-enhet.

   >[!NOTE]
   >Både Tizen-enheten och `http`-servern ska kunna ansluta till varandra, det vill säga servern ska kunna nås till Tizen-spelaren.


## Undantag för användaragenter med Cookie-problemet för samma webbplats {#exempting-user-agents}

>[!IMPORTANT]
>**Detta avsnitt gäller Adobe Experience Manager (AEM) 6.5.5 till AEM 6.5.7**
>Det finns webbläsarmotorer som är inkompatibla med attributet *SameSite=None* som används i inloggningstoken som utfärdas av AEM 6.5 till AEM 6.7. I de flesta fall kan problemet lösas genom att du uppgraderar webbläsaren till den senaste tillgängliga versionen. I vissa fall är sådana uppgraderingar inte möjliga, t.ex. för smarta skärmar, digitalboxar eller andra enheter med inbäddade webbläsarmotorer.

Följ stegen nedan för att undanta dessa inkompatibla klienter när du använder *SameSite=None*:

1. Uppgradera till Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. När AEM startat om går du till `/system/console/configMgr` och söker efter **Autentiseringshanteraren för Adobe Granite-token**. Ange värdet **SameSite** som **None**.

1. Du bör se ett nytt alternativ *Användaragenter som ska undantas från samma platsattribut*. Fyll i detta med en regex som motsvarar användaragenten/användaragenterna som är inkompatibla med attributet *SameSite=None*.
   >[!NOTE]
   >Se [SameSite=None: Kända inkompatibla klienter](https://www.chromium.org/updates/same-site/incompatible-clients) för mer information. För Tizen-spelaren använder du regex: `(.*)Tizen(.*)`.

1. Registrera Tizen-spelaren mot din AEM 6.5.5 och senare och registrera och visa innehåll normalt.

## Fjärretablering av Tizen-spelaren {#remote-provisioning}

Genom att fjärrdistribuera Tizen Player kan du utan ansträngning driftsätta hundratals och tusentals Samsung Tizen-skärmar. Man slipper det tidsödande arbetet med att konfigurera varje spelare med server-URL:en och massregistreringskoden, eller andra parametrar, och när det gäller skärmar som en Cloud Service för att konfigurera molnläge och molntoken.

Med den här funktionen kan du fjärrkonfigurera Tizen-spelaren och även uppdatera dessa konfigurationer centralt, om det behövs. Allt du behöver är `HTTP`-servern som används som värd för Tizen-programmet `(wgt and xml file)` och en textredigerare som sparar `config.json` med lämpliga parametrar.

Kontrollera att du har konfigurerat startadressen för URL-adressen på enheten Tizen, det vill säga startinställningen för Hem-knappen —> URL-startinställningar.
På `HTTP`-servern som är värd för Tizen-programmet placerar du filen `config.json` på samma plats som `wgt`-filen. Filnamnet måste vara `config.json`.
Tizen-spelaren installeras och vid start (och varje omstart) kontrolleras och inställningarna i `config.json`-filen tillämpas.

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

### Principattribut och syfte {#policy-attributes}

I följande tabell sammanfattas profilerna med deras funktioner.

>[!NOTE]
>Principkonfigurationer används strikt och åsidosätts inte manuellt i spelarens administratörsgränssnitt. Om du vill tillåta manuell spelarkonfiguration för en viss princip ska du inte ange principen i principkonfigurationen. Om du till exempel vill tillåta manuell konfiguration för omstartschema ska du inte ange nyckeln `rebootSchedule` i principkonfigurationen. Principkonfigurationer läses upp varje gång spelaren läses in igen.

| **Principnamn** | **Syfte** |
|---|---|
| server | URL:en till Adobe Experience Manager-servern (AEM). |
| registrationKey | Används för massregistrering av enheter med hjälp av i förväg delad nyckel. |
| upplösning | Enhetens upplösning. |
| rebootSchedule | Schemat för att starta om spelaren. |
| enableAdminUI | Aktivera administratörsgränssnittet för att konfigurera enheten på platsen. Anges till false när den är helt konfigurerad och i produktion. |
| enableOSD | Aktivera kanalväljarens användargränssnitt så att användare kan växla kanaler på enheten. Överväg att ställa in på false när den är helt konfigurerad och i produktion. |
| enableActivityUI | Aktivera om du vill visa förloppet för aktiviteter som hämtning och synkronisering. Aktivera för felsökning och inaktivera när den är helt konfigurerad och i produktion. |
| cloudMode | Ange true om du vill att Tizen-spelaren ska ansluta till skärmar som Cloud Service. Ange som false för att ansluta till AMS eller AEM. |
| cloudToken | Registreringstoken för registrering mot skärmar som Cloud Service. |


## Registrera den tizen-enheten på Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Följ stegen nedan för att registrera Tizen-enheten till Samsung Remote Management Service (RMS) och fjärrkonfigurera URL-startprogrammet:

>[!NOTE]
>Kontrollera nätverksinställningarna och övervakaren.

1. Navigera till **Meny** -> **Nätverk** -> **Servernätverksinställningar** och tryck på **Enter**.

1. Navigera till Serveradress och skriv in MagicInfo URL-åtkomst och tryck på **Done**.

1. Konfigurera TLS, om det behövs. Navigera till porten och markera portnumret på servern och klicka på **Spara**.

1. Navigera till fliken **Device** och sök efter den enhet du just konfigurerade. När en enhet hittas klickar du i kryssrutan och väljer **Godkänn**.

   >![bild](/help/user-guide/assets/tizen/rms-3.png)

1. Fyll i nödvändig information och välj en enhetsgrupp. Klicka på **OK** för att slutföra godkännandeprocessen.

   >![bild](/help/user-guide/assets/tizen/rms-7.png)

1. När enheten har godkänts ska den visas i enhetslistan. Klicka på knappen *Information* i enhetsrutan, d.v.s. **i**, enligt bilden nedan.

   >![bild](/help/user-guide/assets/tizen/rms-6.png)

1. Dialogrutan för enhetsinformation visas. Välj fliken **Enhetsinformation** och klicka på **Redigera**.

   >![bild](/help/user-guide/assets/tizen/rms-5.png)

1. Redigera enhetsalternativen och välj fliken **Inställningar**. Navigera till **URL Launcher** och ange webbadress som är värd för widgeten och `SSSP config file` för att installera ett `SSSP`-program, som bilden nedan visar.

   ![bild](/help/user-guide/assets/tizen/rms-9.png)

1. Klicka på **Spara** så visas ändringarna på visningsskärmen.

