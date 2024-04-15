---
title: Projekttaxonomi
description: Läs mer om projekttaxonomi när det gäller AEM Screens.
exl-id: be0ad77a-e593-4c95-8a58-4e5ccb974fcf
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Projekttaxonomi {#project-taxonomy}

>[!NOTE]
>
>En typisk intressent för den här aktiviteten är en AEM implementerare.

Innan du skapar ett AEM Screens-projekt måste du förstå och integrera alla komponenter som definierats i projektets UX-trådramsfas.

Tänk på följande innan du implementerar din digitala signeringslösning från AEM Screens:

* **Platser**
* **MediaZones**
* **Visar**
* **Schemaläggning**
* **Förhandsgranska innehållet**

Mer information om dessa villkor finns i [Ordlista](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/overview/screens-glossary).

>[!NOTE]
>
>Det är bäst att överväga att använda:
>
>* databas för maskinvaruresurser för att automatiskt fylla i ett skärmsprojekt
>* textkonfigurationsfil som automatiskt pekar varje spelare mot en viss instans av en AEM

## Implementera ett AEM Screens-projekt {#creating-a-project}

En AEM Screens-författare ansvarar för att skapa och hantera en användarupplevelse med de tillgängliga komponenterna i AEM Screens. Författaren skapar och granskar materialet och har ett lättanvänt grafiskt användargränssnitt genom att konfigurera, driftsätta och integrera de tillgängliga segmenten i AEM Screens.

>[!NOTE]
>
>En författare skapar kanaler från de angivna sekvenserna och känner till kampanjens målgrupp och det önskade fokus. En AEM Screens-författare skapar och organiserar användarupplevelsen genom att skapa olika kanaler och tilldela sekvenser till en tidsinriktad kanalupplevelse.

En författare startar vanligtvis ett AEM Screens-projekt av:

* [skapa ett AEM Screens-projekt](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [skapa kanaler](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-channels)
* [lägga till komponenter och resurser i kanalen](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/adding-components-to-a-channel)
* [skapa tidsplaner](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-schedules)
* [skapa platser](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-locations)
* [skapa skärmar](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [tilldela kanaler till skärmar](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/assigning-channels/channel-assignment)

* [visa innehåll i en AEM Screens-spelare](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/working-with-screens-player)

>[!NOTE]
>Du kan också importera en uppsättning platser gruppvis från ett CSV-/XLS-kalkylblad till ditt AEM Screens-projekt. Se [Ny projektimporterare från fil](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/project-importer).
