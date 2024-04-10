---
title: Användningsfall för övergångar mellan MultiZone och SingleZone
description: Följ den här sidan så att du kan lära dig mer om hur MultiZone till SingleZone-övergångar används.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Övergång mellan flera zoner och en zon {#multizone-to-singlezone-use-case}

## Använd fallbeskrivning {#use-case-description}

I det här avsnittet beskrivs ett exempel på hur du kan använda en flerzonslayoutkanal som växlar med en enzonslayoutkanal. Flerzonskanalen har sekvensbilder/videor och visar hur du kan ställa in projekt som växlar från flera zoner till en zon och omvänt.

### Förhandsvillkor {#preconditions}

Innan du börjar med det här användningsexemplet måste du förstå hur du gör:

* **[Skapa och hantera kanaler](managing-channels.md)**
* **[Skapa och hantera platser](managing-locations.md)**
* **[Skapa och hantera scheman](managing-schedules.md)**
* **[Enhetsregistrering](device-registration.md)**

### Primära aktörer {#primary-actors}

Innehållsförfattare

## Konfigurera projektet {#setting-up-the-project}

Följ stegen nedan för att konfigurera ett projekt:

1. Skapa ett AEM Screens-projekt med namnet **TakeoverLoop**, vilket visas nedan.

   ![resurs](assets/mz-to-sz1.png)


1. **Skapa en skärmkanal för flera zoner**

   1. Välj **Kanaler** mapp och klicka på **Skapa** i åtgärdsfältet och öppnar guiden så att du kan skapa en kanal.
   1. Välj **Vänster-L-fält, delad skärmkanal** från guiden och skapa kanalen som **MultiZoneLayout**.
   1. Lägg till innehåll i kanalen. Dra och släpp resurserna till varje zon. I följande exempel visas en **MultiZoneLayout** kanal som innehåller en video, en bild och en textbanderoll (i en inbäddad sekvens), vilket visas nedan.

   ![resurs](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en layout för flera zoner i din kanal finns i [Layout med flera zoner](multi-zone-layout-aem-screens.md).


1. Skapa en annan kanal med namnet som **TakeoverChannel** till **Kanaler** mapp.

   ![resurs](assets/mz-to-sz3.png)

1. Klicka **Redigera** från åtgärdsfältet så att du kan lägga till innehåll i den här kanalen. Lägg till en **Kanal** och en bildresurs som du vill växla till för den här kanalen, vilket visas i bilden nedan:

   ![resurs](assets/mz-to-sz4.png)

1. Öppna inställningarna för kanalkomponenten och peka på den **MultiZoneLayout** kanal som du skapade i *steg 2*.

   ![resurs](assets/mz-to-sz5.png)

1. Ange varaktighet från **Sekvens** fält till **10000 millisekunder**.

   ![resurs](assets/mz-to-sz6.png)

1. Öppna på liknande sätt inställningarna för bilden (resursen som du lade till) och ange dess varaktighet från **Sekvens** fält till **3 000 millisekunder**.

   ![resurs](assets/mz-to-sz7.png)

## Kontrollera förhandsvisningen {#checking-the-preview}

Du kan visa önskade utdata från spelaren eller bara genom att välja **Förhandsgranska** från redigeraren.

Utdata visar hur en flerzonslayout spelas upp för *10000 millisekunder* och växlar sedan till layout med en zon som har uppspelningstiden *3 000 millisekunder* och växlar sedan tillbaka till flerzonslayouten.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Du kan anpassa din kanalövergång (från flerzonslayout till enzonslayout eller omvänt) efter behov.
