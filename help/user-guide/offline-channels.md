---
title: Offlinekanaler
description: Läs mer om hur AEM Screens Player ger offlinesupport för kanaler med hjälp av ContentSync-tekniken.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# Offlinekanaler {#offline-channels}

Screens-spelaren tillhandahåller offlinesupport för kanalerna med hjälp av tekniken ***ContentSync*** .

Spelarna använder en lokal http-server för att hantera det uppackade innehållet.

När en kanal har konfigurerats för att köra *online*, visar spelaren kanalresurserna genom att gå till AEM. När kanalen är konfigurerad att köra *offline*, visar spelaren kanalresurserna från en lokal http-server.

Arbetsflödet är följande:

1. Tolka de önskade sidorna.
1. Samla in alla relaterade resurser.
1. Paketera allt i en zip-fil.
1. Ladda ned zip-filen och extrahera den lokalt.
1. Visa en lokal kopia av innehållet.

## Uppdatera hanterare {#update-handlers}

***ContentSync*** använder uppdateringshanterare för att analysera och samla in alla nödvändiga sidor och resurser för ett visst projekt. AEM Screens använder följande uppdateringshanterare:

### Vanliga alternativ {#common-options}

* *typ*: den uppdateringshanterartyp som ska användas
* *sökväg*: sökväg till resursen
* *[targetRootDirectory]*: målmapp i zip-filen

<table>
 <tbody>
  <tr>
   <td><strong>Typ</strong></td> 
   <td><strong>Beskrivning</strong></td> 
   <td><strong>Alternativ</strong></td> 
  </tr>
  <tr>
   <td><code>channels</code></td> 
   <td>samlar in en kanal</td> 
   <td>tillägg: tillägg för resursen för att samla in <br /> [pathSuffix='']: suffix att lägga till i kanalsökvägen <br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>samla in angivet klientbibliotek</td> 
   <td>[extension='']: kan vara antingen css eller js, för att bara samla in den första, eller bara den senare</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>samla in resursåtergivningar</td> 
   <td>[renditions=[]]: lista över renderingar som ska samlas in. Standardvärdet är den ursprungliga återgivningen</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>kopiera den angivna strukturen från sökvägen</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Testar konfigurationen av ContentSync {#testing-contentsync-configuration}

Följ stegen nedan för att testa ContentSync-konfigurationen:

1. Öppna `https://localhost:4502/libs/cq/contentsync/content/console.html`.
1. Klicka på din konfiguration i listan.
1. Klicka på **Rensa cache**.
1. Klicka på **Uppdatera cache**.
1. Klicka på **Hämta fullständig**.
1. Extrahera zip-filen.
1. Starta en lokal server i den extraherade mappen.
1. Öppna startsidan och kontrollera din appstatus.

## Aktivera offlinekonfiguration för en kanal {#enabling-offline-config-for-a-channel}

Följ stegen nedan för att aktivera offlinekonfiguration för en kanal:

1. Inspect kanalinnehållet och kontrollera om det begärs från en AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Navigera till kanalkontrollpanelen.
1. Klicka på **..** på panelen **KANALINFORMATION**.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Navigera till kanalegenskaperna.
1. Kontrollera att kryssrutan är inaktiverad på fliken ((Kanal)) och klicka sedan på **Spara och stäng**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Klicka på **Uppdatera offlineinnehåll** innan innehållet distribueras korrekt till enheten.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Statusen **Offline** under **EGENSKAPER** uppdateras också.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect kanalinnehållet och kontrollera om det efterfrågas från den lokala spelarcachen.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Läs mer om mallen för anpassade offlineresurshanterare. Och läs mer om minimikraven i `pom.xml` för projektet. Se [Mall för anpassade hanterare](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) i **Utveckla en anpassad komponent för AEM Screens**.
