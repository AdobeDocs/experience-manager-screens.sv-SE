---
title: Kanaltilldelning - senaste offertförfrågan
seo-title: Kanaltilldelning - senaste offertförfrågan
description: Följ den här sidan om du vill veta mer om kanaltilldelning och Dag-delning.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
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

1. Klicka på **Spara** när du har konfigurerat inställningarna.

### Visa innehållet i Chrome Player {#viewing-content-output}

### Förstå kanalegenskaper från kanaltilldelning {#channel-properties}

### Referenskanal {#ref-channel}

Med referenskanalen kan du ange en referens till den önskade kanalen, antingen efter kanalnamn eller efter kanalsökväg.

* **efter sökväg**: du anger en explicit referens med kanalens absoluta sökväg.

* **efter namn**: Du anger namnet på den kanal som ska matchas mot en faktisk kanal efter kontext. Med den här funktionen kan du skapa en lokal version av en kanal för att dynamiskt matcha platsspecifikt innehåll. Exempel: en kanal med *dagens* namnaffärer, där det faktiska innehållet skulle vara annorlunda i två städer, men du har fortfarande den tillräkneliga kanalrollen på alla skärmar.

### Kanalroll {#role-channel}

Kanalrollen definierar visningssammanhanget. Rollen är inriktad på olika åtgärder och är oberoende av den faktiska kanal som uppfyller rollen.

### Priority {#priority-channel}

Prioritet används för att ordna tilldelningarna om flera matchar uppspelningsvillkoren. Den som har det högsta värdet har alltid företräde framför de lägre värdena. Om det till exempel finns två kanaler A och B. A har prioriteten 1 och B har prioriteten 2, och sedan visas kanal B eftersom den har högre prioritet än A.

>[!NOTE]
>Prioriteten för en kanal anges som ett tal (1 för minimum) i dialogrutan **Kanaltilldelning** , vilket nämns ovan. Dessutom sorteras de tilldelade kanalerna baserat på fallande prioritet.

### Händelser som stöds {#supported-events-channel}

* **Inledande inläsning**: läser in kanalen när spelaren startas. Den kan tilldelas flera kanaler i kombination med ett schema
* **Inaktiv skärm**: läses in när skärmen är inaktiv. Den kan tilldelas flera kanaler i kombination med ett schema
* **Timer**: måste anges när ett schema anges
* **Användarinteraktion**: spelaren växlar till den angivna kanalen, om det finns en användarinteraktion på skärmen (pekning) i en inaktiv kanal och kommer att läsas in när skärmen rörs

### Avbrottsmetod {#interruption-method-channel}

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