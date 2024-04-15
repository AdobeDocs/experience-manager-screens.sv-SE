---
title: Aktivering på kanalnivå - uppspelning av enstaka händelse
description: Läs om aktivering på kanalnivå med en enda händelseuppspelning.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1769'
ht-degree: 0%

---

# Aktivering på kanalnivå {#channel-level-activation-single-event-playback}

Den här sidan beskriver kanalnivåaktivering för resurserna som används i kanaler.

Följande ämnen behandlas i detta avsnitt:

* Ökning
* Aktiveringsfönster
* Använda kanalnivåaktivering som en enda händelseuppspelning
* Hantera återkommande för resurser i en kanal
   * DayParting
   * WeekParting
   * MånadDelning
   * Kombination av partner
* Använda kanalnivåaktivering som en enda händelseuppspelning

## Ökning {#overview}

***Aktivering på kanalnivå*** gör att kanalerna kan växla efter ett visst angivet schema. Den enskilda händelsekanalen ersätter huvudkanalen efter ett angivet schema och spelas upp en viss tid tills huvudkanalen spelar upp innehållet igen.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* a ***huvudsekvenskanal*** för den globala sekvensen
* a ***single event channel*** som endast körs en gång i en angiven tid
* a ***ange schema och prioritet*** för den enda uppspelningshändelsen som inträffar inuti huvudsekvenskanalen

## Aktiveringsfönster {#using-channel-level-activation}

I följande avsnitt beskrivs hur du skapar en enda händelseuppspelning i en kanal för ett AEM Screens-projekt.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har följande krav klara att börja implementera aktivering på kanalnivå:

* Skapa ett AEM Screens-projekt, i detta exempel **Aktivering på kanalnivå**

* Skapa en kanal som **MainAdChannel** under **Kanaler** mapp

* Skapa en annan kanal som **TargetedSinglePlay** under **Kanaler** mapp

* Lägg till relevanta resurser i båda kanalerna

Följande bild visar **Aktivering på kanalnivå** projekt med **MainAdChannel** och **TargetedSinglePlay** kanaler i **Kanaler** mapp.

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>Mer information om hur du skapar ett projekt och hur du skapar en sekvenskanal finns i följande resurser:
>
>* [Skapa och hantera projekt](creating-a-screens-project.md)
>
>* [Hantera en kanal](managing-channels.md)
>

### Implementering {#implementation}

Implementering av kanalnivåaktivering i ett AEM Screens-projekt innefattar tre viktiga uppgifter:

1. **Konfigurera Project-taxonomin inklusive kanaler, platser och bildskärmar**
1. **Tilldela kanaler att visa**
1. **Konfigurera ett schema och en prioritet**

Följ stegen nedan för att implementera funktionen:

1. **Skapa en plats**

   Navigera till **Platser** i ditt AEM Screens-projekt och skapa en plats som **Län**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa visning under Plats**

   1. Navigera till **Aktivering på kanalnivå** > **Platser** > **Län**.
   1. Välj **Län** och markera **+ Skapa** i åtgärdsfältet.
   1. Välj **Visa** från guiden och skapa en skärm med namnet **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Tilldela kanaler att visa**

   För **Huvudkanal:**

   1. Navigera till **Aktivering på kanalnivå** > **Platser** > **Län** > **RegionDisplay** och markera **Tilldela kanal** i åtgärdsfältet.
   1. **Kanaltilldelning** öppnas.
   1. Välj **Referenskanal** efter bana.
   1. Välj **Kanalsökväg** as **Aktivering på kanalnivå** > ***Kanaler*** > ***MainAdChannel***.
   1. The **Kanalroll** fylls i som **huvudkanal**.
   1. Välj **Prioritet** as **1**.
   1. Välj **Händelser som stöds** as **Inledande inläsning** och **Inaktiv skärm**.
   1. Välj **Spara**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Du kan också tilldela kanal från kontrollpanelen genom att navigera till **Aktivering på kanalnivå** > **Platser** > **Län** > **RegionDisplay** och markera **Kontrollpanel** i åtgärdsfältet. Välj **+ Tilldela kanal** från **TILLDELADE KANALER OCH SCHEMAN** -panelen.

   Tilldela kanal på samma sätt **TargetedSinglePlay** för bildskärm**:

   1. Navigera till **Aktivering på kanalnivå** > **Platser** > **Län** > **RegionDisplay** och markera **Tilldela kanal** i åtgärdsfältet.
   1. **Kanaltilldelning** öppnas.
   1. Välj **Referenskanal** efter bana.
   1. Välj **Kanalsökväg** as **Aktivering på kanalnivå*** > ***Kanaler*** > ***TargetedSinglePlay***.
   1. The **Kanalroll** fylls i som **målsingleplay**.
   1. Ange **Prioritet** as **2**.
   1. Välj **Händelser som stöds** as **Inledande inläsning**, **Inaktiv skärm** och **Timer**, vilket visas i figuren nedan.
   1. Välj datum i **aktiv från** den 27 november 2018 kl. 11:59 och i **aktiv tills** 28 november 2018 12:05
   1. Välj **Spara**.

   >[!CAUTION]
   >
   >Ange prioritet för **TargetedSinglePlay** kanal högre än **MainAdSegment** kanal.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Om du vill välja samma dag väljer du nästa dag och redigerar sedan datumet manuellt till samma dag men för en senare tid. Detta begränsar användaren från att välja ett tidigare datum. Se följande exempel:

   ![new1](assets/new1.gif)

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens-spelaren för att visa innehållet.

