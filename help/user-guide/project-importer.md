---
title: Ny projektimporterare från fil
description: Med den här funktionen kan du massimportera en uppsättning platser från ett CSV-/XLS-kalkylblad till ditt AEM Screens-projekt.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# Ny projektimporterare från fil {#new-project-importer-from-file}

I det här avsnittet beskrivs en funktion för att massimportera en uppsättning platser från ett CSV-/XLS-kalkylblad till ditt AEM Screens-projekt.

## Introduktion {#introduction}

När du skapar ett AEM Screens-projekt för första gången i organisationen skapar du även alla platser. Om ditt projekt omfattar många platser resulterar det i en långsam uppgift som innebär att du väljer och väntar mycket i användargränssnittet.

Målet med den här funktionen är att minska den tid som krävs för att ställa in projektet och därmed lösa budgeteringsproblem.

Genom att låta författaren tillhandahålla ett kalkylblad som en indatafil, och låta systemet automatiskt skapa platsträdet i bakänden, den här funktionen:

* *uppnår mycket bättre prestanda än att välja manuellt via gränssnittet*
* Med *kan kunden exportera de platser som de har från sitt eget system och enkelt importera dem direkt till AEM*

Denna process sparar både tid och pengar vid den första projektinstallationen eller vid utvidgning av den befintliga AEM Screens till nya platser.

## Arkitektöversikt {#architectural-overview}

I följande diagram visas en översikt över arkitekturen för Project Importer-funktionen:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Datamodell {#data-model}

Datamodellen för Project Importer beskrivs nedan:

>[!NOTE]
>
>Den aktuella versionen har bara stöd för importplatser.

| **Egenskap** | **Beskrivning** |
|---|---|
| ***`path {string*}`*** | Resurssökvägen för platsen |
| ***`[./jcr:title] {string*}`*** | Namnet på mallen som ska användas (det vill säga platsen för *skärmar/kärna/mallar/plats*) |
| ***`template {string}`*** | Valfri titel att använda för sidan |
| ***`[./jcr:description] {string}`*** | Valfri beskrivning som ska användas för sidan |

Kalkylbladsfilen (CSV/XLS) kräver därför följande kolumner:

* **sökväg{string}** - Sökvägen till platsen som ska importeras, där sökvägen är platsmappen för projektet (det vill säga *`/foo`* importeras till *`/content/screens/<project>/locations/foo`*)
* **template{string}** - Den mall som ska användas för den nya platsen är för närvarande det enda tillåtna värdet &quot;location&quot;, men det här värdet utökas till alla `Screens` -mallar i framtiden (`display`, `sequencechannel` o.s.v.)
* **[./*] {string}** - Valfri egenskap som ska anges för platsen (d.v.s. `./jcr:title`, `./jcr:description`, `./foo, ./bar`). Den aktuella versionen tillåter ingen filtrering.

>[!NOTE]
>
>Alla kolumner som inte matchar villkoren ovan ignoreras. Om du till exempel har någon annan kolumn definierad i bladet (CSV/XLS) som inte är **path**, **template**, **title** eller **description** i filen, ignoreras dessa fält. **Projektimporteraren** validerar inte de ytterligare fälten för import av ditt projekt till ditt AEM Screens-projekt.

## Använda projektimporteraren {#using-project-importer}

I följande avsnitt beskrivs hur projektimporteraren används i ett AEM Screens-projekt.

>[!CAUTION]
>
>Begränsningar:
>
>* Andra filer än CSV-/XLS-/XLSX-tillägg stöds inte i den aktuella versionen.
>* Det finns ingen filtrering av egenskaperna för importerade filer och något som börjar med &quot;./&quot; importeras.
>

### Förutsättningar {#prerequisites}

* Skapa ett projekt med namnet **DemoProjectImport**

* Använd en CSV- eller Excel-exempelfil som du måste importera.

I demosyfte kan du ladda ned en Excel-fil från avsnittet nedan.

[Hämta fil](assets/minimal-file.xls)

### Importerar filen med minst obligatoriska fält {#importing-the-file-with-minimum-required-fields}

Följ stegen nedan för att importera en fil till en platsmapp med de obligatoriska fälten:

>[!NOTE]
>
>I följande exempel visas de minst fyra fälten som krävs för att importera projektet:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Navigera till ditt AEM Screens-projekt (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Klicka på projektet** DemoProjectImporter **>** Create **>** Import Locations** från sidofältet.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. Guiden **Importera** visas. Klicka på filen för projektet med platser eller klicka på filen (***minimum-file.xls***) som du hämtade från avsnittet *Förutsättningar*.

   När du har markerat filen klickar du på **Nästa**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Kontrollera innehållet i filen (platserna) i importguiden och klicka på **Importera**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Därför kan du nu visa alla platser som importerats till ditt projekt.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
