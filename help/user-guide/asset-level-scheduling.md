---
title: Aktivering på tillgångsnivå
seo-title: Asset Level Activation
description: Följ den här sidan för att lära dig hur du aktiverar en specifik resurs i en kanal för en schemalagd tidsram i spelarens lokala tidszon.
seo-description: Follow this page to learn how to activate a specific asset in a channel for a scheduled time frame in the player's local timezone.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: 939d078def133e0db0e61ec80167f496c65ade46
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

---

# Aktivering på tillgångsnivå {#asset-level-scheduling}

Den här sidan beskriver resursnivåaktivering för de resurser som används i kanaler.

Följande ämnen behandlas i detta avsnitt:

* Översikt
* Aktiveringsfönster
* Uppspelning av enstaka händelse
* Hantera återkommande i resurser
   * DayParting
   * WeekParting
   * MånadDelning
   * Kombination av partner
* Aktivering av flera resurser
* Global åsidosättning för universell starttid

>[!CAUTION]
>
>Denna AEM Screens-funktionalitet är endast tillgänglig om du har installerat AEM 6.3 Feature Pack 3 eller AEM 6.4 Screens Feature Pack 1.
>
>Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

## Översikt {#overview}

***Aktivering på tillgångsnivå*** kan du aktivera en viss resurs i en kanal för en schemalagd tidsram i spelarens lokala tidszon. Detta är tillgängligt för bilder, videoklipp, övergångar, sidor och inbäddade kanaler (dynamiska eller statiska).

*Till exempel* vill du att en specialkampanj bara ska visas under en glad timme (2:00 till 17:00) på måndagar och onsdagar.

Med den här funktionen kan du inte bara ange start- och slutdatum och sluttid utan även ett upprepningsmönster.

## Aktiveringsfönster {#single-event-playback}

Aktivering på tillgångsnivå görs genom att konfigurera **Aktivering** när du får åtkomst till egenskaper för en resurs.

Följ stegen nedan för att utföra planering på tillgångsnivå:

1. Välj valfri kanal och klicka på **Redigera** från åtgärdsfältet för att lägga till eller redigera innehåll i kanalen.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Mer information om hur du
   >
   >* Skapa ett projekt, se [Skapa ett nytt projekt](creating-a-screens-project.md).
   >* Skapa och lägga till innehåll i en kanal, se [Hantera kanaler](managing-channels.md).


