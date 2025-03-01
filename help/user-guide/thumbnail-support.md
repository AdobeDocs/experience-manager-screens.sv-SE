---
title: Stöd för miniatyrbilder för videofilmer i AEM Screens
description: Lär dig hur du lägger till stöd för miniatyrbilder för videoklipp i AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 1%

---

# Stöd för miniatyrbilder för videor {#thumbnail-support-videos}

## Introduktion {#introduction}

En innehållsförfattare kan definiera en miniatyrbild för videoklipp så att bilden används som platshållare. Programmet kan testa uppspelning och målinriktning av innehåll på rätt sätt, medan rätt team slutför själva videon. Bilden kan också användas om videouppspelningen misslyckas.

Genom att lägga till stöd för en miniatyrbild i videokomponenten kan kunden lägga till en giltig komponent i kanalen, med faktiskt innehåll, och utföra eventuella målinriktningskonfigurationer innan videon levereras.

>[!NOTE]
>Miniatyrbilden spelas upp om den har angetts för videokomponenten om det inte går att spela upp videon i spelaren. Med denna reservlösning kan du leverera önskat meddelande till målgruppen (genom att spela upp innehåll) i stället för att helt hoppa över det.

Med stöd för miniatyrbilder kan du:

* Förbered en kanalupplevelse när videoklippen inte är klara än, eller när du inte nödvändigtvis vill testa en stor resurshämtning på spelarna

* Ange en reservmekanism om det skulle uppstå uppspelningsproblem på enheten.

## Använda miniatyrer i videoklipp {#using-thumbnails}

Följ stegen nedan för att använda en miniatyrbild i videoklipp:

1. Navigera till en befintlig AEM Screens-kanal eller skapa en kanal.

1. Klicka på kanalen och klicka på **Redigera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Lägg till eller redigera en befintlig videokomponent enligt bilden nedan.

   ![bild](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Klicka på videon och klicka på ikonen *skiftnyckel* .

   ![bild](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. Dialogrutan **Video** öppnas där du kan visa släppzonen **Miniatyrbild**.

   ![bild](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Dra och släpp en bild från resursväljaren till släppzonen **Miniatyrbild** och klicka på **Klar**.

   ![bild](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Klicka på **Förhandsgranska**.

1. Om en video är inställd på komponenten spelas videon upp. Om inte, och miniatyrbilden är inställd, spelas miniatyrbilden upp. Annars betraktas komponenten som inte konfigurerad och hoppas över.

## Användningsexempel som stöds vid användning av miniatyrbilder i videoklipp {#understand-use-case}

Miniatyrbilder i videoklipp har stöd för följande användningsområden:

* En videokomponent utan några inställningar hoppas över.

* En videokomponent med bara miniatyrbildsuppsättningen spelar upp miniatyrbilden.

* En videokomponent med både videon (om videon har rätt återgivning) och miniatyruppsättningen spelar upp videon.

* En videokomponent med videouppsättningen spelar upp miniatyrbilden, om det finns ett uppspelningsfel, eller hoppar till nästa objekt om miniatyrbilden inte är konfigurerad.
