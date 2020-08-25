---
title: Kanaltilldelning - senaste offertförfrågan
seo-title: Kanaltilldelning - senaste offertförfrågan
description: Följ den här sidan om du vill veta mer om kanaltilldelning och Dag-delning.
translation-type: tm+mt
source-git-commit: c022e583a52d68e20d7916a8f02341905bb957b6
workflow-type: tm+mt
source-wordcount: '1495'
ht-degree: 1%

---


# Kanaltilldelning {#channel-assignment}

>[!IMPORTANT]
>I det här avsnittet beskrivs kanaltilldelning och planering av kanaler för AEM 6.5.5 Screens Feature Pack och senare.

När du har konfigurerat en skärm måste du tilldela en kanal till en skärm för att kunna visa innehållet.

På den här sidan visas hur du tilldelar en kanal till visningen.

>[!NOTE]
>Du kan tilldela flera kanaler till en skärm.


## Tilldela en kanal {#assign-a-channel-new-release}

Följ nedanstående avsnitt för att skapa ett AEM Screens-projekt och tilldela en kanal till en skärm.

### Skapa ett AEM Screens-projekt och kanaler {#creating-project}

Följ stegen nedan för att konfigurera ett projekt och en kanal:

1. Skapa ett AEM Screens-projekt med namnet **DemoScreens**.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Mer information om hur du skapar ett AEM Screens-projekt finns i [Skapa och hantera projekt](creating-a-screens-project.md) .

1. Skapa en sekvenskanal med namnet **Cafeteria** i mappen **Kanaler** .

