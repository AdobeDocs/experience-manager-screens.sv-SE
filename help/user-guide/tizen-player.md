---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: 5275a4ff79404e946d5aa0806fc705ab3bce2fcd
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) för att ladda ned Tizen Player.

1. Installera Tizen-spelarfilen (.zip) från den lokala datorn.

## Konfigurera den lokala servern och extrahera zip-filer {#setting-local-server}

Följ stegen nedan för att konfigurera den lokala servern och kopiera de extraherade filerna:

1. Hämta IP-adressen för den lokala datorn.

   >[!NOTE]
   >Du kan hämta IP-adressen från datorns terminal med följande kommandon:
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. I Terminal navigerar du till samma katalog i den uppzippade installationsmappen och kontrollerar om den lokala värden fungerar.

   >[!NOTE]
   >I **Mac** skriver du `http://localhost` och kontrollerar om `http` servern körs.

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

1. Kopiera de två extraherade filerna `AEMScreensPlayer.wgt` och `sssp_config.xml` till `/Library/WebServer/Documents`.

### Konfigurera uppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens-spelaren på enheten:

1. Gå till din Samsung-enhet och peka på din lokala värdserver.
1. Välj **URL-startinställningar** och ange IP-adressen till den lokala värdservern.
1. Installera webbprogram.
1. Välj **Fjärr** i **utvecklarläget**.
1. AEM Screens Player bör nu starta installationen automatiskt på din Samsung-enhet.


