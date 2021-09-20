---
title: Stöd för miniatyrbilder för videofilmer i AEM Screens
description: På den här sidan beskrivs hur du lägger till stöd för miniatyrbilder för videoklipp på skärmar.
index: false
source-git-commit: 07b5b6159b09c0c1301a5e782dfe959d0b83a7d2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Stöd för miniatyrbilder för videoklipp {#thumbnail-support-videos}

## Introduktion {#introduction}

Innehållsförfattare kan definiera en miniatyrbild för videoklipp så att bilden kan användas som platshållare och testa uppspelning och målgruppsanpassning av innehållet medan videon färdigställs av rätt team. Bilden kan också användas om videouppspelningen misslyckas.

Genom att lägga till stöd för en miniatyrbild i videokomponenten kan kunden lägga till en giltig komponent i kanalen, med faktiskt innehåll, och utföra eventuella målinriktningskonfigurationer innan videon levereras.

>[!NOTE]
>Miniatyrbilden spelas upp om videomponenten är inställd om videouppspelningen misslyckas i spelaren. På så sätt kan du leverera önskat meddelande till målgruppen (genom att spela upp innehåll) i stället för att helt hoppa över det.

Med stöd för miniatyrbilder kan du:

* Förbered en kanalupplevelse när videoklippen inte är klara än, eller när du inte nödvändigtvis vill testa en stor resurshämtning på spelarna

* Ange en reservmekanism om det skulle uppstå uppspelningsproblem på enheten.

## Använda miniatyrer i videoklipp {#using-thumbnails}

Följ stegen nedan för att använda miniatyrbilden i videoklipp:

1. Navigera till en befintlig skärmkanal eller skapa en ny kanal.

1. Markera kanalen och klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.

1. Lägg till eller redigera en befintlig videokomponent enligt bilden nedan.

1. Markera videon och klicka på ikonen *skiftnyckel* för att öppna videoegenskaperna.

1. Dialogrutan **Video** öppnas där du kan visa släppzonen **Miniatyrbild**.

1. Dra och släpp en bild från resursväljaren till släppzonen **Miniatyrbild** och klicka på **Klar**.

1. Klicka på **Förhandsgranska**.

1. Om en video är inställd på komponenten spelas videon upp. Om inte, och miniatyrbilden är inställd, spelas miniatyrbilden upp. Annars betraktas komponenten som inte konfigurerad och kommer att hoppas över.

## Användningsexempel som stöds vid användning av miniatyrbilder i videoklipp {#understand-use-case}

Miniatyrbilder i videoklipp har stöd för följande användningsområden:

* En videokomponent utan inställningar hoppas över.

* En videokomponent som bara innehåller en miniatyrbilduppsättning spelar upp miniatyrbilden.

* En videokomponent med både videon (om videon har rätt återgivning) och en miniatyrbildsuppsättning spelar upp videon.

* En videokomponent med videouppsättningen spelar upp miniatyrbilden om det uppstår ett uppspelningsfel, eller hoppar bara till nästa objekt om miniatyrbilden inte är konfigurerad.