1. Markera kanalen och klicka på **Redigera** i åtgärdsfältet för att lägga till innehåll i kanalen.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   I **Cafeteriakanalen** visas nu följande bilder:

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Skapa en plats med namnet **SanJose** och en visning som **Lobby**.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Tilldela kanal till en skärm {#assigning-channel-to-display}

När projektet är klart måste du tilldela kanalen till en skärm för att kunna visa innehållet.

1. Navigera till önskad visning, till exempel **DemoScreens** —> **Locations** —> **SanJose** —> **Lobby**.

1. Tryck/klicka på **Tilldela kanal** i åtgärdsfältet.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Eller

   Tryck/klicka på **Kontrollpanelen** och klicka på **+Tilldela kanal** på panelen **TILLDELADE KANALER &amp; SCHEMALER** .

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. Dialogrutan **Kanaltilldelning** öppnas.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. I alternativet **Inställningar** kan du välja kanal efter sökväg eller namn, ange kanalroll, prioritet, händelser som stöds och avbrottsmetoder. Du kan även aktivera alternativet för att dra till och från den här dialogrutan.

   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Mer information om kanalegenskaper finns i avsnittet [Kanalegenskaper](#channel-properties) .

1. I alternativet **Scheman** väljer du **Tidszon** för referens, **Aktiveringsfönster** och **Återkommande schema**.
   ![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Mer information om kanalegenskaper finns i avsnittet [Kanalegenskaper](#channel-properties) .

1. Klicka på **Spara** när du har konfigurerat inställningarna.

### Visa innehållet i Chrome Player {#viewing-content-output}

I det här exemplet visas utdata på en Chrome Player. När du har tilldelat kanalen till din skärm måste du registrera enheten för en spelare.

Läs mer i [Device Registration](device-registration.md) om hur du registrerar en enhet i en AEM Screens-spelare.

Följande utdata visas när du väljer spelare:

### Förstå kanalegenskaper från kanaltilldelning {#channel-properties}

Följande egenskaper ställs in från alternativet **Inställningar** i dialogrutan **Kanaltilldelning** .

![bild](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

#### Välj en kanal {#select-channel}

Om du väljer en kanal kan du ange en referens till den önskade kanalen, antingen efter kanalnamn eller efter kanalsökväg.

* **efter sökväg**: du anger en explicit referens med kanalens absoluta sökväg.

* **efter namn**: Du anger namnet på den kanal som ska matchas mot en faktisk kanal efter kontext. Med den här funktionen kan du skapa en lokal version av en kanal för att dynamiskt matcha platsspecifikt innehåll. Exempel: en kanal med *dagens* namnaffärer, där det faktiska innehållet skulle vara annorlunda i två städer, men du har fortfarande den tillräkneliga kanalrollen på alla skärmar.

#### Kanalroll {#role-channel}

Kanalrollen definierar visningssammanhanget. Rollen är inriktad på olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen.

#### Priority {#priority-channel}

Prioritet används för att ordna tilldelningarna om flera matchar uppspelningsvillkoren. Den som har det högsta värdet har alltid företräde framför de lägre värdena. Om det till exempel finns två kanaler A och B. A har prioriteten 1 och B har prioriteten 2, och sedan visas kanal B eftersom den har högre prioritet än A.

>[!NOTE]
>Prioriteten för en kanal anges som ett tal (1 för minimum) i dialogrutan **Kanaltilldelning** , vilket nämns ovan. Dessutom sorteras de tilldelade kanalerna baserat på fallande prioritet.

#### Händelser som stöds {#supported-events-channel}

* **Inledande inläsning**: läser in kanalen när spelaren startas. Den kan tilldelas flera kanaler i kombination med ett schema
* **Inaktiv skärm**: läses in när skärmen är inaktiv. Den kan tilldelas flera kanaler i kombination med ett schema
* **Timer**: måste anges när ett schema anges
* **Användarinteraktion**: spelaren växlar till den angivna kanalen, om det finns en användarinteraktion på skärmen (pekning) i en inaktiv kanal och kommer att läsas in när skärmen rörs

#### Avbrottsmetod {#interruption-method-channel}

>[!IMPORTANT]
>
> Det här alternativet är endast tillgängligt med AEM 6.4 Feature Pack 8 eller AEM 6.5 Feature Pack 4.

Som innehållsförfattare bör du kunna ange när en kanal avbryts så att du kan välja att avbryta icke-kritiskt innehåll, men du kan välja att låta viktigt innehåll spelas upp helt innan uppspelningen avbryts på grund av schemaläggning.

Välj något av följande alternativ som är tillgängliga för att ange avbrottsmetoden i dialogrutan **Kanaltilldelning** :

* **Omedelbart**: När schemat aktiveras eller en uppdatering tas emot kan du avbryta uppspelningen och omedelbart uppdatera eller spela upp det nya innehållet
* **I slutet av det aktuella objektet**: När ett nytt schema aktiveras eller en uppdatering tas emot kan du välja att vänta tills det aktuella objektet i sekvensen har spelats upp, och först efter det kan du uppdatera eller spela upp det nya innehållet
   >[!NOTE]
   >Det här alternativet är markerat som standard.
* **I slutet av sekvensen**: När ett nytt schema aktiveras eller en uppdatering tas emot kan du välja att vänta tills hela sekvensen är klar, och precis före den önskade sekvensen går du tillbaka till det första elementet och uppdaterar eller spelar upp det nya innehållet

   >[!NOTE]
   >Om du använder det andra eller tredje alternativet kan schemaläggningstiderna som är definierade för tilldelningen fördröjas något eftersom spelaren väntar på slutet av objektet eller sekvensen (efter den angivna tiden) innan den uppdateras. Fördröjningen beror på objektets uppspelningstid.


Följande egenskaper ställs in från alternativet **Schemalägg** i dialogrutan **Kanaltilldelning** .

#### Referens-tidszon {#reference-timezone}

Med tidszonen Referens kan du välja tidszon för visning av ditt innehåll.

#### Aktiveringsfönster {#activation-window}

I aktiveringsfönstret kan du välja ett **startdatum** och ett **slutdatum** för att visa innehållet.

#### Återkommande schema {#recurrence-schedule}

Med upprepningsschemat kan du ange ett återkommande schema för ditt innehåll. Klicka på **+ Lägg till schema** för att lägga till ett upprepningsschema i kanalen.

>[!NOTE]
>Du kan lägga till flera återkommande scheman i din kanal.
>I Återkommande scheman introduceras *DayParting*, som gör att du kan ställa in ett globalt schema med flera kanaler som körs vid specifika tidpunkter på dagen och återanvända inställningen för alla skärmar samtidigt.

Du kan ange följande alternativ:

* **Namn**: Namn på ditt återkommande schema.
* **Upprepa**: Välj om schemat ska köras **varje dag**, **varje vecka**, **varje månad** eller **varje år**.
* **Start**: Starttiden för ditt schema.
* **Slut**: Sluttiden för ditt schema. Du kan ställa in den genom att:
* **Tid**: Schemat avslutas vid en angiven tidpunkt.
* **Varaktighet**: Schemat körs för en viss tidsperiod i timmar eller minuter.

### DayParting {#dayparting}

DayParting innebär att dela upp en dag i tidskortplatser och ange vilket innehåll som spelas upp vid önskad tidpunkt. Med AEM Screens kan ni schemalägga kanaler i form av DayParting inom en dag, vecka eller månad efter behov.

I följande exempel förklaras DayParting i kanaler i tre olika scenarier:

#### Spela upp innehåll på en dag uppdelat i flera tidsplatser {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

I det här exemplet visas hur en Restaurant använder DayParting för att visa upp sin frukost-, lunch- och middagsmeny.

Här delar vi upp varje dag i tre olika tidsplatser, så att kanalinnehållet spelas upp enligt den angivna tiden på dagen. Följande egenskaper för upprepningsschemat ställs in så att innehållet spelas upp enligt det här användningsfallet.

| **Namn** | **Upprepa** | **Start** | **End** |
|---|---|---|---|
| Frukosten | Dagligen | 6:00 | 11:00 |
| Frukosten | Dagligen | 11:02 | 3:00 PM |
| Frukosten | Dagligen | 3:01 PM | 8:00 PM |

#### Spela upp innehåll en viss veckodag {#playing-content-on-a-particular-day-of-the-week}

I det här exemplet visas den DayParting som skapades i ett kasino där live-event inträffar varje helg från kl. 20.00 till kl. 23.00 och erbjudanden är tillgängliga för middagsmeny efter kl. 10.00 till kl. 13.00.


#### Spela upp innehåll under en viss månad/månad {#playing-content-for-a-particular-month-months}

I det här exemplet visas DayParting för en butik som visar sin sommarsamling från juni till augusti och höstsamlingen från september till slutet av oktober.

Här skapar du DayParting per månad, så att kanalinnehållet spelas upp enligt årets angivna månader.


>[!NOTE]
>
>Dessutom kan du definiera ***prioritet*** för var och en av kanalerna. Om till exempel två kanaler är inställda för samma dag och tid eller för samma månad, spelas den kanal som har högre prioritet upp först. Minimivärdet för prioritet kan anges till 0.

#### Spela upp innehåll för kanaler med samma prioritet {#playing-content-for-channels-with-same-priority}

I det här exemplet visas DayParting för en butik som visar sin vintersamling med samma schema under december. Men eftersom kanal B har prioriteten 2, under den veckan, Kanal B spelar upp innehållet i stället för kanal A.




