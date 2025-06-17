---
title: Aktivering på kanalnivå - uppspelning av enstaka händelse
description: Läs om aktivering på kanalnivå med en enda händelseuppspelning.
topic-tags: authoring
feature: Authoring Screens, Channels
role: Admin, Developer
level: Intermediate
exl-id: 51a63429-2488-45be-b8f5-cb755ca69c7f
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1791'
ht-degree: 0%

---

# Aktivering på kanalnivå {#channel-level-activation-single-event-playback}

Den här sidan beskriver kanalnivåaktivering för resurserna som används i kanaler.

Följande ämnen behandlas i detta avsnitt:

* Ökning
* Aktiveringsfönster
* Använda kanalnivåaktivering som en enda händelseuppspelning
* Hantera återkommande för Assets i en kanal
   * DayParting
   * WeekParting
   * MånadDelning
   * Kombination av partner
* Använda kanalnivåaktivering som en enda händelseuppspelning

## Ökning {#overview}

***Kanalnivåaktivering*** tillåter kanalerna att växla efter ett visst angivet schema. Den enskilda händelsekanalen ersätter huvudkanalen efter ett angivet schema och spelas upp en viss tid tills huvudkanalen spelar upp innehållet igen.

I följande exempel får du en lösning genom att fokusera på följande nyckeltermer:

* en ***huvudsekvenskanal*** för den globala sekvensen
* en ***enskild händelsekanal*** som bara körs en gång i taget
* en ***ange schema och prioritet*** för den enda uppspelningshändelse som inträffar inuti huvudsekvenskanalen

## Aktiveringsfönster {#using-channel-level-activation}

I följande avsnitt beskrivs hur du skapar en enda händelseuppspelning i en kanal för ett AEM Screens-projekt.

### Förutsättningar {#prerequisites}

Innan du börjar implementera den här funktionen bör du kontrollera att du har följande krav klara att börja implementera aktivering på kanalnivå:

* Skapa ett AEM Screens-projekt, i det här exemplet **Kanalnivåaktivering**.

* Skapa en kanal som **MainAdChannel** under mappen **Kanaler**.

* Skapa en annan kanal som **TargetedSinglePlay** under mappen **Kanaler**.

* Lägg till relevanta resurser i båda kanalerna.

Följande bild visar **kanalnivåaktiveringsprojektet** med kanalerna **MainAdChannel** och **TargetedSinglePlay** i mappen **Channel** .

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

1. **Konfigurerar Project-taxonomin inklusive kanaler, platser och skärmar**
1. **Tilldelar kanaler till visning**
1. **Konfigurera ett schema och en prioritet**

Följ stegen nedan för att implementera funktionen:

1. **Skapa en plats**

   Navigera till mappen **Platser** i ditt AEM Screens-projekt och skapa en plats som **Region**.

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >Mer information om hur du skapar en plats finns i **[Skapa och hantera platser](managing-locations.md)**.

1. **Skapa visning under plats**

   1. Navigera till **Kanalnivåaktivering** > **Platser** > **Region**.
   1. Klicka på **Region** och klicka på **+ Skapa** i åtgärdsfältet.
   1. Klicka på **Visning** i guiden och skapa en visning med namnet **RegionDisplay.**

   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **Tilldela kanaler att visa**

   För **MainAdChannel:**

   1. Navigera till **Kanalnivåaktivering** > **Platser** > **Region** > **RegionDisplay** och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. Klicka på **Referenskanal** efter sökväg i dialogrutan **Kanaltilldelning**.
   1. Klicka på **kanalsökvägen** och sedan på **Aktivering på kanalnivå** > ***Kanaler*** > ***MainAdChannel***.
   1. **Kanalrollen** fylls i som **huvudkanal**.
   1. Klicka på **Prioritet** och ange **1**.
   1. Klicka på **Händelser som stöds**, till exempel **Inledande inläsning** och **Inaktiv skärm**.
   1. Klicka på **Spara**.

   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >Du kan också tilldela kanalen från kontrollpanelen. Navigera till **Kanalnivåaktivering** > **Platser** > **Region** > **RegionDisplay**. Välj **Instrumentpanel** i åtgärdsfältet. Klicka på **+ Tilldela kanal** på panelen **TILLDELADE KANALER &amp; SCHEMAT**.

   Tilldela på liknande sätt kanalen **TargetedSinglePlay** för visning**:

   1. Navigera till **Kanalnivåaktivering** > **Platser** > **Region** > **RegionDisplay** och klicka på **Tilldela kanal** i åtgärdsfältet.
   1. Klicka på **Referenskanal** efter sökväg i dialogrutan **Kanaltilldelning**.
   1. Klicka på **kanalsökvägen** och sedan på **Aktivering på kanalnivå** > ***Kanaler*** > ***TargetedSinglePlay***.
   1. **Kanalrollen** fylls i som **målsinglePlay**.
   1. Ange **Prioritet** till **2**.
   1. Klicka på **Händelser som stöds** och ange **Inledande inläsning**, **Inaktivitetsskärm** och **Timer** enligt bilden nedan.
   1. I **active from**, set as November 27, 2018, 11:59 P.M., and in **active until**, set as November 28, 2018, 12:05 A.M.
   1. Klicka på **Spara**.

   >[!CAUTION]
   >
   >Ange prioriteten för kanalen **TargetedSinglePlay** som är högre än **MainAdSegment** -kanalen.

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   >
   >Om du vill välja samma dag klickar du på nästa dag och redigerar sedan datumet manuellt till samma dag men för en senare tid. Detta begränsar användaren från att välja ett tidigare datum. Se följande exempel:

   ![new1](assets/new1.gif)

