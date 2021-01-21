---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: 2ace2f926900304377afcd6187462545a60784d3
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 1%

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

## Massetablering av Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Det kan vara tidsödande att manuellt ange AEM-serverns adress i administratörsgränssnittet för varje enhet för ett stort antal enheter. Vi rekommenderar att du använder Samsung Remote Management-lösning (RMS) för att distribuera och hantera större lösningar. Mer information finns i [Registrera Tizen-enheten för Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm).

Följ stegen nedan om du vill att programmet ska etableras gruppvis och peka på AEM författarinstans när det startas:

1. Hämta och installera [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Öppna `wgt`-filen med Tizen studio.
1. Öppna filen `firmware-platform.js` och sök efter `DEFAULT_PREFERENCES` och ändra server-URL:en till AEM författares URL och spara.
1. Skapa den nya `wgt`-filen.

   >[!NOTE]
   >Du kan behöva skapa eller konfigurera ett signeringscertifikat.

1. Distribuera den nya `wgt`-filen med RMS eller URL Launcher. När spelaren startas ska den automatiskt peka mot servern så att du inte behöver ange den manuellt för varje enhet.

### Registrera den tizen-enheten på Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

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

