---
title: Lägga till komponenter i en kanal
seo-title: Lägga till komponenter i en kanal
description: Följ den här sidan om du vill veta mer om hur du lägger till komponenter i kanaler i ett AEM Screens-projekt.
seo-description: Följ den här sidan om du vill veta mer om hur du lägger till komponenter i kanaler i ett AEM Screens-projekt.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: cec2a2f8b056bf713e56a9fab08d88e29263820b

---


# Lägga till komponenter i en kanal{#adding-components-to-a-channel}

Komponenterna är de grundläggande elementen i AEM-upplevelsen (Adobe Experience Manager). Du kan använda ett antal komponenter och lägga till dem i din kanal i ett AEM Screens-projekt.

## Komponenter i AEM-skärmar {#components-in-aem-screens}

AEM Screens innehåller olika AEM-komponenter som kan användas i ett skärmsprojekt.

### Visa komponenter för AEM-skärmar {#viewing-aem-screens-components}

När du skapar ett AEM-skärmsprojekt visas en lista med standardkomponenter som kan läggas till i projektet.

Följ stegen nedan om du vill visa standardkomponenterna för ditt skärmsprojekt:

1. Markera kanalen. Exempel: **We.Retail In Store** —> **Channels** —> **Idle Channel**.

1. Klicka på **Redigera** i åtgärdsfältet för att öppna AEM-redigeraren.
1. Klicka på **+** -ikonen i sidofältet för att öppna komponenterna.
1. Alla komponenter som inkluderas som standard i ett AEM Screens-projekt visas, vilket visas i bilden nedan.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Lägga till en ny komponent {#adding-a-new-component}

AEM tillhandahåller ett antal andra komponenter. Du kan alltid lägga till andra komponenter (som inte ingår som standard) i ditt projekt, eftersom de är kompatibla med AEM-skärmar.

I följande exempel visas hur en Livefyre-komponent läggs till i ett AEM Screens-projekt:

1. Markera kanalen där du vill lägga till en ny komponent. Exempel: **We.Retail In Store** —> **Channels** —> **Idle Channel**.

1. Klicka på **Redigera** i åtgärdsfältet för att öppna redigeraren.
1. Välj **designläge** .
1. Markera hela designredigeraren till höger och klicka på inställningssymbolen för att öppna dialogrutan **ParSys Design** .
1. Du kan välja vilka komponenter du vill importera till ditt AEM-skärmsprojekt. I följande exempel visas hur **Livefyre** -komponenten läggs till i ett AEM Screens-projekt.

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>På samma sätt kan du lägga till valfritt antal andra nya komponenter som är kompatibla med AEM-skärmar i ditt projekt.

## Förstå AEM Screen-komponenter {#understanding-aem-screen-components}

I följande avsnitt förklaras vilka AEM Screens-komponenter du kan använda i ditt projekt.

>[!NOTE]
>
>Om du vill visa egenskaperna för en komponent markerar du komponenten och klickar på hamsikonen för att öppna/visa egenskaper.

### Program {#application}

Med **programkomponenten** kan du lägga till ett program i kanalen.

Programkomponenten har följande egenskaper:

| **Egenskap** | **Beskrivning** |
|---|---|
| ***Programsökväg*** | Välj den absoluta sökvägen där programmet finns. |
| ***Varaktighet (ms)*** | Välj varaktighet för programmet. Som standard är längden inställd på -1, vilket innebär att elementet körs för alltid (det vill säga ett enkelsidigt program). Om du ställer in varaktighetsvärdet >0 visas elementet för den angivna varaktigheten och fortsätter sedan till nästa. |

I följande exempel visas hur du bäddar in en programkomponent tillsammans med förhandsvisningen av dess egenskaper:

![adding_componentsApplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Se exemplet ovan för att visa egenskaper för var och en av komponenterna nedan.

### Kanal {#channel}

Med **kanalkomponenten** kan du lägga till en hel kanal i projektet.

Komponenten Channel har följande egenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong><em>Kanalsökväg</em></strong></td>
   <td>Välj den absoluta sökvägen där programmet finns.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Varaktighet (ms)</em></strong></td>
   <td>Markera kanalens hela längd. Om du anger längden som -1 anger du att den inbäddade kanalen kommer att köra hela längden i en viss kanal.</td>
  </tr>
 </tbody>
</table>

### Inbäddad sida {#embedded-page}

Med en **inbäddad sida** kan du lägga till en inbäddad sida i projektet. Det kan till exempel vara ett webbprogram eller en produktkatalog.

Den inbäddade sidan har följande egenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong><em>Sidsökväg<br /> </em></strong></td>
   <td>Välj den här absoluta sökvägen där kanalen finns.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Varaktighet (ms)</em></strong></td>
   <td>Markera kanalens hela längd. Om du anger längden som -1 anger du att den inbäddade kanalen kommer att köra hela längden i en viss kanal.</td>
  </tr>
 </tbody>
</table>

### Inbäddad sekvens {#embedded-sequence}

>[!NOTE]
>
>Mer information om inbäddade sekvenser finns i avsnittet [Inbäddade sekvenser](embedded-sequences.md) under redigeringsskärmar.

Med en inbäddad sekvens kan du lägga till en inbäddad sekvenskanal i den befintliga kanalen (med andra resurser).

Den inbäddade sekvensen har följande sidegenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td>Kanalsökväg</td>
   <td>Välj den absoluta sökvägen för den sekvens som du vill ta med i kanalen.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Varaktighet (ms)</em></strong></td>
   <td>Markera kanalens hela längd. Om du anger längden som -1 anger du att den inbäddade kanalen kommer att köra hela längden i en viss kanal.</td>
  </tr>
  <tr>
   <td><strong><em>Strategi</em></strong></td>
   <td>Ställ in den på <strong>original</strong> eller <strong>enkel</strong>. Om du ställer in värdet på <strong>original</strong> körs efterföljande helt på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är <strong>enkelt</strong> och det skulle bara visa ett objekt i efterföljande körning (till exempel det första objektet i den första slingan, det andra objektet i den andra slingan och så vidare).</td>
  </tr>
 </tbody>
</table>

### Dynamisk inbäddad sekvens {#dynamic-embedded-sequence}

Med en dynamisk inbäddad sekvens kan du lägga till en sekvens som liknar den ovan nämnda förutom efter kanalroll.

Mer information om inbäddade sekvenser finns i avsnittet [Inbäddade sekvenser](embedded-sequences.md) under redigeringsskärmar.

Den dynamiska inbäddade sekvensen har följande egenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong><em>Kanaltilldelningsroll</em></strong><br /> </td>
   <td>Ange kanalrollen.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Varaktighet (ms)</em></strong></td>
   <td>Markera kanalens hela längd. Om du anger längden som -1 anger du att den inbäddade kanalen kommer att köra hela längden i en viss kanal.</td>
  </tr>
  <tr>
   <td><strong><em>Strategi</em></strong></td>
   <td>Ställ in den på <strong>original</strong> eller <strong>enkel</strong>. Om du ställer in värdet på <strong>original</strong> körs efterföljande helt på varje cykel i den överordnade sekvensen. Det andra möjliga värdet är <strong>enkelt</strong> och det skulle bara visa ett objekt i efterföljande körning (till exempel det första objektet i den första slingan, det andra objektet i den andra slingan och så vidare).</td>
  </tr>
 </tbody>
</table>

### Experience Fragment {#experience-fragment}

Med Experience Fragment kan ni lägga till ett upplevelsefragment (en grupp med en eller flera komponenter, inklusive innehåll och layout som kan refereras på sidor) i kanalen för AEM-skärmar. Dra och släpp komponenten till AEM-redigeraren och välj upplevelsefragmentet.

Mer information om hur du skapar ett upplevelsefragment och använder det i ett AEM Screens-projekt finns i [Använda Experience Fragments](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **Egenskap** | **Beskrivning** |
|---|---|
| **Experience Fragment** |
| ***Experience Fragment*** | Välj upplevelsefragmentet. |
| ***Varaktighet*** | Markera hela varaktigheten för det upplevelsefragment som spelas upp i kanalen. |
| **Offlinekonfiguration** |
| ***Bibliotek på klientsidan*** | Javascript- och CSS-filer. |
| ***Statiska filer*** | Statiska filer som du kan lägga till som offlinekonfigurationer i ditt upplevelsefragment. |

>[!NOTE]
>
>Biblioteken **på** klientsidan och de **statiska filer** som du lägger till från den här komponenten kommer att vara utöver de redan konfigurerade biblioteken **på** klientsidan och de statiska filer som läggs till från upplevelsefragmentets **egenskaper**.

### Bild {#image}

Med en bild kan du lägga till en bild i kanalen.

Bildresursen har tre flikar: **Bild**, **Hjälpmedel** och **Sekvens**:

| **Egenskap** | **Beskrivning** |
|---|---|
| **Bild** |
| ***Bildresurs*** | Välj bildresurs. |
| ***Titel*** | Bildens namn. |
| ***Länka till*** | Lägg till en länk till bilden. |
| ***Beskrivning*** | Kort beskrivning av bilden. |
| ***Storlek*** | Bildens storlek. |
| **Tillgänglighet** |
| ***Alternativ text*** | Alternativ text till bilden. |
| **Sekvens** |
| ***Varaktighet*** | Som standard är längden inställd på *8000 ms*. Om du vill ändra uppspelningstiden för bilden uppdaterar du fältet **Varaktighet** . |

### Övergång {#transition}

Med komponenten Transition kan du lägga till en övergång i skärmsprojektet.

I följande bild visas övergångskomponenten (som lagts till med dra och släpp) i redigeraren.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Markera övergångsikonen och klicka på **Konfigurera** (skiftnyckelsikonen) för att öppna dialogrutan **Övergång** . Den här dialogrutan innehåller tre flikar:

* **Övergång**
* **Sekvens**
* **Aktivering**

>[!NOTE]
>
>Som standard är sekvensen inställd på 600 ms. Du kan uppdatera övergångssekvensen till ett annat värde på fliken **Sekvens** .

![övergång](assets/transition.gif)

Övergångskomponenten har följande egenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><strong>Övergång</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Typ</em></strong></td>
   <td><p>Typ av övergång mellan elementet före och det efter. Övergångstypen <strong>Type</strong> innehåller följande alternativ:</p>
    <ul>
     <li><strong>Normal</strong></li>
     <li><strong>Tona</strong></li>
     <li><strong>Glid in från höger</strong></li>
     <li><strong>Glid in från vänster</strong></li>
     <li><strong>Glid in uppifrån</strong></li>
     <li><strong>Glid in nedifrån</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Sekvens</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Varaktighet</em></strong></td>
   <td>Markera hela övergångstiden. Som standard är den inställd på 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Aktivering</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Aktiv från</em></strong></td>
   <td>Tidsstämpel som beskriver när övergången kan aktiveras.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Aktiv tills</em></strong></td>
   <td>Tidsstämpel som beskriver tills övergången kan aktiveras.</td>
  </tr>
  <tr>
   <td><strong><em>Schema</em></strong></td>
   <td>Lägg till ett fördefinierat schema.</td>
  </tr>
 </tbody>
</table>

### Video {#video}

Med videokomponenten kan du lägga till en video i skärmsprojektet.

Videokomponenten har följande egenskaper:

<table>
 <tbody>
  <tr>
   <td><strong>Egenskap</strong></td>
   <td><strong>Beskrivning</strong></td>
  </tr>
  <tr>
   <td><em><strong>Videoresurs</strong></em></td>
   <td>Markera länken till videon.</td>
  </tr>
  <tr>
   <td><em><strong>Varaktighet</strong></em></td>
   <td>Välj videons längd. Som standard är längden inställd på -1, vilket innebär att elementet körs för alltid. Om du ställer in varaktighetsvärdet &gt;0 visas elementet för den angivna varaktigheten och fortsätter sedan till nästa.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Återgivning</strong></em></td>
   <td><p>Om videoproportionerna inte får plats på skärmen kan du justera återgivningen så att den antingen <strong>innehåller</strong> eller <strong>täcker</strong>.</p> <p><em>Innehåller</em> innebär att hela videon visas och att de saknade områdena fylls med en svart ram.</p> <p><em>Omslag</em> innebär att videon täcker hela visningsrutan, men vissa delar som flödar över sidorna är dolda.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Storlek</strong></em></td>
   <td>Videons storlek.</td>
  </tr>
 </tbody>
</table>

