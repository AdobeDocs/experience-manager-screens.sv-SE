---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: 4c005ace7b1da94ed527164d6cfa09666d746273
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till sidan [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) för att hämta Tizen Player.

1. Installera Tizen-spelaren *(.zip)*-filen från den lokala datorn.

## Undantag för användaragenter med Samesite Cookie-problem {#exempting-user-agents}

>[!IMPORTANT]
>**Detta avsnitt gäller AEM 6.5.5 till AEM 6.5.7**
>Det finns webbläsarmotorer som är inkompatibla med attributet *SameSite=None* som används i inloggningstoken som utfärdas av AEM 6.5 till AEM 6.7. I de flesta fall kan problemet lösas genom att du uppgraderar webbläsaren till den senaste tillgängliga versionen. I vissa fall är sådana uppgraderingar inte möjliga, t.ex. för smarta skärmar, digitalboxar eller andra enheter med inbäddade webbläsarmotorer. Om du vill undanta dessa inkompatibla klienter när du använder SameSite=None ska du göra följande:

1. Hämta filen *jar* från `https://artifactory.corp.adobe.com/artifactory/maven-aem-release-local/com/adobe/granite/crx-auth-token/2.6.10/`.

1. Navigera till `/system/console/bundles` i AEM och klicka på knappen `install/update`.

1. Installera filen `crx-auth-token` jar. Du kan behöva stänga av och starta om AEM när du har installerat den här burken eftersom den är relaterad till autentiseringen.

1. När AEM startat om går du till `/system/console/configMgr` och söker efter **Autentiseringshanteraren för Adobe Granite-token**. Ange värdet Ingen för inställningen SameSite.

1. Du bör se ett nytt alternativ *Användaragenter som ska undantas från samma platsattribut*. Fyll i detta med en regex som motsvarar användaragenten/användaragenterna som är inkompatibla med attributet *SameSite=None*.
   >[!NOTE]
   >Se [SameSite=None: Kända inkompatibla klienter](https://www.chromium.org/updates/same-site/incompatible-clients) för mer information.

1. För Tizen-spelaren använder du regex: `(.*)Tizen (4|5)(.*)` Registrera Tizen-spelaren mot AEM 6.5.5 och senare och registrera och visa innehåll normalt.


## Konfigurera den lokala servern och extraherar zip-filer {#setting-local-server}

Följ stegen nedan för att konfigurera den lokala servern och kopiera de extraherade filerna:

1. Hämta IP-adressen för den lokala datorn.
   >[!NOTE]
   >Läs den officiella dokumentationen och lär dig hur du aktiverar den lokala servern på din plattform.

1. I Terminal navigerar du till samma katalog i den uppzippade installationsmappen och kontrollerar om den lokala värden fungerar.

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

1. Kopiera de två extraherade filerna som `AEMScreensPlayer.wgt` och `sssp_config.xml` till rotkatalogen för den lokala Apache-webbservern.

   >[!NOTE]
   >`AEMScreensPlayer.wgt`är det faktiska Tizen-spelarprogrammet och `sssp_config.xml` innehåller information om kartan som hjälper dig att installera den på Tizen-enheten.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens-spelaren på enheten:

1. Navigera till din Samsung-enhet och aktivera.

1. Klicka på knappen **MENU** på enhetens fjärr och bläddra nedåt till **System** i det vänstra navigeringsfältet.

1. Bläddra nedåt och välj alternativet **Starta uppspelning via URL**.
   ![bild](/help/user-guide/assets/tizen/rms-2.png)

1. Tryck på knappen **Hem** på fjärrkontrollen.

1. Ange IP-adressen till den lokala värdservern.

1. Välj **Fjärr** i **Utvecklarläge**.

1. Klicka på knappen **Hem** på enhetens fjärr och välj **URL Launcher**.

1. AEM Screens Player bör nu installeras och startas automatiskt på din Samsung-enhet.

## Massetablering av Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Det kan vara tidsödande att manuellt ange AEM-serverns adress i administratörsgränssnittet för varje enhet för ett stort antal enheter. Vi rekommenderar att du använder Samsung Remote Management-lösning (RMS) för att distribuera och hantera lösningen. Mer information finns i [Registrera Tizen-enheten för Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm).

Följ stegen nedan om du vill att programmet ska etableras gruppvis och peka på AEM författarinstans när det startas:

1. Hämta och installera [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Öppna `wgt`-filen med Tizen studio.
1. Öppna filen `firmware-platform.js` och sök efter `DEFAULT_PREFERENCES` och ändra server-URL:en till AEM författares URL och spara.
1. Skapa den nya `wgt`-filen.

   >[!NOTE]
   >Du kan behöva skapa eller konfigurera ett signeringscertifikat.

1. Distribuera den nya RMS-filen `wgt` och när spelaren startas ska den automatiskt peka på servern så att du inte behöver ange den manuellt för varje enhet.

### Registrerar den tizen-enheten till Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Följ stegen nedan för att registrera Tizen-enheten till Samsung Remote Management Service (RMS) och fjärrkonfigurera URL-startprogrammet:

>[!NOTE]
>Kontrollera nätverksinställningarna och övervakaren.

1. Navigera till **Meny** -> **Nätverk** -> **Servernätverksinställningar** och tryck på **Enter**.

   >[!NOTE]
   >Kontrollera att skärmen är konfigurerad för att spela upp via URL-start.
   >![bild](/help/user-guide/assets/tizen/rms-2.png)

1. Navigera till Serveradress och skriv in MagicInfo URL-åtkomst och tryck på Klart.

1. Konfigurera TLS, om det behövs. Navigera till porten och välj portnumret på servern. Klicka på **Spara**.

1. Navigera till fliken Enhet och leta efter den enhet du just konfigurerade.

1. När en enhet hittas klickar du i kryssrutan och väljer **Godkänn**.

1. Fyll i nödvändig information och välj en enhetsgrupp. Klicka på **OK** för att slutföra godkännandeprocessen.

   >![bild](/help/user-guide/assets/tizen/rms-7.png)

1. När enheten har godkänts ska den visas i enhetslistan. Klicka på knappen *Information* i enhetens ruta **i**.

   >![bild](/help/user-guide/assets/tizen/rms-6.png)

1. Dialogrutan för enhetsinformation visas. Välj fliken **Enhetsinformation** och klicka på **Redigera**.

1. Redigera enhetsalternativ och välj fliken **Inställningar**. Navigera till **URL Launcher** och ange webbadress som är värd för widgeten och `SSSP config file` för att installera ett `SSSP`-program, som bilden nedan visar.

   ![bild](/help/user-guide/assets/tizen/rms-9.png)

1. Klicka på **Spara** så visas ändringarna på visningsskärmen.




