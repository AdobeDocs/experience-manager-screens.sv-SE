---
title: Kanaltilldelning - senaste FP
description: Läs mer om kanaltilldelning och Dag-delning.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 346eec9a-e291-4b0d-9686-fee1d5a0e7dd
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# Kanaltilldelning {#channel-assignment}

>[!IMPORTANT]
>
>I det här avsnittet beskrivs kanaltilldelning och kanalplanering för AEM 6.5.5 Screens Feature Pack och senare.

När du har konfigurerat en visning tilldelar du en kanal till en visning för att visa innehållet.

På den här sidan visas hur du tilldelar en kanal till visningen, hur du förstår kanalegenskaper och DayParting.

>[!NOTE]
>
>Du kan tilldela flera kanaler till en skärm.


## Tilldela en kanal {#assign-a-channel-new-release}

Följ nedanstående avsnitt för att skapa ett AEM Screens-projekt och tilldela en kanal till en skärm.

### Skapa ett AEM Screens-projekt och kanaler {#creating-project}

Följ stegen nedan för att konfigurera ett projekt och en kanal:

1. Skapa ett AEM Screens-projekt med namnet **DemoScreens**.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Mer information om hur du skapar ett AEM Screens-projekt finns i [Skapa och hantera projekt](creating-a-screens-project.md).

1. Skapa en sekvenskanal med namnet **Cafeteria** i mappen **Kanaler**.

