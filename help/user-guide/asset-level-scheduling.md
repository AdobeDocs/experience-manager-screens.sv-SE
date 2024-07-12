---
title: Aktivering på tillgångsnivå
description: Lär dig hur du aktiverar en viss resurs i en kanal för en schemalagd tidsram, allt inom spelarens lokala tidszon.
feature: Authoring Screens, Asset Level Activation
role: Admin, Developer
level: Intermediate
exl-id: a2f5b2cc-6797-4397-b49c-72175a2d2ef7
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 0%

---

# Aktivering på tillgångsnivå {#asset-level-scheduling}

Den här sidan beskriver resursnivåaktivering för de resurser som används i kanaler.

Följande ämnen behandlas i detta avsnitt:

* Ökning
* Aktiveringsfönster
* Uppspelning av enstaka händelse
* Hantera upprepning i Assets
   * DayParting
   * WeekParting
   * MånadDelning
   * Kombination av partner
* Aktivering av flera resurser
* Global åsidosättning för universell starttid

<!-- REFERS TO ARCHIVED VERSIONS THAT ADOBE NO LONGER SUPPORTS>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permission, you can download it from Package Share. -->

## Ökning {#overview}

Med ***Aktivering på resursnivå*** kan du aktivera en specifik resurs i en kanal för en schemalagd tidsram, allt inom spelarens lokala tidszon. Den här funktionen är tillgänglig för bilder, videoklipp, övergångar, sidor och inbäddade kanaler (dynamiska eller statiska).

*Du vill till exempel att en specialkampanj endast ska visas under en glad timme (2:00 till 5:00) på måndagar och onsdagar.*

Med den här funktionen kan du inte bara ange start- och slutdatum och sluttid utan även ett upprepningsmönster.

## Aktiveringsfönster {#single-event-playback}

Aktivering på tillgångsnivå görs genom att fliken **Aktivering** konfigureras medan egenskaperna för en resurs nås.

Följ stegen nedan för att utföra planering på tillgångsnivå:

1. Klicka på en kanal och sedan på **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

   >[!NOTE]
   >
   >Lär dig mer om hur man
   >
   >* Skapa ett projekt. Se [Skapa ett nytt projekt](creating-a-screens-project.md).
   >* Skapa och lägga till innehåll i en kanal. Se [Hantera kanaler](managing-channels.md).

1. Klicka på **Redigera** så att du kan öppna kanalredigeraren och klicka på en resurs som du vill använda schemaläggningen på.

   ![bild](/help/user-guide/assets/asset-activation/asset-level2.png)

1. Klicka på resursen och sedan på **Konfigurera** (skiftnyckelsikon) överst till vänster.

   Klicka på fliken **Aktivering**.

   ![bild](/help/user-guide/assets/asset-activation/asset-level3.png)

1. Du kan ange datumet från datumväljaren med fälten **Aktiv från** och **Aktiv till**.

   Om du klickar på datumet och tiden **Aktiv från** och **Aktiv till** visas och spelas endast upp mellan startdatumet/tiden och slutdatumet/tiden.

   ![bild](/help/user-guide/assets/asset-activation/asset-level3.png)

## Hantera upprepning i Assets {#handling-recurrence-in-assets}

Du kan schemalägga att resurser ska återkomma med vissa intervall på en daglig, veckovis eller månadsbasis beroende på dina behov.

Anta att du bara vill visa en bild på fredag från 1:00 till 10:00. Du kan använda fliken **Aktivering** för att ange önskat intervall för resursen.

### Dag-parsning {#day-parting}

1. Klicka på resursen och klicka på **Konfigurera** (skiftnyckelsikon) för att öppna dialogrutan för egenskaper.

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för dagdelning {#example-one}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08.00 | resursen i kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | resursen i kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | mediefilen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | resursen i kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |

>[!NOTE]
>
>Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).

### WeekParting {#week-parting}

