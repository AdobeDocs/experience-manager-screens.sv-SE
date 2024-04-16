---
title: Inbäddade sekvenser
description: Lär dig mer om inbäddade sekvenser för kanaler där du kan lägga till komponenter i den överordnade kanalen och även återanvända innehållet från en annan kanal och bädda in det i den överordnade kanalen.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# Inbäddade sekvenser {#embedded-sequences}

Använda ***Inbäddade sekvenser*** för kanaler tillåter användaren att lägga till komponenter i den överordnade kanalen och även att återanvända innehållet från en annan kanal och bädda in det i den överordnade kanalen.

## Lägga till inbäddade sekvenser {#adding-embedded-sequences}

Du kan lägga till följande komponenter i sekvenskanalen:

* Inbäddad sekvens
* Dynamisk inbyggd sekvens

>[!NOTE]
>
>Om du vill veta mer om hur du använder andra komponenter i ditt skärmsprojekt går du till [Lägga till komponenter i en kanal](adding-components-to-a-channel.md).

### Lägga till en inbäddad sekvens {#adding-an-embedded-sequence}

Du kan lägga till en inbäddad sekvens i kanalen. En inbäddad sekvens är en annan kanal som innehåller resurser som bilder eller videor. Genom att lägga till en inbäddad sekvens kan användaren lägga till sekvensen i en kanal genom att ***Kanalsökväg***.

>[!NOTE]
>***Kanalsökväg*** definierar en explicit referens till kanalen.
>Mer information om *Kanalsökväg*, se [Kanaltilldelning](channel-assignment.md) i redigeringsskärmar.

Följ stegen nedan för att lägga till en inbäddad sekvens i kanalen:

1. Klicka på den kanal där du vill bädda in en sida. Till exempel: **`We.Retail`I butik** > **Kanaler** > **Inaktiv kanal**.

1. Klicka **Redigera** i åtgärdsfältet.
1. Klicka på komponentikonen i det vänstra fältet i redigeringsläget så att du kan lägga till den inbäddade sidan. Dra och släpp **Inbäddad sekvens** till redigeraren.
1. Dubbelklicka på **Inbäddad sekvens** så att du kan lägga till kanalen i den ursprungliga sekvenskanalen.
1. Klicka på **Kanalsökväg** av kanalen.
1. Klicka på **Varaktighet (millisekunder)** för den inbäddade kanalen i **Sekvens** -fliken. Som standard är längden inställd på **-1**, vilket innebär att inbäddad kanal körs helt. Om användaren anger en varaktighet avbryts efterföljande (d.v.s. den avbryts) vid den angivna tidpunkten.

1. Ange **Metered Playback Strategy** till **normal**.

Som standard är den inställd på **normal**. Ange värdet till **normal** (Spela upp alla objekt) innebär att efterföljande körs helt och hållet på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enstaka objekt**. Det värdet visar bara ett objekt i efterföljande körningar. Det första objektet i den första slingan och det andra objektet i den andra slingan.

>[!IMPORTANT]
>
>Tilldela kanalen som används i inbäddad sekvens till samma skärm.
>
>Följ stegen nedan när du har lagt till en inbäddad sekvens i kanalen från de föregående stegen:
>
>1. Navigera till visningen och klicka på visningen från **Platser** mapp.
>1. Klicka **Kontrollpanel** i åtgärdsfältet.
>1. Klicka på **+ Tilldela kanaler** från **TILLDELADE KANALER OCH SCHEMALAGDA PANELER** så att du kan öppna **Dialogrutan Kanaltilldelning**.
>
>1. Klicka på banan för kanalen som du (används i inbäddad sekvens) i **Kanalsökväg**.
>1. Se till att **Prioritet** är lägre än huvudkanalen.
>
>1. Klicka inte på någon **Händelser som stöds**.
>1. Klicka **Spara** när det är klart.
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

1. Klicka på den kanal där du vill bädda in en dynamisk sekvens. Till exempel: **`We.Retail`I butik** > **Kanaler** > **Inaktiv kanal**.

1. Klicka **Redigera** i åtgärdsfältet.
1. Klicka på komponentikonen i det vänstra fältet i redigeringsläget så att du kan lägga till den dynamiska inbäddade sekvensen. Dra och släpp **Dynamisk** **Inbäddad sekvens** till redigeraren.

1. Dubbelklicka på **Dynamisk** **Inbäddad sekvens** så att du kan lägga till sidan i sekvenskanalen.

1. Ange **Kanaltilldelningsroll**.
1. Ange **Metered Playback Strategy** till **normal**. Som standard är den inställd på **normal**. Ange värdet till **normal** (Spela upp alla objekt) innebär att efterföljande körs helt och hållet på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enstaka objekt**. Det värdet visar bara ett objekt i efterföljande körningar. Det första objektet i den första slingan och det andra objektet i den andra slingan.

1. Klicka på **Varaktighet (millisekunder)** in **Sekvens** -fliken för den inbäddade kanalen i sekvensen.

![senaste](assets/latest.gif)
