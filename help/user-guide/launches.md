---
title: Content Update using Screens Launch
seo-title: Content Update using Screens Launch
description: Innehållsförfattare kan skapa framtida versioner av kanalerna, så kallade Launch och ange live-datum för den här starten, så att innehållet kan visas på enheter och spelare.
seo-description: Innehållsförfattare kan skapa framtida versioner av kanalerna, så kallade Launch och ange live-datum för den här starten, så att innehållet kan visas på enheter och spelare.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: redigeringsskärmar, startprogram
role: Administratör, utvecklare
level: Mellanliggande
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 0%

---


# Innehållsuppdatering med skärmstart {#launches}

Innehållsförfattare kan skapa framtida versioner av kanalen/kanalerna, så kallade **Screens Launch** och ange live-datumet för den här starten ytterligare. Detta gör att innehållet kan vara live i enheter eller spelare på angivet live-datum.

Med hjälp av ***Screens Launch*** kan författare förhandsgranska varje kanal i starten och bör kunna initiera en granskningsbegäran. Godkännargruppen får meddelanden och kan godkänna eller avvisa begäran. När live-datumet nås spelas innehållet upp på enheterna.

Om författaren till exempel vill skapa framtida versioner av c1, c2 (kanaler) skapas en start och ett live-datum ställs in (till exempel 10 november 8:00). Ytterligare uppdateringar skickas ut för granskning.

När den har godkänts och på live-datumet (10 november 08:00) spelas innehållet upp på enheterna eller spelarna.

## Krav {#requirements}

Innan du börjar använda *Skärmstart* i ett AEM Screens-projekt måste du förstå begreppet respitperiod och dess relevans.

När du kör en upplevelse på det angivna live-datumet på spelaren ingår följande:

* befordran av startprogrammet (tar normalt några sekunder)

* publicera resurser för att publicera instanser (tar vanligtvis några minuter, beroende på kanalernas eller resursernas storlek som behöver publiceras)

* den tid det tar att uppdatera offlineinnehållet (tar normalt några minuter)

* den tid det tar för spelarna att hämta innehållet från publiceringsinstansen (tar vanligtvis minuter beroende på bandbredden och storleken på resurserna som behöver hämtas)

* vid olika tidpunkter på servern och spelaren

### Om giltighetsperiod {#understanding-grace-period}

För att spelaren ska kunna börja spela upp innehållet på angivet live-datum måste föregående aktiviteter startas före live-datumet.

Om live-datumet är *24 november, 9:00* och respitperioden är *24 timmar*, startar ovanstående åtgärdssekvens (live-datum - respitperiod), dvs. 23 november, 9:00-servertid. Detta ger 24 timmar på sig att slutföra alla de ovannämnda åtgärderna och innehållet kommer att nå fram till aktörerna. Spelarna kommer att förstå att det här är ett startinnehåll, så innehållet spelas inte upp direkt, men spelarna kommer att lagra innehållet som en framtida version och börja spela upp exakt på det angivna direktdatumet i spelarens tidszon.

Exempel: servern är i PST och enheterna är i EST, den maximala tidsskillnaden är 3 timmar i det här fallet och förutsätter att erbjudandet tar 1 minut och att publiceringen tar 10 minuter att publicera och spelaren kan hämta resurserna i vanliga fall på 10-15 minuter. Fristen = tidsskillnad (3 timmar) + tid för att starta programmet (1 min) + tid för att publicera starten (10 min) + tid för nedladdning vid spelaren (10-15 min) + buffert (för att vara säker, till exempel 30 min) = 3 timmar 56 min = 14 160 sekunder.

Så när vi schemalägger en livesändning börjar kampanjen tidigt med den här förskjutningen. I ekvationen ovan tar de flesta objekten inte så lång tid. Vi kan använda en bra gissning för den här förskjutningen när vi vet den maximala tidsskillnaden mellan servern och valfri spelare.

