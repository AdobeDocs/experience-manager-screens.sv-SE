---
title: Inbäddade sekvenser
seo-title: Embedded Sequences
description: Följ den här sidan om du vill veta mer om inbäddade sekvenser för kanaler som gör att användaren kan lägga till komponenter i den överordnade kanalen och även återanvända innehållet från en annan kanal och bädda in det i den överordnade kanalen.
seo-description: Follow this page to learn about embedded sequences for channels that allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Inbäddade sekvenser {#embedded-sequences}

Använda ***Inbäddade sekvenser*** för kanaler tillåter användaren att lägga till komponenter i den överordnade kanalen och även att återanvända innehållet från en annan kanal och bädda in det i den överordnade kanalen.

## Lägga till inbäddade sekvenser {#adding-embedded-sequences}

Du kan lägga till följande komponenter i sekvenskanalen:

* Inbäddad sekvens
* Dynamisk inbäddad sekvens

>[!NOTE]
>
>Om du vill veta mer om hur du använder andra komponenter i ditt skärmsprojekt går du till [Lägga till komponenter i en kanal](adding-components-to-a-channel.md).

### Lägga till en inbäddad sekvens {#adding-an-embedded-sequence}

Du kan lägga till en inbäddad sekvens i kanalen. En inbäddad sekvens är en annan kanal som innehåller resurser som bilder eller videoklipp. Genom att lägga till en inbäddad sekvens kan användaren lägga till sekvensen i en kanal genom att ***Kanalsökväg***.

>[!NOTE]
>***Kanalsökväg*** definierar en explicit referens till kanalen.
>Mer information om *Kanalsökväg*, se [Kanaltilldelning](channel-assignment.md) i redigeringsskärmar.

Följ stegen nedan för att lägga till en inbäddad sekvens i kanalen:

1. Markera kanalen där du vill bädda in en sida. Till exempel: **Store** —> **Kanaler** —> **Inaktiv kanal**.

1. Klicka **Redigera** från åtgärdsfältet för att öppna kanalen i redigeringsläget.
1. Klicka på komponentikonen i det vänstra fältet för att lägga till den inbäddade sidan. Dra och släpp **Inbäddad sekvens** till redigeraren.
1. Dubbelklicka på **Inbäddad sekvens** om du vill lägga till kanalen i den ursprungliga sekvenskanalen.
1. Välj **Kanalsökväg** av kanalen.
1. Välj **Varaktighet (ms)** för den inbäddade kanalen i **Sekvens** -fliken. Som standard är längden inställd på **-1**, vilket innebär att inbäddad kanal körs helt. Om användaren anger en varaktighet kommer efterföljande att avbrytas (d.v.s. brytfrekvens) vid den angivna tiden.

1. Ange **Metered Playback Strategy** till **normal**.

Som standard är den inställd på **normal**. Ange värdet till **normal** (Spela upp alla objekt) betyder att efterföljande kommer att köras helt och hållet i varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enstaka objekt** (Spela upp ett enstaka objekt) och det skulle bara visa ett objekt i efterföljande körning (t.ex. det första objektet i den första slingan, det andra objektet i den andra slingan och så vidare).

>[!IMPORTANT]
>
>Du måste tilldela kanalen (används i inbäddad sekvens) till samma visning.
>
>Följ stegen nedan när du har lagt till en inbäddad sekvens i kanalen från de föregående stegen:
>
>1. Navigera till visningen och välj visningen från **Platser** mapp.
>1. Klicka på **Kontrollpanel** i åtgärdsfältet för att navigera till kontrollpanelen.
>1. Välj **+ Tilldela kanaler** från **TILLDELADE KANALER OCH SCHEMALAGDA PANELER** för att öppna **Dialogrutan Kanaltilldelning**.
>
>1. Markera banan för kanalen som du (används i inbäddad sekvens) i **Kanalsökväg**.
>1. Se till att **Prioritet** är lägre än huvudkanalen.
>
>1. Du får inte välja någon **Händelser som stöds**.
>1. Klicka **Spara** när allt är klart.

>


I följande exempel visas tillägget av en inbäddad sekvens (**Inaktiv kanal - Natt**) till en befintlig kanal (**Inaktiv kanal**).

![new2](assets/new2.gif)

### Lägga till en dynamisk inbäddad sekvens {#adding-a-dynamic-embedded-sequence}

Du kan lägga till en dynamisk inbäddad sekvens i kanalen. En dynamisk inbäddad sekvens liknar en inbäddad sekvens men gör det möjligt för användaren att följa en hierarki där ändringar/uppdateringar som görs i en kanal sprids till en annan i relation till den. Den följer hierarkin för överordnade och underordnade och innehåller även resurser som bilder eller videoklipp. Genom att lägga till en dynamisk sekvens kan användaren lägga till en kanal per kanalroll.

>[!NOTE]
>
>***Kanalroll*** definierar rollen Kanal som definierar visningssammanhanget.
>
>Mer information om *Kanalroll*, se [Kanaltilldelning](channel-assignment.md) i redigeringsskärmar.

Följ stegen nedan för att lägga till en inbäddad sekvens i kanalen:

1. Markera kanalen där du vill bädda in en dynamisk sekvens. Till exempel: **Store** —> **Kanaler** —> **Inaktiv kanal**.

1. Klicka **Redigera** från åtgärdsfältet för att öppna kanalen i redigeringsläget.
1. Klicka på komponentikonen i det vänstra fältet för att lägga till den dynamiska inbäddade sekvensen. Dra och släpp **Dynamisk** **Inbäddad sekvens**  till redigeraren.

1. Dubbelklicka på **Dynamisk** **Inbäddad sekvens** för att lägga till sidan i sekvenskanalen.

1. Ange **Kanaltilldelningsroll**.
1. Ange **Metered Playback Strategy** till **normal**. Som standard är den inställd på **normal**. Ange värdet till **normal** (Spela upp alla objekt) betyder att efterföljande kommer att köras helt och hållet i varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enstaka objekt** (Spela upp ett enstaka objekt) och det skulle bara visa ett objekt i efterföljande körning (t.ex. det första objektet i den första slingan, det andra objektet i den andra slingan och så vidare).

1. Välj **Varaktighet (ms)** in **Sekvens** -fliken för den inbäddade kanalen i sekvensen.

![senaste](assets/latest.gif)