1. Klicka **Redigera** för att öppna kanalredigeraren och välja en resurs som du vill använda schemaläggningen på.

   ![bild](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Markera resursen och klicka på uppe till vänster **Konfigurera** (skiftnyckelsikon) om du vill öppna bildens egenskaper.

   Klicka på **Aktivering** -fliken.

   ![bild](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Du kan ange datumet från datumväljaren med **Aktiv från** och **Aktiv tills** fält.

   Om du väljer **Aktiv från** och **Aktiv tills** datum och tid, kommer resursen endast att visas och slingras mellan startdatum/tid respektive slutdatum/tid.

   ![bild](/help/user-guide/assets/asset-activation/asset-level3.png)

## Hantera återkommande i resurser {#handling-recurrence-in-assets}

Du kan schemalägga att mediefiler ska återkomma med vissa intervall på daglig, veckovis eller månadsbasis efter behov.

Anta att du bara vill visa en bild på fredag från 1:00 till 10:00. Du kan använda **Aktivering** för att ange önskat återkommande intervall för resursen.

### Dag-parsning {#day-parting}

1. Markera resursen och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet på dag och tid.

#### Exempeluttryck för dagdelning {#example-one}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08:00 | resursen i kanalen spelas upp innan klockan åtta varje dag |
| efter klockan 2:00 | resursen i kanalen spelas upp efter klockan 17:00 varje dag |
| efter 12:15 och före 12:45 | resursen i kanalen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | resursen i kanalen spelas upp före kl. 12.15 varje dag och även efter kl. 12.45 |


>[!NOTE]
>
>Du kan också använda _militär tid_ notation (d.v.s. 14:00) i stället för *fm/em* notation (d.v.s. 2:00).

### WeekParting {#week-parting}

1. Markera resursen och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet på dag och tid.

#### Exempeluttryck för WeekParting {#example-two}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| Mån,Vind,Fre | mediefilen spelas upp i kanalen från måndag, onsdag och fredag |
| mån-Thu | resursen spelas upp i kanalen från måndagar till torsdagar |

>[!NOTE]
>
>Du kan också använda _full_ (dvs. måndag, onsdag, fredag) i stället för _kort_ notation (d.v.s. Mon, Wed, Fri).


### MånadDelning {#month-parting}

1. Markera resursen och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet på dag och tid.

#### Exempeluttryck för MonthParting {#example-three}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| februari,maj,augusti,november | mediefilen spelas upp i februari, maj, augusti och november |
| februari-juli | tillgången spelas upp i kanalen från februari hela tiden fram till slutet av juli |

>[!NOTE]
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari.

### Kombination av partner {#combined-parting}

1. Markera resursen och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan Egenskaper.

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet på dag och tid.

#### Exempeluttryck för en kombination av partner {#example-four}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| efter 6:00 och före 18:00 i Mon, Wed of Jan-Mar | tillgången spelas upp i kanalen mellan kl. 6.00 och kl. 18.00 måndag och onsdag från januari till slutet av mars |
| den första dagen i januari efter kl. 2:00 också den andra dagen i januari, även den tredje dagen i januari före kl. 3:00 | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| den 1-2 januari efter kl. 2:00 också den 2-3 januari före kl. 3:00 | resursen i kanalen startar spelaren efter kl. 2:00 den 1 januari, fortsätter att spelas upp till kl. 17:00 den 2 januari och börjar igen kl. 2:00 och fortsätter att spelas upp till kl. 3:00 den 3 januari |

>[!NOTE]
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari.  Du kan även använda _militär tid_ notation (d.v.s. 14:00) i stället för *fm/em* notation (d.v.s. 2:00).


## Aktivering av flera resurser {#multi-asset-scheduling}

>[!CAUTION]
>
>The **Aktivering av flera resurser** finns bara om du har AEM 6.3 Feature Pack 5 eller AEM 6.4 Feature Pack 3.

***Aktivering av flera resurser*** gör att användaren kan välja flera resurser och tillämpa ett uppspelningsschema på alla markerade resurser.

### Förutsättningar {#prerequisites}

Skapa ett AEM Screens-projekt med en sekvenskanal om du vill använda multimedieaktivering för dina resurser. I följande exempel visas implementeringen av funktionen:

* Skapa ett AEM Screens-projekt med namnet **MultiAssetDemo**
* Skapa en kanal med namnet som **MultiAssetChannel** och lägga till innehåll i kanalen enligt bilden nedan

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Följ stegen nedan för att välja flera resurser och schemalägga hur de ska visas i ett AEM Screens-projekt:

1. Välj **MultiAssetChannel** och klicka **Redigera** i åtgärdsfältet för att öppna redigeraren.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Markera flera resurser i redigeraren och klicka på **Redigera aktivering** (ikon längst upp till vänster).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Välj datum och tid i **Aktiv från** och **Aktiv tills** från **Komponentaktivering** -dialogrutan. Klicka på bockmarkeringsikonen när du är klar med att välja scheman.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Klicka på Uppdatera för att kontrollera de resurser som används i ett schema för flera resurser.

   >[!NOTE]
   >
   >Schemaikonen visas i det övre högra hörnet för resurser som har aktivering av flera resurser.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Global åsidosättning för universell starttid {#global-override-scheduling}

***Global åsidosättning för universell starttid***, är en inställning som gör det möjligt för innehållsförfattaren att definiera uppspelningen av en bild eller videoklipp baserat på en viss tid. Inställningen time/timezone för en enskild spelare används inte.

I vanliga fall bestäms uppspelningen av den lokala tiden för en viss spelare, men med den globala åsidosättningen kan en specifik universell starttid användas för att initiera uppspelningen av resursen.

Detta gör att innehållsförfattaren kan ange att uppspelning av en viss resurs ska ske vid ett visst datum/tid, oavsett lokal klocka för alla spelare som har det tilldelade innehållet.

Global åsidosättning för universell starttid görs genom att konfigurera **Aktivering** när du får åtkomst till egenskaper för en resurs. Följ stegen nedan för att utföra en global åsidosättning för tillgångsplanering:

1. Välj valfri kanal och klicka på **Redigera** från åtgärdsfältet för att lägga till eller redigera innehåll i kanalen.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Klicka **Redigera** för att öppna kanalredigeraren och välja en resurs som du vill använda schemaläggningen på.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. För en global åsidosättning anger du aktiveringstiden i **Åsidosättning av tidszon** för resursen. Om du inte anger något i det här området används spelarens tidszon.