1. Klicka på resursen och sedan på **Konfigurera** (skiftnyckelsikon).

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för WeekParting {#example-two}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| `Mon,Wed,Fri` | mediefilen spelas upp i kanalen från måndag, onsdag och fredag |
| `Mon-Thu` | resursen spelas upp i kanalen från måndagar till torsdagar |

>[!NOTE]
>
>Du kan också använda _full_-notation (`Monday,Wednesday,Friday`) i stället för _short_ (`Mon,Wed,Fri`).


### MånadDelning {#month-parting}

1. Klicka på resursen och sedan på **Konfigurera** (skiftnyckelsikon).

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för MonthParting {#example-three}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| `on February,May,August,November` | mediefilen spelas upp i februari, maj, augusti och november |
| `on February-July` | tillgången spelas upp i kanalen från februari till slutet av juli |

>[!NOTE]
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari.

### Kombination av partner {#combined-parting}

1. Klicka på resursen och sedan på **Konfigurera** (skiftnyckelsikon).

1. När du har angett startdatum/tid och slutdatum/tid kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för en kombination av partner {#example-four}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| `after 6:00 and before 18:00 on Mon,Wed of Jan-Mar` | tillgången spelas upp i kanalen mellan kl. 18.00 och kl. 18.00 måndag och onsdag från januari till slutet av mars |
| `on the 1st day of January after 2:00 P.M. also on the 2nd day of January also on the 3rd day of January before 3:00 A.M.` | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| `on the 1-2 days of January after 2:00 P.M. also on the 2-3 days of January before 3:00 A.M.` | resursen i kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari. Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.*(2:00 P.M.).


## Aktivering av flera resurser {#multi-asset-scheduling}

<!--
>[!CAUTION]
>
>The **Multi-asset Activation** feature is only available if you have installed AEM 6.3 Feature Pack 5 or AEM 6.4 Feature Pack 3. -->

***Aktivering av flera resurser*** gör att användaren kan klicka på flera resurser och tillämpa ett uppspelningsschema för alla markerade resurser.

### Förutsättningar {#prerequisites}

Skapa ett AEM Screens-projekt med en sekvenskanal om du vill använda multimedieaktivering för dina resurser. I följande exempel visas implementeringen av funktionen:

* Skapa ett AEM Screens-projekt med namnet **MultiAssetDemo**.
* Skapa en kanal med namnet **MultiAssetChannel** och lägg till innehåll i kanalen, enligt bilden nedan.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Följ stegen nedan för att klicka på flera resurser och schemalägga hur de ska visas i ett AEM Screens-projekt:

1. Klicka på **MultiAssetChannel** och sedan på **Redigera** i åtgärdsfältet.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Klicka på flera resurser i redigeraren och klicka sedan på **Redigera aktivering** (ikonen längst upp till vänster).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Klicka på datumet och tiden i **Aktiv från** och **Aktiv tills** i dialogrutan **Komponentaktivering**. Klicka på bockmarkeringsikonen när du är klar med att välja scheman.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Klicka på Uppdatera för att kontrollera de resurser som du vill använda schemat för flera resurser på.

   >[!NOTE]
   >
   >Schemaikonen visas i det övre högra hörnet för de resurser som har aktivering av flera resurser.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

## Global åsidosättning för universell starttid {#global-override-scheduling}

***Global åsidosättning för universell starttid*** är en inställning som gör att innehållsförfattaren kan definiera uppspelningen av en bild eller videoresurs baserat på en viss tid. Inställningen för tid/tidszon för en enskild spelare används inte.

Normalt avgör den lokala tiden för en viss spelare uppspelningen. Men med den globala åsidosättningen kan en specifik universell starttid användas för att initiera uppspelningen av resursen.

Därför kan innehållsförfattaren definiera uppspelning av en viss resurs. De kan ha den vid ett specifikt datum/tid, oavsett lokal klocka, på alla spelare som har det tilldelade innehållet.

***Global åsidosättning för universell starttid*** görs genom att fliken **Aktivering** konfigureras medan egenskaper för en resurs nås. Följ stegen nedan för att utföra en global åsidosättning för resursplanering:

1. Klicka på en kanal och klicka sedan på **Redigera** i åtgärdsfältet så att du kan lägga till eller redigera innehåll i kanalen.

   ![screen_shot_2018-04-23at11422am](/help/user-guide/assets/asset-activation/asset-level1.png)

1. Klicka på **Redigera**.
1. Klicka på en resurs vars schema du vill använda i kanalredigeraren.

   ![screen_shot_2018-12-21at70550am](/help/user-guide/assets/asset-activation/Asset-level4.png)

1. Om du vill åsidosätta globalt anger du aktiveringstiden i avsnittet **Åsidosätt tidszon** för resursen. Om du inte anger något i det här området används spelarens tidszon.


