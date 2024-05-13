---
title: Kanaltilldelning
description: Lär dig mer om kanaltilldelning och dagsdelning.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---

# Kanaltilldelning {#channel-assignment}

>[!IMPORTANT]
>I det här avsnittet beskrivs kanaltilldelning och planering av kanaler för funktionspaket som är äldre än AEM 6.5.5-skärmar.

När du har konfigurerat en visning tilldelar du en kanal till en visning för att visa innehållet.

På den här sidan visas hur du tilldelar en kanal till visningen.

>[!NOTE]
>Du kan tilldela flera kanaler till en skärm.

## Tilldela en kanal {#assign-a-channel}

Följ stegen nedan för att tilldela en kanal till en skärm:

1. Navigera till önskad visning, till exempel **DemoProject** > **Platser** > **SanJose** > **StoreDisplay**.

   ![bild](assets/screen_shot_2018-08-23at25359pm.png)

1. Klicka **Tilldela kanal** i åtgärdsfältet.

   eller

   Klicka **Kontrollpanel** och klicka **+Tilldela kanal** från **TILLDELADE KANALER** så att du kan öppna **Kanaltilldelning** -dialogrutan.

   ![bild](/help/user-guide/assets/channel-assign1.png)

   Du kan konfigurera egenskaperna från **Kanaltilldelning** från avsnittet nedan. Se [Kanalegenskaper](#channel-properties) om du vill ha mer information om kanalegenskaper.

## Förstå kanalegenskaper från kanaltilldelning {#channel-properties}

### Referenskanal {#ref-channel}

Med en referenskanal kan du ange en referens till den önskade kanalen, antingen efter kanalnamn eller efter kanalsökväg.

* **efter bana** - Du anger en explicit referens med kanalens absoluta sökväg.

* **efter namn** - Du anger namnet på den kanal som matchar en faktisk kanal efter kontext. Med den här funktionen kan du skapa en lokal version av en kanal så att du dynamiskt kan matcha platsspecifikt innehåll. En kanal med namnet *dagens erbjudanden*, där det faktiska innehållet skulle vara annorlunda i två städer, men du fortfarande har den tillräkneliga kanalrollen på alla skärmar.

### Kanalroll {#role-channel}

Kanalrollen definierar visningssammanhanget. Rollen avser olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen.

### Prioritet {#priority-channel}

Prioritet används för att ordna tilldelningarna om flera matchar uppspelningsvillkoren. Den som har det högsta värdet har alltid företräde framför de lägre värdena. Om det till exempel finns två kanaler A och B. A har prioriteten 1 och B har prioriteten 2, och sedan visas kanal B eftersom den har högre prioritet än A.

>[!NOTE]
>Prioriteten för en kanal anges som ett tal (1 för minimum) i **Kanaltilldelning** som nämns ovan. Dessutom sorteras de tilldelade kanalerna baserat på fallande prioritet.

### Händelser som stöds {#supported-events-channel}

* **Inledande inläsning** - Läser in kanalen när spelaren startas. Den kan tilldelas flera kanaler med ett schema.
* **Inaktiv skärm** - Läser in när skärmen är inaktiv. Den kan tilldelas flera kanaler med ett schema.
* **Timer** - Måste anges när ett schema anges.
* **Användarinteraktion** - Spelaren växlar till den angivna kanalen om det finns en användarinteraktion på skärmen (beröring) i en inaktiv kanal och läses in när skärmen rörs.

### Avbrottsmetod {#interruption-method-channel}

>[!IMPORTANT]
>
> Det här alternativet är bara tillgängligt med <!--AEM 6.4 Feature Pack 8 or -->AEM 6.5 Feature Pack 4.

Ange när en kanal ska avbrytas som innehållsförfattare. Om du gör det kan du klippa ut icke-kritiskt innehåll om du vill, men du kan även låta viktigt innehåll spelas upp innan uppspelningen avbryts på grund av schemaläggningen.

Klicka på ett av följande alternativ som är tillgängliga för att ange avbrottsmetoden i dialogrutan **Kanaltilldelning** dialogruta:

* **Omedelbart** - När schemat aktiveras eller en uppdatering tas emot kan du avbryta uppspelningen och omedelbart uppdatera eller spela upp det nya innehållet.
* **Vid slutet av aktuell artikel** - När ett nytt schema aktiveras eller en uppdatering tas emot kan du välja att vänta tills det aktuella objektet i sekvensen har spelats upp. Först därefter kan du uppdatera eller spela upp det nya innehållet.

  >[!NOTE]
  >Det här alternativet är markerat som standard.
* **I slutet av sekvensen** - När ett nytt schema aktiveras eller en uppdatering tas emot, kan du välja att vänta tills hela sekvensen är klar. Precis före den önskade sekvensen kan du sedan repetera det första elementet, uppdatera eller spela upp det nya innehållet.

  >[!NOTE]
  >Om du använder det andra eller tredje alternativet kan schemaläggningstiderna som har definierats för tilldelningen bli något fördröjda. Orsaken är att spelaren väntar på slutet av objektet eller sekvensen (efter den angivna tiden) innan den uppdateras. Fördröjningen beror på objektets uppspelningstid.

### Schema {#schedule-channel}

Med Schema kan du ange en beskrivning i texten när kanalen ska visas. Här kan du också definiera ett startdatum (**aktiv från**) och ett slutdatum (**aktiv tills**) för den kanal som ska visas.

**Visa tips för Attraktion**

Visa verktygstipset för attribut anger om verktygstipset för attributet (&quot;*Peka var som helst för att börja*&quot;) måste visas eller inte medan kanalen körs.

### DayParting {#dayparting}

Scheman, när de kombineras med **DayParting** kan du ange ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dygnet och återanvända det som är inställt för alla skärmar samtidigt.

DayParting innebär att dela upp en dag i tidskortplatser och ange vilket innehåll som spelas upp vid önskad tidpunkt. Med AEM Screens kan ni schemalägga kanaler i form av DayPparting inom en dag, vecka eller månad efter behov.

I följande exempel förklaras Dag-delning i kanaler i tre olika scenarier:

#### Spela upp innehåll på en dag uppdelat i flera tidsplatser {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

I det här exemplet visas hur en Restaurant använder DayParting för att visa sin frukost-, lunch- och middagsmeny.

Här delar du upp varje dag i tre olika tidsplatser så att kanalinnehållet spelas upp enligt den angivna tiden på dagen:

| **Kanal** | **Roll** | **Prioritet** | **Schema** |
|---|---|---|---|
| Meny_A | Frukosten |  | Efter 6:00 och före 11:00 |
| Meny_B | Lunch |  | Efter 11:00 och före 15:00 |
| Meny_C | Middag |  | Efter 15:00 och före 20:00 |

#### Spela upp innehåll en viss veckodag {#playing-content-on-a-particular-day-of-the-week}

I det här exemplet visas dagenParting som uppnåtts i ett kasino där live-event inträffar varje helg från klockan åtta till klockan 10.00 och erbjudanden finns tillgängliga för middagsmeny efter klockan 10.00 till klockan 10.00.

<table>
 <tbody>
  <tr>
   <td><strong>Kanal</strong></td>
   <td><strong>Roll</strong></td>
   <td><strong>Prioritet</strong></td>
   <td><strong>Schema</strong></td>
  </tr>
  <tr>
   <td>LiveConvert</td>
   <td>Weekend</td>
   <td> </td>
   <td>21 oktober 2017-22 oktober 2017 <br /> efter 20:00 före 22:00</td>
  </tr>
  <tr>
   <td>SpecialMiddag</td>
   <td>Weekend</td>
   <td> </td>
   <td>21 oktober 2017-22 oktober 2017 <br /> efter 22:00 före 1:00</td>
  </tr>
 </tbody>
</table>

#### Spela upp innehåll under en viss månad/månad {#playing-content-for-a-particular-month-months}

I det här exemplet visas DayParting för en butik som visar sin sommarsamling från juni till augusti och höstsamlingen från september till slutet av oktober.

Här skapar du DayParting som per månad, så att kanalinnehållet spelas upp enligt årets angivna månader.

| **Kanal** | **Roll** | **Prioritet** | **Schema** |
|---|---|---|---|
| SummerCollection | Sommar |  | 1 juni 2017-31 augusti 2017 |
| FallCollection | Höst |  | 1 september 2017-30 oktober 2017 |

>[!NOTE]
>
>Du kan också definiera ***Prioritet*** för varje kanal. Om till exempel två kanaler är inställda för samma dag och tid eller för samma månad, spelas den kanal som har högre prioritet upp först. Minimivärdet för prioritet kan anges till 0.

#### Spela upp innehåll för kanaler med samma prioritet {#playing-content-for-channels-with-same-priority}

I det här exemplet visas DayParting för en butik som visar sin vintersamling med samma schema under december. Men eftersom kanal B har prioriteten 2 under den veckan spelar kanal B upp innehållet i stället för kanal A.

| **Kanal** | **Roll** | **Prioritet** | **Schema** |
|---|---|---|---|
| A | Vinter | 1 | 1 december 2017-31 december 2017 |
| B | Jul | 2 | 24 december 2017-31 december 2017 |


>[!NOTE]
>
> Mer information om DayParting finns i avsnitten nedan:
>
>* [Hantera återkommande i resurser](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Hantera återkommande för resurser i en kanal](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
