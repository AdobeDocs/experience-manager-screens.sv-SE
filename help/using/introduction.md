---
title: Introduktion till [!UICONTROL AEM Screens]
seo-title: Guide till bästa praxis för [!UICONTROL AEM Screens]-projekt
description: Den här sidan är ett introduktionsavsnitt för AEM Screens
seo-description: Den här sidan innehåller en introduktion till AEM Screens
translation-type: tm+mt
source-git-commit: 8a80ea5c79bfd9890211bd7e0d958ab0d4c2d4b6

---


# Introduktion till AEM-skärmar {#introduction}

**AEM (Adobe Experience Manager) Screens** är en lösning för digitala signaturer som gör att ni kan skapa, publicera och spela dynamiska och interaktiva digitala upplevelser som omfattar olika typer av skärmar på plats i kombination med en omfattande strategi för digital marknadsföring i flera kanaler.

Med AEM Screens kan du skapa:

* **dedikerade digitala menybord**
* **produktrekommendationer**
* **livsstilsbild i bakgrunden**

Skärmar erbjuder dessutom många unika program för kunder och anställda baserat på den domän där de distribueras, till exempel:

* **interaktiva bildskärmar**
* **hitta**
* **branding**
* **skapa atmosfär i din miljö**

Det är enkelt och intuitivt att skapa och hantera ett nätverk för digitala signaturer med hjälp av AEM Screens. En spelarapp fungerar som värd för innehållskanaler som skapats för AEM Screens av kunder eller implementeringspartners. *Platserna* hanterar en fördefinierad platshierarki och innehåller skärmar. Varje *skärm* har en kontrollpanel som visar olika kopplade enheter och skärmar. Innehåll för AEM Screens hanteras i *kanaler*. *AEM Screens Player* återger innehåll som finns i kanaler på skärmar.



>[!NOTE]
>
>Om du vill veta mer om olika funktioner i ett AEM Screens-projekt går du till **[AEM Screens User Guide](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)**.

## AEM Sites jämfört med AEM Screens {#aem-sites-screens}

> [!NOTE]
>
> Om implementeringsteamet har erfarenhet av att arbeta med AEM Sites-program är det viktigt att förstå skillnaden mellan AEM Sites och AEM Screens.

AEM Screens är en enhetlig redigerings-/uppspelningsplattform för distribution av innehåll till digitala signeringsenheter på offentliga platser. Även om den som skapar upplevelsen bör sträva efter att bibehålla en konsekvent upplevelse över webben och i alla kanaler, finns det vissa skillnader som bör noteras.

* **Dwell-time**: Webbsidor är oftast utformade för att ge en mängd information som kan användas under en relativt längre tidsperiod. Digitala upplevelser på plats bör däremot förutse visningsprogrammets behov och ge tydliga och kortfattade anvisningar om hur och varför användaren bör engagera sig. Detta resulterar i upplevelser som är mer målinriktade, välstrukturerade och sammanhangsbaserade.

* **Visningsavstånd**: Visningsavståndet är i allmänhet längre eller längre bort än den normala tittarupplevelsen på en webbplats. Därför bör textstorleken normalt vara större och mellanrummet mellan text, bilder och annat kostnadsfritt innehåll testas baserat på den förväntade skärmstorleken och placeringen i det fysiska utrymmet.

* **Persistence**: Spelarenhetens anslutna läge ska aldrig tillåtas påverka om digitala upplevelser levereras till användaren eller inte. Spelaren måste vara konstruerad så att en eller flera upplevelser alltid finns kvar och kan levereras oavsett spelarenhetens anslutna läge.

* **Segmentering med** medieslinga: Genom att konfigurera varje spelarenhet så att den har ett eget loopsegment kan du enkelt skapa, publicera och spela upp lokaliserat innehåll i den övergripande digitala upplevelsen. Medieresurser som finns i inbäddade sekvenskanaler läggs till i det föregående slingsegmentet och ger möjlighet att rikta in ett medielöpssegment för varje platsgruppering.

* **Interaktiva upplevelser**: Pekaktiverat datorprogram kan redigeras och levereras i en skärmkanal med hjälp av AEM och SPA-redigeraren. Det är en god vana att använda konsekventa flerkanalsdesignegenskaper, en inaktivitetstimer för att återställa upplevelsen och ett tydligt anrop till åtgärd för vilka åtgärder programmet kan utföra. Landningssidan ska bestå av viktiga digitala element som är utformade för att förmedla värde, locka användaren till skärmen och uppmana användaren att engagera sig.

AEM Screens har ett ramverk för att distribuera innehåll till fysiska enheter. Innehållet tilldelas kanaler på skärmar, som kan innehålla mediainnehåll eller program för pekskärmar. I det här ramverket kan en AEM Sites-applikation levereras som innehåll via en kanal.

Innan en AEM Sites tas bort i en kanal på skärmar måste den vara formaterad för att kunna användas med dimensionerna för den visningsenhet som den är avsedd för.

> [!NOTE]
>
> Många AEM Sites-komponenter är inte kompatibla med AEM-skärmar. AEM Screens innehåller många av sina egna färdiga komponenter som gör att du kan skapa digitala upplevelser utan att behöva anpassa dem. Om projektkraven tillåter det ska du använda den inbyggda AEM-skärmens funktionalitet där det är möjligt.