---
title: Introduktion till AEM Screens
description: Läs om AEM Screens och vad det kan göra för dig.
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 8%

---

# Introduktion till AEM Screens {#introduction}

**AEM Screens** är en digital signeringslösning som gör att du kan skapa, publicera och spela upp dynamiska och interaktiva digitala upplevelser. Det omfattar olika typer av skärmar på plats i kombination med en omfattande strategi för digital marknadsföring i flera kanaler.

Med AEM Screens kan du skapa:

* **dedikerade digitala menybord**
* **produktrekommendationer**
* **bakgrundsbilder för livsstil**

Screens erbjuder dessutom många unika program för kunder och anställda baserat på den domän där programmen är distribuerade, till exempel:

* **interaktiva skärmar**
* **hitta**
* **varumärkning**
* **lägger till atmosfär i din miljö**

Det är enkelt och intuitivt att skapa och hantera ett nätverk för digitala signaturer med hjälp av AEM Screens. En spelarapp fungerar som värd för innehållskanaler som skapats för AEM Screens av kunder eller implementeringspartners. *Platser* hanterar en fördefinierad platshierarki och innehåller skärmar. Varje *skärm* har en kontrollpanel som visar olika kopplade enheter och skärmar. Innehåll för AEM Screens hanteras i *kanaler*. *AEM Screens Player* återger innehåll som finns i kanaler på skärmar.

>[!NOTE]
>
>Mer information om olika funktioner i en AEM Screens-projektutveckling och -hantering finns i **[AEM Screens användarhandbok](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction)**.

## AEM Sites jämfört med AEM Screens {#aem-sites-screens}

>[!NOTE]
>
>Om implementeringsteamet har erfarenhet av att arbeta med AEM Sites-program är det viktigt att förstå skillnaden mellan AEM Sites och AEM Screens.

AEM Screens erbjuder en enhetlig redigerings-/uppspelningsplattform för distribution av innehåll till digitala signeringsenheter på offentliga platser. Även om den som skapar upplevelsen bör sträva efter att bibehålla en konsekvent upplevelse över webben och i alla kanaler, finns det vissa skillnader som bör noteras.

* **Dwell-time**: Webbsidor är vanligtvis utformade för att tillhandahålla en mängd information som kan användas under en relativt längre tid. Digitala upplevelser på plats bör däremot förutse visningsprogrammets behov och ge tydliga och kortfattade anvisningar om hur och varför användaren bör engagera sig. Sådan uppmärksamhet ger upplevelser som är mer målinriktade, välstrukturerade och sammanhangsbaserade.

* **Visningsavstånd**: Visningsavstånd är längre eller längre bort än det normala visningsavstånd som användare upplever på en webbplats. Därför bör textstorleken normalt vara större och mellanrummet mellan text, bilder och annat kostnadsfritt innehåll testas baserat på den förväntade skärmstorleken och placeringen i det fysiska utrymmet.

* **Persistence**: Spelarenhetens anslutna läge får aldrig påverka om digitala upplevelser levereras till användaren. Spelaren måste vara konstruerad så att en eller flera upplevelser alltid finns kvar och kan levereras oavsett spelarenhetens anslutna läge.

* **Segmentering av medieslinga**: Genom att konfigurera varje spelarenhet så att den har ett eget loopsegment kan du enkelt skapa, publicera och spela upp lokaliserat innehåll i den övergripande digitala upplevelsen. Medieresurser som finns i inbäddade sekvenskanaler läggs till i det föregående slingsegmentet och ger möjlighet att rikta in ett medielöpssegment för varje platsgruppering.

* **Interaktiva upplevelser**: Ett beröringsaktiverat datorkioskprogram kan skapas och levereras i en Screens-kanal med AEM och SPA. Det är en god vana att använda konsekventa designegenskaper i flera kanaler, en inaktivitetstimer för att återställa upplevelsen och ett tydligt anrop till åtgärd för vilka åtgärder programmet kan utföra. Landningssidan ska bestå av viktiga digitala element som är utformade för att förmedla värde, locka användaren till skärmen och uppmana användaren att engagera sig.

AEM Screens tillhandahåller ett ramverk för att distribuera innehåll till fysiska enheter. Innehållet tilldelas kanaler i Screens, som kan innehålla mediainnehåll eller program för pekskärmar. I det här ramverket kan ett AEM Sites-program levereras som innehåll via en kanal.

En AEM webbplats måste vara formaterad för användning med dimensionerna för den visningsenhet som den är avsedd för. Det bör göras innan det släpps in i en kanal i Screens.

>[!NOTE]
>Många AEM Sites-komponenter är inte kompatibla med AEM Screens. AEM Screens har många av sina egna färdiga komponenter som gör att du kan skapa digitala upplevelser utan att behöva anpassa dem. Om projektkraven tillåter det ska du använda den inbyggda AEM Screens-funktionen där det är möjligt.
