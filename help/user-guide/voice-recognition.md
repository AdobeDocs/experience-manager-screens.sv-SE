---
title: Röstigenkänning i AEM Screens
description: Sidan beskriver röstigenkänningsfunktionen i AEM Screens.
feature: Redigeringsskärmar
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 1%

---

# Röstigenkänning i AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Viktig sekretessinformation**
>
>När du använder funktionen för röstigenkänning ska du följa alla tillämpliga juridiska och etiska riktlinjer för din region (inklusive, men inte begränsat till, att ge slutanvändarna ett synligt meddelande om att spelaren använder röstigenkänning). Adobe Inc., tar inte emot, lagrar eller bearbetar någon röstrelaterad information. AEM Screens-spelarna använder det standardwebbtal-API som är inbyggt i webbläsarmotorn. Bakom kulisserna skickar denna API en vågform av ditt tal till Googles servrar för konvertering från tal till text och den här texten matchas av spelaren mot konfigurerade nyckelord.
>
>Mer information finns i [Google Privacy White-paper om webbtal-API](https://www.google.com/chrome/privacy/whitepaper.html#speech).


Röstigenkänningsfunktionen tillåter innehållsändringar i en AEM Screens-kanal som styrs av röstinteraktion.

En innehållsförfattare kan konfigurera en visning som röstaktiverad. Syftet med den här funktionen är att ge kunderna möjlighet att använda tal som sätt att interagera med sina bildskärmar. Exempel på liknande användningsområden är att hitta produktrekommendationer i butiker, beställa menyalternativ på materier och restauranger. Den här funktionen ökar tillgängligheten för användarna och kan förbättra kundupplevelsen avsevärt.

>[!NOTE]
>Spelarens maskinvara måste stödja röstindata, t.ex. en mikrofon.

## Implementera röstigenkänning {#implementing}

>[!IMPORTANT]
> Röstigenkänningsfunktionen är bara tillgänglig i Chrome OS- och Windows-spelare.

Om du vill implementera röstigenkänning i ditt AEM Screens-projekt måste du aktivera röstigenkänningen för bildskärmen och associera varje kanal med en unik tagg för att utlösa en kanalövergång.

I följande avsnitt beskrivs hur du kan aktivera och använda funktionen för röstigenkänning i ett AEM Screens-projekt.

## Visa innehåll i helskärmsläge eller kanalbyte för delad skärm {#sequence-channel}

Innan du använder funktionen för röstigenkänning bör du kontrollera att du har ett projekt och en kanal med innehåll som har konfigurerats för ditt projekt.

1. I följande exempel visas ett demonstrationsprojekt med namnet **VoiceDemo** och tre sekvenskanaler **Main**, **ColdDrinks** och **HotDrinks**, vilket visas i bilden nedan.

   ![bild](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en kanal eller lägger till innehåll i en kanal finns i [Skapa och hantera kanaler](/help/user-guide/managing-channels.md)

   Eller

   Du kan skapa tre sekvenskanaler **Main**, **ColdDrinks** och **HotDrinks** och ytterligare en 1x2 Split Screens channel **SplitScreen** enligt bilden nedan.

   ![bild](assets/voice-recognition/vr-emb-1.png)

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren och lägga till innehåll (bilder/videor) efter dina behov. Lägg på samma sätt till innehåll i både **ColdDrinks** och i **HotDrinks**-kanalen.

   Kanalerna innehåller nu resurser (bilder), vilket visas i figurerna nedan.

   **Huvud**:

   ![bild](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![bild](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![bild](assets/voice-recognition/vr-2.png)

   Om du har lagt till kanalen Dela skärmar i ditt projekt går du till **SplitScreen** och drar och släpper två inbäddade sekvenser och lägger till banor i både **ColdDrinks**- och **HotDrinks**-kanalen enligt bilden nedan.
   ![bild](assets/voice-recognition/vr-emb-6.png)


### Konfigurera taggar för kanaler {#setting-tags}

När du har lagt till innehåll i kanalerna måste du navigera till var och en av kanalerna och lägga till lämpliga taggar som skulle utlösa röstigenkänningen.

Följ stegen nedan för att lägga till taggar i din kanal:

1. Navigera till varje kanal och lägg till innehåll. Navigera till **VoiceDemo** —> **Kanaler** —> **Main** och markera kanalen.

1. Klicka på **Egenskaper** i åtgärdsfältet.

   ![bild](assets/voice-recognition/vr-5.png)

1. Navigera till fliken **Grunderna** och markera en tagg som redan finns i fältet **Taggar** eller skapa en ny.

   Du kan antingen skapa en ny tagg genom att skriva in ett nytt namn för taggen och trycka på `return` enligt bilden nedan:

   ![bild](assets/voice-recognition/vr-6.png)

   Eller

   Du kan också skapa taggar från AEM i förväg för ditt projekt och sedan markera dem. När du har följt stegen som beskrivs i [Skapa taggar](#creating-tags) kan du markera taggen från platsen och lägga till den i kanalen, vilket visas i bilden nedan:

   ![bild](assets/voice-recognition/vr-tag1.png)

1. Lägg på liknande sätt till taggen **hot** i kanalen **HotDrinks**.

1. Om du använder en kanal för delade skärmar lägger du till båda taggarna (**hot** och **kall**) i kanalegenskaperna för **SplitScreen**, vilket visas i bilden nedan.

   ![bild](assets/voice-recognition/vr-emb-7.png)

1. Klicka på **Spara och stäng** när du är klar.


### Skapa taggar {#creating-tags}

Skapa taggar genom att följa stegen nedan:

1. Navigera till AEM.

1. Klicka på verktygsikonen —> **Taggning**.
   ![bild](assets/voice-recognition/vr-7.png)

1. Klicka på **Skapa** —> **Skapa namnområde**.
   ![bild](assets/voice-recognition/vr-tag3.png)

1. Ange namnet på ditt projekt, till exempel **VoiceDemo** och klicka på **Skapa**.

1. Välj projektet **VoiceDemo** och klicka på **Skapa tagg** i åtgärdsfältet.
   ![bild](assets/voice-recognition/vr-tag4.png)

1. Ange namnet på taggen och klicka på **Skicka**.
   ![bild](assets/voice-recognition/vr-tag5.png)

Nu kan du använda dessa taggar i ditt AEM Screens-projekt.

### Tilldela kanal till en bildskärm och aktivera röstigenkänning {#channel-assignment}

1. Skapa en visning i mappen **Platser**, vilket visas i bilden nedan.

   ![bild](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. Tilldela kanalerna **Main**, **ColdDrinks** och **HotDrinks** till din **LobbyDisplay**. Om du dessutom använder **SplitScreen**-kanalen för ditt projekt måste du tilldela den till skärmen.

   >[!NOTE]
   >Om du har skapat en kanal för delad skärm tilldelar du kanalen **SplitScreen** till visningen.

1. Ange följande egenskaper för varje kanal när du tilldelar kanalen.

   | **Kanalnamn** | **Prioritet** | **Händelser som stöds** |
   |---|---|---|
   | Huvud | 2 | Inledande inläsning, inaktiv skärm, timer |
   | HotDrinks | 1 | Användarinteraktion |
   | ColdDrinks | 3 | Användarinteraktion |
   | SplitScreen | 1 | Användarinteraktion |

   >[!NOTE]
   >
   >Mer information om hur du tilldelar en kanal till en skärm finns i [Skapa och hantera skärmar](/help/user-guide/managing-displays.md).

1. När du har tilldelat kanaler till en visning går du till **LobbyDisplay** och väljer visningen. Välj **Egenskaper** i åtgärdsfältet.

1. Gå till fliken **Visa** och aktivera **Röstaktiverat** under **Innehåll**.

   ![bild](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Det är obligatoriskt att aktivera funktionen för röstigenkänning från skärmen.

### Visa innehållet i Chrome Player {#viewing-content}

När de föregående stegen är slutförda kan du registrera din fönsterenhet för att visa utdata.

>[!NOTE]
>Läs [Device Registration](device-registration.md) om du vill veta hur du registrerar en enhet i en AEM Screens-spelare.

**Önskad utdata för sekvenskanal**

Huvudkanalen **Huvudkanalen** spelar upp innehållet, men när du använder ord med nyckelord **hot**, som *Jag vill ha ett varmt*, börjar kanalen spela upp innehållet i **HotDrinks**-kanalen.

Om du använder ord med ett nyckelord **kallt**, t.ex. *Jag vill ha något kallt*, börjar kanalen spela upp innehållet i kanalen **ColdDrinks**.

**Önskad utdata för kanalen för delade skärmar**

Huvudkanalen i **Main** spelar upp innehållet, men när du använder ord med nyckelord **hot** och **kall** tillsammans, t.ex. *vill jag se menyn för varma och kalla drycker* börjar kanalen spela upp innehållet i **SplitScreen** . Om du säger *tillbaka till huvudmenyn* växlar den tillbaka till huvudkanalen.