1. Klicka på kanalen och sedan på **Redigera** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Kanalen **Cafeteria** visar nu följande bilder:

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Skapa en plats med namnet **SanJose** och en visning som **Lobby**.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Tilldela kanal till en skärm {#assigning-channel-to-display}

När projektkonfigurationen är klar tilldelar du kanalen till en visning för att visa innehållet.

1. Navigera till önskad visning, till exempel **DemoScreens** > **Platser** > **SanJose** > **Lobby**.

1. Klicka på **Tilldela kanal** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Eller

   Klicka på **Instrumentpanel** i åtgärdsfältet och klicka på **+Tilldela kanal** på panelen **TILLDELADE KANALER OCH SCHEMALÄGG** .

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Dialogrutan **Kanaltilldelning** öppnas.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Från alternativet **Inställningar** kan du välja kanalen **efter sökväg** eller **efter namn**, ange **kanalrollen**, **prioritet**, **händelser som stöds** och **avbrottsmetoder**. Du kan även aktivera attributverktygstipset i den här dialogrutan.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >
   >Mer information om egenskaper för kanaltilldelning finns i avsnittet [Kanalegenskaper](#channel-properties).

1. Klicka på **Aktiveringsfönstret** och **Återkommande schema** i alternativet **Schema**.
   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >
   >Mer information om egenskaper för kanaltilldelning finns i avsnittet [Kanalegenskaper](#channel-properties).

1. Klicka på **Spara** när du har konfigurerat inställningarna.

### Visa innehåll i Chrome Player {#viewing-content-output}

I det här exemplet visas utdata för en Chrome Player. När du har tilldelat kanalen till din skärm registrerar du enheten till en spelare.

Mer information om hur du registrerar en enhet i en AEM Screens Player finns i [Enhetsregistrering](device-registration.md).

Du kan visa följande utdata när du väljer spelare:

![new1](assets/channel-assignment/channel-assign-output.gif)

## Tidslinjevy {#timeline-view}

När du har tilldelat en kanal till en visning och konfigurerat ett upprepningsschema, kan du visa tidslinjen från panelen **TILLDELADE KANALER &amp; SCHEMALÄGG** .

Följ stegen nedan för att navigera till tidslinjevyn:

1. Navigera till önskad visning, till exempel **DemoScreens** > **Platser** > **SanJose** > **Lobby**.

1. Klicka på **Tilldela kanal** i åtgärdsfältet.

   Eller

   Klicka på **Instrumentpanel** och klicka på **Tidslinje** på panelen **TILLDELADE KANALER OCH SCHEMALÄGG**.

   ![bild](/help/user-guide/assets/channel-assignment/timeline-1.png)

## Förstå kanalegenskaper från dialogrutan Kanaltilldelning {#channel-properties}

Följande egenskaper ställs in från alternativet **Inställningar** i dialogrutan **Kanaltilldelning** .

![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### Välj en kanal {#select-channel}

Om du väljer en kanal kan du ange en referens till den önskade kanalen, antingen efter kanalnamn eller efter kanalsökväg.

* **Efter sökväg** - Du anger en explicit referens med kanalens absoluta sökväg.
* **Efter namn** - Du anger namnet på kanalen som tolkas till en faktisk kanal efter kontext. Med den här funktionen kan du skapa en lokal version av en kanal så att du dynamiskt kan matcha platsspecifikt innehåll. En kanal med namnet *erbjudanden för dagen*, där det faktiska innehållet skulle vara annorlunda i två städer, men du har fortfarande den tillräkneliga kanalrollen på alla skärmar.

### Kanalroll {#role-channel}

Kanalrollen definierar visningssammanhanget. Olika åtgärder har rollen som mål. Det är oberoende av den faktiska kanal som fullgör rollen.

### Prioritet {#priority-channel}

Prioritet används för att ordna tilldelningarna om flera matchar uppspelningsvillkoren. Den som har det högsta värdet har alltid företräde framför de lägre värdena. Om det till exempel finns två kanaler A och B. A har prioriteten 1 och B har prioriteten 2, och sedan visas kanal B eftersom den har högre prioritet än A.

>[!NOTE]
>
>Prioriteten för en kanal anges som ett tal (1 för minimum) i dialogrutan **Kanaltilldelning** enligt ovan. Dessutom sorteras de tilldelade kanalerna baserat på fallande prioritet.

### Händelser som stöds {#supported-events-channel}

* **Inledande inläsning** - Läser in kanalen när spelaren startas. Den kan tilldelas flera kanaler med ett schema.
* **Inaktiv skärm** - läses in när skärmen är inaktiv. Den kan tilldelas flera kanaler med ett schema.
* **Timer** - Måste anges när ett schema anges.
* **Användarinteraktion** - Spelaren växlar till den angivna kanalen om det finns en användarinteraktion på skärmen (pekning) i en inaktiv kanal och läses in när skärmen ändras.

### Avbrottsmetod {#interruption-method-channel}

>[!IMPORTANT]
> Det här alternativet är endast tillgängligt med <!--AEM 6.4 Feature Pack 8 or-->AEM 6.5 Feature Pack 4.

Som innehållsförfattare kan du ange när en kanal ska avbrytas. På så sätt kan du välja att ta bort icke-kritiskt innehåll. Men det ger också möjlighet att låta viktigt innehåll spelas upp i sin helhet innan det förkortas på grund av schemaläggningen.

Välj något av följande alternativ som är tillgängliga för att ange avbrottsmetoden i dialogrutan **Kanaltilldelning**:

* **Omedelbart** - När schemat aktiveras eller en uppdatering tas emot kan du avbryta uppspelningen och omedelbart uppdatera eller spela upp det nya innehållet
* **Slut på det aktuella objektet** - När ett nytt schema aktiveras eller en uppdatering tas emot kan du välja att vänta tills det aktuella objektet i sekvensen har spelats upp. Sedan kan du bara uppdatera eller spela upp det nya innehållet.

  >[!NOTE]
  >Det här alternativet är markerat som standard.

* **I slutet av sekvensen** - När ett nytt schema aktiveras eller en uppdatering tas emot kan du välja att vänta tills hela sekvensen är slut. Precis före den önskade sekvensen kan du sedan repetera det första elementet, uppdatera eller spela upp det nya innehållet.

  >[!NOTE]
  >Om du använder det andra eller tredje alternativet kan schemaläggningstiderna som har definierats för tilldelningen bli något fördröjda. Orsaken är att spelaren väntar på slutet av objektet eller sekvensen (efter den angivna tiden) innan den uppdateras. Fördröjningen beror på objektets uppspelningstid.

Följande egenskaper ställs in från alternativet **Schema** i dialogrutan **Kanaltilldelning** .

![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### Aktiveringsfönster {#activation-window}

I aktiveringsfönstret kan du välja ett **startdatum** och ett **slutdatum** för att visa ditt innehåll.

### Återkommande schema {#recurrence-schedule}

Med upprepningsschemat kan du ange ett återkommande schema för ditt innehåll. Klicka på **+ Lägg till schema** för att lägga till ett upprepningsschema i kanalen.

>[!NOTE]
>Du kan lägga till flera återkommande scheman i din kanal.
>Upprepningsscheman introducerar *DayParting*. Du ställer in ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dygnet och återanvänder det som konfigurerats för alla skärmar samtidigt.

Du kan ange följande alternativ:

* **Namn** - Titel på schemat för återkommande aktiviteter.
* **Upprepa** - Välj om schemat ska köras **varje dag**, **varje vecka**, **varje månad** eller **varje år**.
* **Start** - Starttiden för schemat.
* **Slut** - Sluttiden för ditt schema. Du kan ange den efter tid eller varaktighet.
   * **Tid** - Schemat avslutas vid en angiven tidpunkt.
   * **Varaktighet** - Schemat körs för en viss tid i timmar eller minuter.

### DayParting {#dayparting}

Dag-delning innebär att dela upp en dag i tidsplatser och ange vilket innehåll som spelas upp vid önskad tidpunkt. Med AEM Screens kan ni schemalägga kanaler som DayParting inom en dag, vecka eller månad efter behov.

I följande exempel förklaras DayParting i kanaler i tre olika scenarier:

#### Spela upp innehåll på en dag uppdelat i flera tidsplatser {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

I det här exemplet visas hur en restaurang använder DayParting för att visa upp sin frukost, lunch och matmeny varje dag.

Här delas varje dag in i olika tidsplatser, så att kanalinnehållet spelas upp enligt den angivna tiden på dagen. Ange följande egenskaper i schemat för upprepning för din kanal för att spela upp innehållet enligt det här användningsfallet.

| **Namn** | **Upprepningar** | **Start** | **Slut** |
|---|---|---|---|
| Frukosten | Dagligen | 6.00 | 11:00 |
| Lunch | Dagligen | 11:00 | 03:00 |
| Middag | Dagligen | 03:00 | 08:00 |

#### Spela upp innehåll en viss veckodag {#playing-content-on-a-particular-day-of-the-week}

I det här exemplet visas DayParting som implementerats i ett kasino där live-event inträffar varje helg från kl. 20.00 till kl. 23.00. Specialerbjudanden finns tillgängliga för middagsmeny efter kl. 10.00 till kl. 13.00.

| **Namn** | **Upprepningar** | **Start** | **Slut** |
|---|---|---|---|
| Weekend | Vecka: lördag och söndag | 08:00 | 10.00 |
| Specialer | Dagligen: måndag till fredag | 10.00 | 1:00 |

>[!NOTE]
>
>Du kan också definiera ***prioritet*** för varje kanal. Om till exempel två kanaler är inställda för samma dag och tid eller för samma månad, spelas den kanal som har högre prioritet upp först. Minimivärdet för prioritet kan anges till 0.
