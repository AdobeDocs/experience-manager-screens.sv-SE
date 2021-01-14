---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: 1ec3e3541755550f719dbe53e83326d9796de14f
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till sidan [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) för att hämta Tizen Player.

1. Installera Tizen-spelaren *(.zip)*-filen från den lokala datorn.

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
   ![bild](/help/user-guide/assets/tizen/url-launcher.png)

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

Följ stegen nedan för att registrera Tizen-enheten till Samsung Remote Management Service (RMS) och fjärrkonfigurera URL Launcher:

>[!NOTE]
>Kontrollera nätverksinställningarna och övervakaren.

1. Tryck på Menu på fjärrkontrollen, gå till System och tryck sedan på Retur på Play Via.

   >[!NOTE]
   >Kontrollera att skärmen är konfigurerad för att spela upp via URL-startaren
1. Navigera till **Meny** -> **Nätverk** -> **Servernätverksinställningar** och tryck på **Enter**.

1. Navigera till Serveradress och skriv in MagicInfo URL-åtkomst och tryck på Klart.

1. Navigera till fliken Enhet när du har loggat in på MIS
1. Leta efter den enhet du just konfigurerade genom att titta på IP-adressen och/eller dess Mac-adress.
1. När en enhet hittas klickar du i kryssrutan och väljer Godkänn
1. Kontrollera att skärmen är konfigurerad för att spela upp via URL Launcher
1. Tryck på Meny på fjärrkontrollen, gå till System och tryck sedan på Retur på Play Via
1. Navigera till Meny -> Nätverk -> Servernätverksinställningar och tryck på Retur
1. Gå till Serveradress och ange MagicInfo URL-åtkomst och tryck på Klart
1. Konfigurera TLS att använda eller inte använda beroende på skiftläge
1. Gå till porten och välj portnumret på servern.
1. Klicka på Spara när alternativen är klara.