>[!NOTE]
>
>Körklar är respitperioden för Screens Launch inställd på 24 timmar, vilket innebär att när vi ställer in livedatum för alla starter för resurserna under */content/screens* så börjar kampanjen med den här förskjutningen.

### Uppdaterar den körklara giltighetsperioden {#updating-out-of-the-box-grace-period}

I det här avsnittet beskrivs hur du kan uppdatera en körklar respitperiod till 10 minuter.

1. Navigera till CRXDE Lite och sedan till `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Högerklicka och kopiera filen.
3. Navigera till `/apps/system/config` och högerklicka och klistra in.
4. Dubbelklicka på `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` för att öppna filen i redigeraren i CRXDE Lite. Den måste visa respitperioden för sökvägen */content/screens/* som **86400**. Ändra det värdet till **600**.

Nu bör innehållet i textfilen se ut ungefär så här:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Eftersom du har angett Respitperiod till 10 minuter i föregående exempel, och du anger ett direktdatum för alla starter för resurserna under */content/screens*, börjar kampanjen med den här förskjutningen.

Om till exempel live-datumet är inställt på 24 november, 9:00 och respitperioden är 600 sekunder börjar kampanjjobbet den 24 november kl. 8:50.

## Använda skärmstart {#using-launches}

I det här avsnittet visas hur du implementerar Screens Launch i ditt AEM Screens-projekt.

### Skapa en skärmstart {#creating-a-launch}

Följ stegen nedan för att implementera funktionen Screens Launch i ditt AEM Screens-projekt:

1. Skapa en sekvenskanal i ditt AEM Screens-projekt, till exempel **LaunchesDemo** —> **Channels** —> **FutureLaunch**, enligt nedan.

   >[!CAUTION]
   >
   >Du måste skapa en lansering från en befintlig kanal i ditt AEM Screens-projekt.

   ![Bild](/help/user-guide/assets/launches-images/launches-11.png)

1. Markera kanalen **FutureLaunch** och klicka på **Create Launch** i åtgärdsfältet.

   ![Bild](/help/user-guide/assets/launches-images/launches-12.png)

1. Guiden **Create Launch** öppnas. Du kan antingen välja den kanal som redan är synlig i guiden eller klicka på **+ Lägg till kanaler** för att lägga till den kanal som du vill starta starten för.

1. Klicka på **Nästa** i guiden **Create Launch**. Alternativet **Inkludera undersidor** är markerat som standard.

   ![bild](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Du kan använda alternativet **+ Lägg till kanaler** för att lägga till en annan kanal som du vill skapa startprogrammet för.

   Om du vill använda alternativet **Lägg till kanaler**, navigerar du till den kanal som du vill starta för och klickar på **Välj**.

   Alternativet **Välj** inaktiveras om du försöker markera flera kanaler eller en mapp för att lägga till starten.

   ![bild](/help/user-guide/assets/launches-images/launches-14.png)

   När du har markerat kanalen/kanalerna klickar du på **Nästa**.


1. Ange **starttitel** som **Sommarkampanjer** och du behöver inte ange **startdatum** enligt bilden nedan. Klicka på **Skapa**.

   >[!NOTE]
   >
   >*Om du aktiverar eller* kontrollerar alternativet  **Ärv källsidans live-** data kan kanalerna skapas som live-kopior vid starten. Om några ändringar görs i den ursprungliga kanalen tillämpas dessa ändringar automatiskt på startkanaler.
   >
   >
   >*Inaktivera eller* **** avmarkeraInherit-källsidans livedata gör att kanalerna kan kopieras utan någon live-relation vid start. Så om ändringar görs i den ursprungliga kanalen tillämpas inte dessa ändringar på startkanaler.

   ![Bild](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Du kan ställa in live-startdatum i det här steget eller ställa in det senare när du redigerar egenskaperna för startprogrammet när det redan har skapats.

   **Förstå starttävlingens omfång**

   * **Erbjud fullständig start**: Alla kanaler för lanseringen befordras vid angivet live-datum.
   * **Befordra ändrade sidor**: Endast ändrade startresurser kommer att befordras. Vi rekommenderar att du använder det här alternativet när startgranskningen inte behövs.
   * **Befordra godkända sidor**: Det här alternativet kräver att arbetsflödet för godkännande vid start körs på startkanalerna. Endast godkända sidor befordras vid angivet live-datum.

      >[!CAUTION]
      >
      >Lansering av live-datum respekterar spelarens/enhetens tidszon i stället för serverns.

1. Du kommer att se att du har startat programmet. Du kan antingen klicka på **Öppna** för att visa sidorna i redigeraren eller klicka på **Klar** för att gå tillbaka till projektet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Om du klickar på **Done** kan du gå tillbaka till din **FutureLaunch**-kanal.

   ![Bild](/help/user-guide/assets/launches-images/launches-16.png)


### Redigera Launch-egenskaperna för att ange live-datum och -omfång {#editing-the-launch-properties-to-set-the-live-date-and-scope}

När starten har skapats kan du uppdatera egenskaperna, till exempel live-datum, starttitel och kampanjomfång, med **Launch Properties**.

* **Startdatum**, hänvisar till live-datumet, det vill säga det datum eller den tidpunkt då innehållet spelas upp i skärmspelaren enligt spelarens tidszon.
* **Production Ready**, gör att kanalerna kan publiceras efter att de har befordrats. Detta är aktiverat, så du behöver inte ändra detta.
* **Scope**, bestämmer vilka kanaler som ska befordras under lanseringskampanjen.


Följ stegen nedan för att redigera startegenskaperna:

1. Navigera till kanalen **FutureLaunch**, *(det är den väntande starten)* och markera kanalen, som visas i bilden nedan.

   ![bild](/help/user-guide/assets/launches-images/launches-17.png)

1. Klicka på **Dashboard** i åtgärdsfältet så ser du panelen **VÄNTANDE LAUNCHES** från kanalkontrollpanelen.

   ![bild](/help/user-guide/assets/launches-images/launches-18.png)

1. Markera starten och klicka på **Starta egenskaper** på panelen **VÄNTANDE START**.

   ![bild](/help/user-guide/assets/launches-images/launches-19.png)

### Redigera Skärmstarten för att lägga till eller ta bort kanaler {#editing-the-screens-launch-to-add-or-remove-channels}

När du har skapat starten kan du lägga till eller ta bort kanaler i den befintliga starten med alternativet **Redigera start**.

När du är klar klickar du på **Spara** för att gå tillbaka till kanalen **FutureLaunch**.

### Befordra skärmstart manuellt{#promote-the-screens-launch-manually}

Du kan befordra starten manuellt med alternativet **Befordra starten** på panelen **VÄNTANDE STARTOR**.

Du kan välja vilka resurser du vill befordra som en del av den här manuella befordringen i **Starta befordringsguiden**.

![bild](/help/user-guide/assets/launches-images/launches-e.png)

1. Du kan aktivera eller inaktivera alternativet att ta bort starten efter produktionen.
1. Du kan ställa in **Scope** för starten med följande alternativ:
   1. **Erbjud fullständig start**: Alla kanaler för lanseringen befordras vid angivet live-datum.
   1. **Befordra ändrade sidor**: Endast ändrade startresurser kommer att befordras. Vi rekommenderar att du använder det här alternativet när startgranskningen inte behövs.
   1. **Befordra godkända sidor**: Det här alternativet kräver att arbetsflödet för godkännande vid start körs på startkanalerna. Endast godkända sidor befordras vid angivet live-datum.
   1. **Höj upp aktuell sida**: Det här alternativet kräver att arbetsflödet för godkännande vid start endast körs för den aktuella sidan.
1. Klicka på **Nästa** i guiden **Befordra start**.
1. Klicka på **Befordra** för att befordra starten.

### Ta bort skärmstart {#deleting-the-screens-launch}

Du kan ta bort starten med alternativet **Ta bort start** på panelen **VÄNTANDE STARTOR**.

>[!CAUTION]
>
>Den här åtgärden tar även bort alla underordnade (kapslade starter).

