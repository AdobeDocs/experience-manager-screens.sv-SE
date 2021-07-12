---
title: Användningsfall för övergångar mellan MultiZone och SingleZone
description: Följ den här sidan om du vill veta mer om hur MultiZone till SingleZone-övergångar används.
seo-description: MultiZone till SingleZone-övergångar - exempel.
contentOwner: Jyotika Syal
feature: Redigeringsskärmar
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Övergång mellan flera zoner och en zon {#multizone-to-singlezone-use-case}


## Använd fallbeskrivning {#use-case-description}

I det här avsnittet beskrivs ett exempel på hur du kan använda ett exempel som betonar hur du ställer in en layoutkanal för flera zoner som växlar med en layoutkanal för en zon. Flerzonskanalen har sekvensbilder/videor och visar hur du kan ställa in projekt som växlar från flera zoner till en zon och vice versa.

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

1. Skapa ett AEM Screens-projekt med namnet **TakeoverLoop**, enligt nedan.

   ![resurs](assets/mz-to-sz1.png)


1. **Skapa en skärmkanal för flera zoner**

   1. Välj mappen **Kanaler** och klicka på **Skapa** i åtgärdsfältet för att öppna guiden och skapa en kanal.
   1. Välj **Delad skärmkanal för vänster-L-fält** i guiden och skapa kanalen **MultiZoneLayout**.
   1. Lägg till innehåll i kanalen. Dra och släpp resurserna till var och en av zonerna. I följande exempel visas en **MultiZoneLayout**-kanal som består av en video, en bild och en textbanderoll (i en inbäddad sekvens), vilket visas nedan.

   ![resurs](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en layout för flera zoner i din kanal finns i [Layout för flera zoner](multi-zone-layout-aem-screens.md).


1. Skapa en annan kanal med namnet **TakeoverChannel** till mappen **Kanaler**.

   ![resurs](assets/mz-to-sz3.png)

1. Klicka på **Redigera** i åtgärdsfältet för att lägga till innehåll i den här kanalen. Lägg till en **Channel**-komponent och en bildresurs som du vill växla till i den här kanalen enligt bilden nedan:

   ![resurs](assets/mz-to-sz4.png)

1. Öppna inställningarna för Channel-komponenten och peka på den **MultiZoneLayout**-kanal som du skapade i *steg 2*.

   ![resurs](assets/mz-to-sz5.png)

1. Ange längden från fältet **Sekvens** till **10000 ms**.

   ![resurs](assets/mz-to-sz6.png)

1. Öppna på samma sätt inställningarna för bilden (resursen som du lade till) och ange dess varaktighet från fältet **Sequence** till **3000 ms**.

   ![resurs](assets/mz-to-sz7.png)

## Kontrollera förhandsvisningen {#checking-the-preview}

Du kan visa önskade utdata från spelaren eller bara genom att klicka på **Förhandsgranska** i redigeraren.

Utdata visar hur en layout med flera zoner spelas upp för *10000 ms* och växlar sedan till layout med en zon som har uppspelningstiden *3000 ms* och växlar sedan tillbaka till layouten med flera zoner.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Du kan anpassa din kanalövergång (från layout med flera zoner till layout med en zon eller tvärtom) efter dina behov.
