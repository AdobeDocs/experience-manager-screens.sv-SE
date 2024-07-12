---
title: Inbäddade sekvenser
description: Lär dig mer om inbäddade sekvenser för kanaler där du kan lägga till komponenter i den överordnade kanalen. Eller återanvänd innehållet från en annan kanal och bädda in det i den överordnade kanalen.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: cdfaee19-15d9-4bcb-bc85-0b43c59d88d2
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Inbäddade sekvenser {#embedded-sequences}

Om du använder ***Inbäddade sekvenser*** för kanaler kan en användare lägga till komponenter i den överordnade kanalen och även återanvända innehållet från en annan kanal och bädda in det i den överordnade kanalen.

## Lägga till inbäddade sekvenser {#adding-embedded-sequences}

Du kan lägga till följande komponenter i sekvenskanalen:

* Inbäddad sekvens
* Dynamisk inbyggd sekvens

>[!NOTE]
>
>Mer information om hur du använder andra komponenter i ditt Screens-projekt finns i [Lägga till komponenter i en kanal](adding-components-to-a-channel.md).

### Lägga till en inbäddad sekvens {#adding-an-embedded-sequence}

Du kan lägga till en inbäddad sekvens i kanalen. En inbäddad sekvens är en annan kanal som innehåller resurser som bilder eller videor. Genom att lägga till en inbäddad sekvens kan användaren lägga till sekvensen i en kanal med ***Kanalsökväg***.

>[!NOTE]
>***Kanalsökvägen*** definierar en explicit referens till kanalen.
>Mer information om *Kanalsökväg* finns i [Kanaltilldelning](channel-assignment.md) i Skapa Screens.

Följ stegen nedan för att lägga till en inbäddad sekvens i kanalen:

1. Klicka på den kanal där du vill bädda in en sida. Exempel: **`We.Retail`In-Store** > **Kanaler** > **Inaktiv kanal**.

1. Klicka på **Redigera** i åtgärdsfältet.
1. Klicka på komponentikonen i det vänstra fältet i redigeringsläget så att du kan lägga till den inbäddade sidan. Dra och släpp den **inbäddade sekvensen** till redigeraren.
1. Dubbelklicka på komponenten **Inbäddad sekvens** så att du kan lägga till kanalen i den ursprungliga sekvenskanalen.
1. Klicka på kanalens **kanalsökväg**.
1. Klicka på **Varaktighet (millisekunder)** för den inbäddade kanalen på fliken **Sekvens**. Som standard är längden inställd på **-1**, vilket innebär att den inbäddade kanalen körs helt. Om användaren anger en varaktighet avbryts efterföljande (d.v.s. den avbryts) vid den angivna tidpunkten.

1. Ställ in **Metered Playback Strategy** på **normal**.

Som standard är den inställd på **normal**. Om du anger värdet till **normal** (Spela upp alla objekt) innebär det att efterföljande körs helt på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enskilt objekt**. Det värdet visar bara ett objekt i efterföljande körningar. Det första objektet i den första slingan och det andra objektet i den andra slingan.

>[!IMPORTANT]
>
>Tilldela kanalen som används i den inbäddade sekvensen till samma skärm.
>
>Följ stegen nedan när du har lagt till en inbäddad sekvens i kanalen från de föregående stegen:
>
>1. Navigera till visningen och klicka på visningen i mappen **Platser** .
>1. Klicka på **Instrumentpanel** i åtgärdsfältet.
>1. Klicka på **+ Tilldela kanaler** på kontrollpanelen **TILLDELADE KANALER &amp; SCHEMALAGDA PANELER** så att du kan öppna dialogrutan **Kanaltilldelning**.
>
>1. Klicka på sökvägen till kanalen som du använde i den inbäddade sekvensen i **Kanalsökväg**.
>1. Kontrollera att **Prioritet** är lägre än huvudkanalen.
>
>1. Klicka inte på några **händelser som stöds**.
>1. Klicka på **Spara** när du är klar.
>

I följande exempel visas tillägget av en inbäddad sekvens (**Inaktiv kanal - Natt**) i en befintlig kanal (**Inaktiv kanal**).

![new2](assets/new2.gif)

### Lägga till en dynamisk inbäddad sekvens {#adding-a-dynamic-embedded-sequence}

Du kan lägga till en dynamisk inbäddad sekvens i kanalen. En dynamisk inbäddad sekvens liknar en inbäddad sekvens men gör det möjligt för användaren att följa en hierarki där ändringar/uppdateringar som görs i en kanal sprids till en annan i relation till den. Den följer en hierarki med överordnade och underordnade objekt och innehåller även resurser som bilder eller videor. Genom att lägga till en dynamisk sekvens kan användaren lägga till en kanal efter kanalroll.

>[!NOTE]
>
>***Kanalrollen*** definierar visningssammanhanget.
>
>Mer information om *Kanalrollen* finns i [Kanaltilldelning](channel-assignment.md) i Skapa Screens.

Följ stegen nedan för att lägga till en inbäddad sekvens i kanalen:

1. Klicka på den kanal där du vill bädda in en dynamisk sekvens. Exempel: **`We.Retail`In-Store** > **Kanaler** > **Inaktiv kanal**.

1. Klicka på **Redigera** i åtgärdsfältet.
1. Klicka på komponentikonen i det vänstra fältet i redigeringsläget så att du kan lägga till den dynamiska inbäddade sekvensen. Dra och släpp den **dynamiska** **inbäddade sekvensen** till redigeraren.

1. Dubbelklicka på komponenten **Dynamisk** **Inbäddad sekvens** så att du kan lägga till sidan i sekvenskanalen.

1. Ange **kanaltilldelningsrollen**.
1. Ställ in **Metered Playback Strategy** på **normal**. Som standard är den inställd på **normal**. Om du anger värdet till **normal** (Spela upp alla objekt) innebär det att efterföljande körs helt på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är **Spela upp ett enskilt objekt**. Det värdet visar bara ett objekt i efterföljande körningar. Det första objektet i den första slingan och det andra objektet i den andra slingan.

1. Klicka på **Varaktighet (millisekunder)** på fliken **Sekvens** för den inbäddade kanalen i sekvensen.

![senaste](assets/latest.gif)