Spelaren visar innehållet i **MainAdChannel** och exakt klockan 11:59 (enligt schemat), **TargetedSinglePlay** -kanalen visar innehållet till kl. 12.05 och sedan **MainAdChannel** fortsätter att spela upp innehållet igen.

>[!NOTE]
>
>Mer information om AEM finns i följande resurser:
>[AEM Screens Player - nedladdningar](https://download.macromedia.com/screens/)
>[Arbeta med AEM Screens Player](working-with-screens-player.md)


## Hantera återkommande för resurser i en kanal {#handling-recurrence-in-assets}

Du kan schemalägga att resurser i en kanal återkommer med vissa intervall på varje dag, vecka eller månad, beroende på dina behov.

Anta att du bara vill visa innehållet i en kanal på fredag från 1:00 till 10:00. Du kan använda **Aktivering** för att ange önskat återkommande intervall för resursen.

### Dag-parsning {#day-parting}

1. Markera kanalen och välj sedan **Kontrollpanel** i åtgärdsfältet.

1. Efter att du angett startdatum/tid och sluttid/tid från **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för dagdelning {#example-one}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| före 08.00 | resursen i kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | resursen i kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | mediefilen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | resursen i kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |
| Mån,Tue,Wed eller Mon-Wed | resursen spelas upp i kanalen från måndag till onsdag |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari, den tredje dagen i januari före kl. 17.00. | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00. | resursen i kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>
>Du kan också använda _militär tid_ notation (14:00) i stället för *A.M./P.M.* (2:00).

### WeekParting {#week-parting}

1. Markera kanalen och välj sedan **Kontrollpanel** i åtgärdsfältet.

1. Efter att du angett startdatum/tid och sluttid/tid från **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för WeekParting {#example-two}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| Mån,Tue,Wed eller Mon-Wed | resursen spelas upp i kanalen från måndag till onsdag |
| före 08.00 | resursen i kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | resursen i kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | mediefilen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | Kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |

>[!NOTE]
>
>Du kan också använda _militär tid_ notation (14:00) i stället för *A.M./P.M.* (2:00).


### MånadDelning {#month-parting}

1. Markera kanalen och välj sedan **Kontrollpanel** i åtgärdsfältet.

1. Efter att du angett startdatum/tid och sluttid/tid från **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för MonthParting {#example-three}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| av `February,May,August,November` | mediefilen spelas upp i februari, maj, augusti, november |

>[!NOTE]
>
>När du definierar veckodagar och månader kan du använda både kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari/januari.

>[!NOTE]
>
>Du kan också använda _militär tid_ notation (14:00) i stället för *A.M./P.M.* (2:00).

### Kombination av partner {#combined-parting}

1. Markera kanalen och välj sedan **Kontrollpanel** i åtgärdsfältet.

1. Efter att du angett startdatum/tid och sluttid/tid från **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschema.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med **Aktiv från** och **Aktiv tills** fält och lägg till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **Schema** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för en kombination av partner {#example-four}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| efter kl. 6.00 och före kl. 18.00 på Mån, Wed från januari-mars | tillgången spelas upp i kanalen mellan kl. 6.00 och kl. 18.00 måndag och onsdag från januari till slutet av mars |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari, den tredje dagen i januari före kl. 17.00. | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00. | resursen i kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari. Du kan även använda _militär tid_ notation (14:00) i stället för *A.M./P.M.* (2:00).
