---
title: Konfiguration och felsökning av videouppspelning
seo-title: Felsöka videoklipp
description: null
seo-description: Följ den här sidan för att lära dig hur du felsöker videoklipp. När du överför en video till DAM och lägger till den i din kanal kan det uppstå problem som videon kanske inte kan spelas upp i skärmspelaren. I det här avsnittet beskrivs hur du felsöker och felsöker videouppspelning i din kanal.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 8a2ed4e0a27175d43abfadda63232c3577d5387b
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---


# Konfiguration och felsökning av videouppspelning {#video-playback-configuration-and-troubleshooting}

När du överför en video till DAM och lägger till den i din kanal kan du stöta på problem som videon kanske inte kan spelas upp i skärmspelaren.

I följande avsnitt beskrivs hur du felsöker och felsöker videouppspelning i din kanal.

## DAM-återgivningar {#dam-renditions}

När du har överfört videon till kanalen bör AEM börja skapa vissa återgivningar för den. Du kan visa dina videor under Resurser.

Så här visar du videon:

1. Navigera till videon, till exempel `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Klicka på videon och expandera den övre vänstra menyn och klicka på **Återgivningar**.

Det ska finnas olika renderingar (MP4 eller M4V).

Om det inte finns någon återgivning kontrollerar du att du har ffmpeg installerat på det operativsystem där AEM körs.

>[!CAUTION]
>
>Om det inte finns någon återgivning kontrollerar du att du har ffmpeg installerat på det operativsystem där AEM körs.
>
>Klicka [här](https://www.ffmpeg.org/download.html) för att installera ffmpeg.

## Videoresurser {#video-assets}

Om du inte ser något källattribut under video kan det bero på att videon inte har transkodats. Om videon är korrekt transkodad visas den på kontrollpanelen, vilket visas i figuren nedan.

Kontrollera att fmpeg är installerat och videoprofilerna.

![chlimage_1-2](assets/chlimage_1-2.png)

### Kontrollerar videoprofil {#checking-video-profile}

1. Navigera till **videoprofilen**, d.v.s. `http://localhost:4502/etc/dam/video.html` och klicka på **Överför testvideo**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Ladda upp en testvideo och klicka på **OK** för att börja omkodningen.

   Om omkodningen misslyckas expanderar du ffmpeg-utdata för att förstå eventuella fel i konsolutdata för ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Om videoomkodningen lyckas kan även den omkodade filen hämtas.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Se till att du hinner koda om videon tillräckligt mycket innan du lägger till den i någon kanal (taggen ska visas ny i stället för att bearbetas).

### Kontrollera profil med en videokomponent {#checking-profile-with-a-video-component}

Kontrollera listan med profiler från siddesignen om videokomponenten inte är korrekt konfigurerad.

1. Navigera till kanalen och välj **designläge** .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Markera videon och öppna dialogrutan **Redigera** . Öppna fliken **Profiler** .

   >[!NOTE]
   >Välj olika profiler (det ska finnas minst en H.264-profil med hög kvalitet).

### Kontrollera videon i webbspelaren {#checking-the-video-in-the-web-player}

Använd **webbspelaren** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` för att validera uppspelningen i webbläsare (Chrome och Safari). Chrome används på Android-enheter medan Safari är OSX- och iOS-webbläsare.

Om videon inte körs på Safari kommer den inte att köras i OSX- och iOS-spelare. Detta är antagligen ett kodningsproblem och videon måste kodas om.

Följ de här stegen för att använda ett DAM-arbetsflöde för att skapa FullHD-renderingar:

1. Navigera till *arbetsflödesmodelladministratören*, det vill säga `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Välj **skärmuppdatering** .
1. Klicka på **Starta arbetsflöde** i åtgärdsfältet för att öppna dialogrutan **Kör arbetsflöde** .

1. Välj videoresurs i **nyttolasten**.
1. Klicka på **Kör**.

>[!NOTE]
>
>Ge lite tid åt att skapa återgivningarna, men efter några sekunder/minuter (beroende på videostorleken) kan du läsa in webbspelaren på Safari igen.

#### Felsökning av flaggan för automatisk uppspelningsprincip {#troubleshooting-autoplay-policy-flag}

Om AEM Screens-spelaren hämtar videon men inte visar den måste du felsöka flaggan för automatisk uppspelningspolicy.

Följ stegen nedan för att felsöka Googles problem med automatisk uppspelningspolicyflagga:

1. Navigera till ***chrome://flags/#autoplay-policy***
1. Ändra **principen** för automatisk uppspelning från **standard** till **ingen användargest krävs**

1. Starta om webbläsaren och uppdatera spelaren

>[!NOTE]
>
>Om du vill veta mer om de bästa sätten för bra användarupplevelser med de nya reglerna för automatisk uppspelning i Chrome kan du läsa dokumentationen om *automatisk uppspelning av policyändringar*, d.v.s. `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Synkronisera video mellan flera spelare {#syncing-video-across-multiple-players}

Om du vill spela upp videofilmer synkront på flera enheter bör du använda den absoluta strategin för den sekvens videon är en del av.

#### Krav {#requirements}

* identiska 2+ spelare
* idealisk maskinvara
* identisk nätverkstopologi (spelare är anslutna till en NTP-server som justerar sina interna systemklockor)

#### Ställa in den absoluta strategin {#setting-up-the-absolute-strategy}

Den absoluta strategin:

* beräknar en ankartid (midnatt den aktuella dagen)
* beräknar sekvensens varaktighet (summan av längden för alla dess objekt)
* beräknar när som helst vilket objekt som ska spelas upp och nästa objekt genom att lösa sekvensen _remain_time = (current_time - anchor_time) % sequence_duration.

Följ stegen nedan för att konfigurera en absolut strategi:

1. Navigera till kanalförfattaren och markera sekvenskomponenten så som visas i bilden nedan.
1. Öppna konfigurationsdialogrutan.
1. Redigera **strategin** och lägg till absolut.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >Spelarnas operativsystem måste ha samma klocka.

**Justera klockor i OS X** Följ stegen nedan för att justera klockorna i OSX:

1. Öppna **datum- och tidsinställningar** för varje OSX-ruta
1. Kontrollera **Ställ in datum och tid automatiskt**
1. Klistra in värdet 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com i listrutan eller kör *sudo ntpdate -u -v 0.pool.ntp.org*
1. Starta 2+ spelare

Det kan ta en stund innan spelarna startar en ny, justerad sekvens.

