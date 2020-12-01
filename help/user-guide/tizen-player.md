---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till sidan [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) för att hämta Tizen Player.

1. Installera Tizen-spelarfilen (.zip) från den lokala datorn.

## Konfigurera den lokala servern och extraherar zip-filer {#setting-local-server}

Följ stegen nedan för att konfigurera den lokala servern och kopiera de extraherade filerna:

1. Hämta IP-adressen för den lokala datorn.
   >[!NOTE]
   >Läs den officiella dokumentationen och lär dig hur du aktiverar den lokala servern på din plattform.

1. I Terminal navigerar du till samma katalog i den uppzippade installationsmappen och kontrollerar om den lokala värden fungerar.

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

1. Kopiera de två extraherade filerna som `AEMScreensPlayer.wgt` och `sssp_config.xml` till rotkatalogen på den lokala servern.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens-spelaren på enheten:

1. Gå till din Samsung-enhet.

1. Klicka på knappen **Hem** på enhetens fjärrdator och välj **URL Launcher Settings**.

1. Ange IP-adressen till den lokala värdservern.

1. Välj **Fjärr** i **Utvecklarläge**.

1. Klicka på knappen **Hem** på enhetens fjärr och välj **URL Launcher**.

1. AEM Screens Player bör nu installeras och startas automatiskt på din Samsung-enhet.



