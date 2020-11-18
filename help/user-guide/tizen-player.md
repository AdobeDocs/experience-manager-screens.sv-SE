---
title: Tizen Player
description: På den här sidan beskrivs hur Tizen Player installeras och fungerar.
translation-type: tm+mt
source-git-commit: baefade9fa013bc77ed1f112d0ad2098c992dde5
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Implementera Tizen Player {#tizen-player}

## Installerar Tizen Player {#installing-tizen-player}

Följ stegen nedan för att implementera Tizen Player för AEM Screens:

1. Gå till [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) för att ladda ned Tizen Player.

1. Installera Tizen-spelarfilen (.zip) från den lokala datorn.

1. Hämta IP-adressen för den lokala datorn.

   >[!NOTE]
   >I terminalen på datorn skriver du följande kommandon för:
   >**Mac** use command `ifconfig`
   >**Windows**, använd kommando `ipconfig`

1. I Terminal navigerar du till samma katalog i den uppzippade installationsmappen och kontrollerar om den lokala värden fungerar.

   >[!NOTE]
   >I **Mac** skriver du `http://localhost` och kontrollerar om `http` servern körs.

1. Tizen-spelaren hämtar installationsprogrammet från den lokala servern.

1. Kopiera de två extraherade filerna `AEMScreensPlayer.wgt` och `sssp_config.xml` till `/Library/WebServer/Documents`.

### Konfigurationsuppdateringar på Samsung-enheten {#config-updates}

Följ stegen nedan på Samsung-enheten för att slutföra installationen av AEM Screens-spelaren på enheten:

1. Klicka på knappen **Hem** från Samsung Remote.
1. Välj **URL-startprogram** i **Inställningar**.
1. Välj **Fjärr** i utvecklarläget.
1. Installera Web App och ange datorns IP-adress.
AEM Screens Player bör installeras automatiskt på Samsung-enheter.


