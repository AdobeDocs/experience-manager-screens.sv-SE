---
title: Installera skärmuppspelaren
description: Lär dig hur du installerar en AEM Screens Player på rätt sätt.
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Installera AEM Screens Player {#installing-player}

På den här sidan beskrivs hur du installerar AEM Screens Player.

## Tillgänglig skärmspelare {#available-players}

AEM Screens Player finns för Android™, Chrome OS och Windows.

För nedladdning **AEM Screens Player**, går till [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) sida.

>[!NOTE]
>
>När du har laddat ned den senaste spelaren (*.exe*) följer du stegen på spelaren så att du kan slutföra ad hoc-installationen:
>
>1. Tryck länge på det övre vänstra hörnet för att öppna administratörspanelen.
>1. Navigera till **Konfiguration** från den vänstra åtgärdsmenyn och ange platsadressen för AEM i **Server** och markera **Spara**.
>1. Välj **Registrering** från den vänstra åtgärdsmenyn och stegen nedan för att slutföra enhetsregistreringsprocessen.

## Grundläggande uppspelningsövervakning {#playback-monitoring}

Spelaren rapporterar olika uppspelningsmått för varje `ping` som standard är 30 sekunder. Baserat på dessa mått kan programmet identifiera olika kantfall, t.ex. problem med fastsittning, tomma skärmar och schemaläggning. Detta gör att vi kan förstå och felsöka problem på enheten och därmed underlätta en utredning och korrigerande åtgärder med dig.

Med grundläggande uppspelningsövervakning i en AEM Screens-spelare kan du göra följande:

* Fjärrövervaka om en spelare spelar upp innehållet korrekt.

* Förbättra reaktiviteten till tomma skärmar eller trasiga upplevelser på fältet.

* Minskar risken för att slutanvändaren får en trasig upplevelse.

### Förstå egenskaper {#understand-properties}

Följande egenskaper ingår i varje `ping`:

| Egenskap | Beskrivning |
|---|---|
| id {string} | spelarens identifierare |
| activeChannel {string} | spelar upp kanalsökvägen eller null om inget är schemalagt |
| activeElements {string} | kommaavgränsade strängar, för närvarande synliga element i alla uppspelningskanaler (flera i det finns en layout med flera zoner) |
| isDefaultContent {boolean} | true om den spelande kanalen betraktas som en standard- eller reservkanal (d.v.s. har prioritet 1 och inget schema) |
| hasContentChanged {boolean} | true om innehållet har ändrats under de senaste fem minuterna, annars false |
| lastContentChange {string} | tidsstämpel för den senaste innehållsändringen |

>[!NOTE]
>Om du vill kan du aktivera en mer avancerad egenskap från spelarens inställningar (Aktivera övervakning av uppspelning). Det vill säga:
>
>| Egenskap | Beskrivning |
>|---|---|
>| isContentRendering {boolean} | true om grafikprocessorn kan bekräfta att det spelar upp faktiskt innehåll (baserat på pixelanalys) |

### Begränsningar {#limitations}

Några begränsningar för grundläggande uppspelningsövervakning visas nedan:

* Spelaren rapporterar ett eget uppspelningsläge till servern, vilket kräver en aktiv anslutning.

* The `isContentRendering` som kontrollerar att grafikprocessorn är för resurskrävande för att aktiveras som standard och kräver explicit deltagande från spelarens inställningar. Adobe rekommenderar att du inte använder den med videofilmer i produktion.

* Den här funktionen stöds bara för sekvenskanaler och täcker ännu inte de interaktiva kanalernas (SPA) användningsfall.

* Måtten är ännu inte helt exponerade för kunderna. Adobe arbetar på att aktivera kontrollpanelsliknande rapporterings- och varningsmekanismer snart.

### Andra resurser {#additional-resources}

Mer information finns i följande avsnitt:

* Ladda ned Android™ Player på **Google Play**. Mer information om hur du implementerar Android™-övervakning finns i [Implementera Android™-spelare](implementing-android-player.md).

* Information om hur du implementerar Chrome OS Player finns i [Chrome Management Console](implementing-chrome-os-player.md) för mer information.

* Information om hur du konfigurerar AEM Screens Windows Player finns i [Implementera Windows Player](implementing-windows-player.md).