## Visa resultaten {#viewing-the-results}

När du har konfigurerat kanalerna och visningen är klar startar du AEM Screens Player för att visa innehållet.

Spelaren visar innehållet i **MainAdChannel** och exakt vid 11:59 P.M. (enligt schemat), visar **TargetSinglePlay** -kanalen innehållet till 12.05 och sedan fortsätter **MainAdChannel** att spela upp innehållet igen.

>[!NOTE]
>
>Mer information om AEM Screen Player finns i följande resurser:
>&#x200B;>[AEM Screens Player-nedladdningar](https://download.macromedia.com/screens/)
>&#x200B;>[Arbeta med AEM Screens Player](working-with-screens-player.md)


## Hantera återkommande för Assets i en kanal {#handling-recurrence-in-assets}

Du kan schemalägga att resurser i en kanal återkommer med vissa intervall, varje dag, varje vecka eller varje månad beroende på dina behov.

Anta att du bara vill visa innehållet i en kanal på fredag från 1:00 till 10:00. Du kan använda fliken **Aktivering** för att ange önskat intervall för resursen.

### Dag-parsning {#day-parting}

1. Klicka på kanalen och sedan på **Kontrollpanel** i åtgärdsfältet.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >
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
| Mån,Tue,Wed eller Mon-Wed | resursen spelas upp i kanalen från måndag till onsdag |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari samt den tredje dagen i januari före kl. 3.00. | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00. | resursen i kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>
>Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).

### WeekParting {#week-parting}

1. Klicka på kanalen och sedan på **Kontrollpanel** i åtgärdsfältet.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för WeekParting {#example-two}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| Mån,Tue,Wed eller Mon-Wed | resursen spelas upp i kanalen från måndag till onsdag |
| före 08.00 | resursen i kanalen spelas upp före 08.00 varje dag |
| efter kl. 2:00. | resursen i kanalen spelas upp efter kl. 2.00 varje dag |
| efter 12:15 och före 12:45 | mediefilen spelas upp efter kl. 12.15 varje dag i 30 minuter |
| före 12:15 även efter 12:45 | Kanalen spelas upp före kl. 12.15 varje dag och sedan även efter kl. 12.45. |

>[!NOTE]
>
>Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).


### MånadDelning {#month-parting}

1. Klicka på kanalen och sedan på **Kontrollpanel** i åtgärdsfältet.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för MonthParting {#example-three}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| av `February,May,August,November` | mediefilen spelas upp i februari, maj, augusti, november |

>[!NOTE]
>
>När du definierar veckodagar och månader kan du använda både kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari/januari.

>[!NOTE]
>
>Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).

### Kombination av partner {#combined-parting}

1. Klicka på kanalen och sedan på **Kontrollpanel** i åtgärdsfältet.

1. När du har angett startdatum/tid och slutdatum/tid i dialogrutan **Kanaltilldelning** kan du använda ett uttryck eller en naturlig textversion för att ange upprepningsschemat.

   >[!NOTE]
   >
   >Du kan hoppa över eller ta med fälten **Aktiv från** och **Aktiv tills** och lägga till uttrycket i fältet Scheman enligt dina önskemål.

1. Ange uttrycket i **schemat** och resursen visas för det angivna intervallet för dag och tid.

#### Exempeluttryck för en kombination av partner {#example-four}

I följande tabell sammanfattas några exempeluttryck som du kan lägga till i schemat när du tilldelar en kanal till en visning.

| **Uttryck** | **Tolkning** |
|---|---|
| efter kl. 6.00 och före kl. 18.00 på Mån, Wed från januari-mars | tillgången spelas upp i kanalen mellan kl. 18.00 och kl. 18.00 måndag och onsdag från januari till slutet av mars |
| den första dagen i januari efter kl. 2.00, även den andra dagen i januari samt den tredje dagen i januari före kl. 3.00. | resursen i kanalen börjar spelas upp efter kl. 2:00 den 1 januari och fortsätter att spela för hela dagen den 2 januari ända till kl. 3:00 den 3 januari |
| 1-2 dagar i januari efter kl. 2:00 också 2-3 dagar i januari före kl. 3:00. | resursen i kanalen startar spelaren efter kl. 17.00 den 1 januari, fortsätter att spelas upp till kl. 17.00 den 2 januari, börjar den igen kl. 2:00 och fortsätter att spela fram till kl. 17.00 den 3 januari |

>[!NOTE]
>
>När du definierar veckodagar och månader kan du både använda kort- och fullnamnsnoteringar, till exempel måndag/måndag och januari. Du kan också använda _militär tid_-notation (14:00) i stället för *A.M./P.M.* (2:00 P.M.).
