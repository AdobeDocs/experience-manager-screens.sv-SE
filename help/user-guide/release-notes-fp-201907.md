---
title: Versionsinformation för funktionspaket 201907
description: Läs om AEM Screens Feature Pack 201907 som släpptes den 31 juli 2019.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Versionsinformation för funktionspaket 201907 {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Adobe rekommenderar att du uppgraderar till den senaste versionen av Adobe Experience Manager (AEM). AEM Screens har underhållsstöd för AEM 6.3 Screens.

AEM Screens har släppt AEM 6.4.5 Feature Pack 5 och AEM 6.5.1 Feature Pack 1 med följande information.

## Releasedatum {#release-date}

Releasedatum för AEM Screens Feature Pack 2019 är 31 juli 2019.

### Nyheter {#what-s-new}

* **Datautlösare driver resursförändringar i en AEM Screens-kanal**

Spelaren byter till en kanal som visar nödinformation. Nödsystemet skickar denna information när det tar emot en händelse. Kanalen fungerar bara tills krissituationen är över.


Se [Nödkanal](emergency-channel.md) användningsfall för implementering.

* **Målgruppsanpassning aktiverad för asynkrona komponenter

Målinriktning kan nu aktiveras för resurser som används i AEM Screens-projektet.

Mer information om hur du kan aktivera målinriktning för resurser i AEM Screens-projektet finns i [ContextHub konfigureras i AEM Screens](configuring-context-hub.md).

När du har konfigurerat ContextHub för ditt AEM Screens-projekt kan du följa olika användningsexempel för att förstå hur datainlösande resurser spelar en viktig roll i olika branscher:

**[Målinställd aktivering för butikslager](retail-inventory-activation.md)**

**[Temperaturaktivering i resecentret](local-temperature-activation.md)**

**[Aktivering av hotellreservation](hospitality-reservation-activation.md)**

* **Förbättringar i uppdateringshanterare**

Uppdateringshanteraren tolkar nu upplevelsefragmenten och samlar in alla bilder, videoklipp och produkter som är kopplade till dem.

* **Startar**

Med det här alternativet kan innehållsförfattare skapa framtida versioner av kanalerna. Med hjälp av Launches kan författarna förhandsgranska varje kanal i lanseringen och bör kunna initiera en begäran om granskning. Godkännargruppen får meddelanden och kan godkänna eller avvisa begäran. När live-datumet nås spelas innehållet upp på enheterna.
Se [Startar](launches.md) för mer information.

* **Offlinekonfigurationer i Experience Fragments**

Du kan nu lägga till offlinekonfigurationer (klientbibliotek och statiska filer) när du konfigurerar skärmar med Experience Fragment. Se [Använda upplevelsefragment](experience-fragments-in-screens.md) för mer information.

### Släppta AEM Screens-spelare

Följande AEM Screens-spelare finns för AEM 6.4.5 Feature Pack 5 och AEM 6.5.1 Feature Pack 1:

* ChromeOS
* Windows
* Android™

#### AEM Screens Player - nedladdningar

Om du vill hämta den senaste versionen av AEM Screens Player och läsa mer om felkorrigeringarna kan du läsa [AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/).
