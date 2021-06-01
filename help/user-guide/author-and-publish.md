---
title: Konfigurera författare och publicera i AEM Screens
seo-title: Konfigurera författare och publicera i AEM Screens
description: AEM Screens arkitektur liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan för att lära dig hur du konfigurerar författare och publicerar för AEM Screens.
seo-description: AEM Screens arkitektur liknar en traditionell AEM Sites-arkitektur. Innehållet skapas på en AEM författarinstans och sedan vidarebefordras till flera publiceringsinstanser. Följ den här sidan för att lära dig hur du konfigurerar författare och publicerar för AEM Screens.
feature: Administrera skärmar
role: Administrator, Developer
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 0%

---


# Konfigurera författare och publicera i AEM Screens {#configuring-author-and-publish-in-aem-screens}

På den här sidan beskrivs följande ämnen:

* **Konfigurera författare- och publiceringsinstanser**
* **Konfigurera publiceringstopologi**
* **Hantera publikation: Leverera innehållsuppdateringar från författare till enhet**

## Förutsättningar {#prerequisites}

Innan du börjar med författare och publiceringsservrar bör du ha kunskap om:

* **AEM Topology**
* **Skapa och hantera AEM Screens Project**
* **Enhetsregistreringsprocess**

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har installerat AEM 6.4 Screens Feature Pack 2. Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

>[!IMPORTANT]
>
>Om du vill använda fler än en publiceringsinstans med dispatchern måste du uppdatera dispatchern.vilken fil som helst i dispatchern. Mer information finns i [Aktivera anteckningssessioner](dispatcher-configurations-aem-screens.md#enable-sticky-session).

## Konfigurerar författare- och publiceringsinstanser {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Om du vill veta mer om författaren och publiceringen av en arkitekturöversikt och hur innehållet skapas på en AEM författarinstans och sedan replikeras till flera publiceringsinstanser kan du läsa [Översikt över författararkitekturen och publiceringsarkitekturen](author-publish-architecture-overview.md).

I följande avsnitt beskrivs hur du konfigurerar replikeringsagenter för författare och publiceringstopologi.

Du kan skapa ett enkelt exempel där du är värd för en författare och två publiceringsinstanser:

* Författare —> localhost:4502
* Publish 1 (pub1) —> localhost:4503
* Publish 2 (pub2) —> localhost:4504

## Konfigurera replikeringsagenter på författaren {#setting-replication-agents}

Om du vill skapa replikeringsagenter måste du lära dig hur du skapar en standardredigeringsagent.

Det finns tre replikeringsagenter som behövs för skärmar:

1. **Standardreplikeringsagent  ***(angiven*** som standardreplikeringsagent**)
1. **Raster Replication Agent**
1. **Agenten för omvänd replikering**

### Steg 1: Skapar en standardreplikeringsagent {#step-creating-a-default-replication-agent}

Följ stegen nedan om du vill skapa en standardsvar för replikering:

1. Navigera till din AEM instans —> hammikon —> **Åtgärder** —> **Konfiguration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Välj **Replikering** i det vänstra navigeringsträdet.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Välj **Agenter på författaren** i mappen **Replikering** och klicka på **Nytt** för att skapa en ny standardslikeringsagent.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Ange **titeln** och **Namn** för att skapa replikeringsagenten och klicka på **Skapa**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Högerklicka på replikeringsagenten och klicka på **Öppna** för att redigera inställningarna.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Klicka på **Redigera** för att öppna dialogrutan **Agentinställningar** och ange informationen.

   >[!NOTE]
   >
   >Användaren måste kontrollera **Aktiverad** för att aktivera replikeringsagenten. Du måste markera det här alternativet för standardagenter, skärmar och agenter för omvänd replikering.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navigera till fliken **Transport** och ange **URI**, **Användare** och **Lösenord**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Du kan också kopiera och byta namn på en befintlig standardreplikeringsagent.


#### Skapar standardreplikeringsagenter {#creating-standard-replication-agents}

1. Skapa en standardobjektreplikeringsagent för pub1 (standardagenten som är klar att användas ska redan vara konfigurerad) (till exempel *https://&lt;värdnamn>:4503/bin/receive?sling:authRequestLogin=1*)
1. Skapa en standardslikeringsagent för pub2. Du kan kopiera rep agent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen. (till exempel *https://&lt;värdnamn>:4504/bin/receive?sling:authRequestLogin=1*)

#### Skapar rasterreplikeringsagenter {#creating-screens-replication-agents}

1. Skapa AEM Screens-replikeringsagent för pub1. Det finns en som heter Screens Replication Agent som pekar på port 4503. Detta måste aktiveras.
1. Skapa AEM Screens replikeringsagent för pub2. Kopiera skärmreplikeringsagenten för pub1 och ändra porten till punkt 4504 för pub2.

#### Skapar agenter för omvänd rasterreplikering {#creating-screens-reverse-replication-agents}

1. Skapa en standardinverterad replikeringsagent för pub1.
1. Skapa en standardinverterad replikeringsagent för pub2. Du kan kopiera omvänd rep-agent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen.

## Konfigurera publiceringstopologi {#setting-up-publish-topology}

### Steg 1: Konfigurera Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Konfigurera Apache Sling Oak-Based Discovery för alla publiceringsinstanser i topologin

För varje publiceringsinstans:

1. Navigera till `https://<host>:<port>/system/console/configMgr`
1. Välj **Apache Sling Oak-Based Discovery Service** Configuration.
1. Uppdatera topologianslutnings-URL: lägga till URL:er för alla partakta publiceringsinstanser som är:
   * `https://localhost:4503/libs/sling/topology/connector`
   * `https://localhost:4504/libs/sling/topology/connector`
1. **Vitlista för topologikoppling**: anpassa sig till IP-adresser eller undernät som omfattar partakta publiceringsinstanser
1. Aktivera **Stoppa lokala loopar automatiskt**

Konfigurationen ska vara identisk för varje publiceringsinstans och den automatiska stopploopen förhindrar en oändlig slinga.

#### Steg 2: Verifiera publiceringstopologi {#step-verify-publish-topology}

Navigera till `https://:/system/console/topology` för alla publiceringsinstanser. Du bör se alla publiceringsinstanser som representeras i topologin under **Utgående topologianslutningar**.

#### Steg 3: Konfigurera ActiveMQ-objektkluster {#step-setup-activemq-artemis-cluster}

I det här steget kan du skapa krypterat lösenord för ActiveMQ Artemis-klustret.
Klusteranvändaren och lösenordet för alla publiceringsinstanser i topologin måste vara identiska. Lösenordet för ActiveMQ Artemis-konfigurationen måste krypteras. Eftersom varje instans har en egen krypteringsnyckel måste du använda krypteringsstöd för att skapa en krypterad lösenordssträng. Krypterat lösenord används sedan i OSGi-konfigurationen för ActiveMQ.

På varje publiceringsinstans:

1. I OSGi Console går du till **MAIN** —> **Krypteringsstöd** (`https://&lt;host&gt;:&lt;port&gt;/system/console/crypto`).
1. Skriv in det önskade lösenordet för oformaterad text (samma för alla förekomster) i **Oformaterad text**
1. Klicka på **Protect**.
1. Kopiera värdet **Skyddad text** till anteckningsblocket eller textredigeraren. Det här värdet används i OSGi-konfigurationen för ActiveMQ.

Eftersom varje publiceringsinstans som standard har unika krypteringsnycklar måste du utföra det här steget på varje pub-instans och spara den unika nyckeln för nästa konfiguration.

>[!NOTE]
>
>Lösenordet ska börja och sluta med klammerparenteser. Till exempel:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Steg 4: Aktivera ActiveMQ-objektkluster {#step-activate-activemq-artemis-cluster}

På varje publiceringsinstans:

1. Navigera till OSGi Config-hanteraren `https://&lt;host&gt;:&lt;port&gt;/system/console/configMgr`
1. Välj **ActiveMQ Artemis JMS Provider**-konfiguration för Apache
1. Uppdatera följande:

   * ***Klusterlösenord***: använd krypterat värde från föregående steg per instans
   * ***Avsnitt***:  `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verifiera ActiveMQ-objektkluster {#verify-activemq-artemis-cluster}

Följ stegen nedan för varje publiceringsinstans:

1. Navigera till OSGi Console -> Meny > ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verifiera och kontrollera om du vill visa portar för andra instanser under Klusterinformation > Topologi > noder=2, members=2.
1. Skicka ett testmeddelande (högst upp på skärmen under Information om mäklare)
1. Ange följande ändringar i fält:

   1. **Mål**: /com.adobe.cq.screens/devTestTopic
   1. **Text**: Hello World
   1. Visa fel.logg för varje instans för att se att meddelandet skickades och togs emot i hela klustret

>[!NOTE]
>
>Navigering till OSGi-konsolen kan ta några sekunder efter att konfigurationen sparats i föregående steg. Du kan också kontrollera error.log för mer information.

Följande bild visas till exempel när ActiveMQ Artemis Server har konfigurerats.

Om du inte ser följande konfiguration från */system/console/mq* går du till */system/console/mq* och klickar på **Starta om** för att starta om mäklaren.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Ta bort krav på referensrubrik {#remove-referrer-header-requirement}

Följ stegen för varje publiceringsinstans:

1. Navigera till **OSGi-konsolen** > **Configuration Manager**
1. Välj **Referensfilter för Apache Sling**
1. Uppdatera konfigurationen och **markera Tillåt tomt**

### Konfigurerar författare och publiceringsinstans {#configuring-author-and-publish-instance}

När du har konfigurerat publiceringstopologin måste du konfigurera författaren och publiceringsinstanserna för att visa de praktiska resultaten av implementeringen:

>[!NOTE]
>
>**Förutsättningar**
>
>För att komma igång med det här exemplet skapar du ett nytt AEM Screens-projekt följt av att du skapar en plats, visning och kanal i ditt projekt. Lägg till innehåll i kanalen och tilldela kanalen till en skärm.

#### Steg 1: Starta en AEM Screens Player (enhet) {#step-starting-an-aem-screens-player-device}

1. Starta ett separat webbläsarfönster.
1. Gå till Skärmspelaren med *webbläsaren*, d.v.s.`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` eller starta AEM Screens-appen. När du öppnar enheten visas enhetens status som ej registrerad.

>[!NOTE]
>
>Du kan öppna en AEM Screens-spelare med den AEM Screens-app du hämtade eller med webbläsaren.

#### Steg 2: Registrerar en enhet på författaren {#step-registering-a-device-on-author}

1. Gå till `https://localhost:4502/screens.html/content/screens/we-retail` eller välj projektet och navigera till Enheter > Enhetshanteraren.
1. Välj **Registrera enhet**.
1. Klicka på **Enhetsregistrering** för att visa enheten.
1. Välj den enhet som du vill registrera och klicka på **Registrera enhet**.
1. Verifiera registreringskoden och klicka på **Validera**.
1. Ange en rubrik för enheten och klicka på **Registrera**.

#### Steg 3: Tilldela enheten till visning {#step-assigning-the-device-to-display}

1. Klicka på **Tilldela visning** i dialogrutan från föregående steg.
1. Välj visningssökvägen för kanalen i mappen **Platser**.
1. Klicka på **Tilldela**.
1. Klicka på **Slutför** för att slutföra processen, och nu tilldelas enheten.

Kontrollera spelaren så ser du innehållet som du har lagt till i kanalen.

#### Steg 4: Publicerar enhetskonfiguration för att publicera instanser {#step-publishing-device-configuration-to-publish-instances}

**Verifiera enheten**

Innan du utför stegen nedan kontrollerar du att enhets-ID är verifierat. Kontrollera genom att söka efter enhets-ID i CRXDE Lite, med sökvägen */home/users/screens/we-retail/devices*.

Så här replikerar du enhetsanvändaren:

1. Gå till sidan för användaradministration (t.ex.: `https://localhost:4502/useradmin`
1. Sök efter gruppen **screens-devices-överordnad**
1. Högerklicka på gruppen och klicka på **Aktivera**

>[!CAUTION]
>
>Aktivera inte författare-publish-screens-service eftersom det är en systemanvändare som används av författarjobbet.

Du kan även aktivera enheten från enhetshanteringskonsolen. Följ stegen nedan:

1. Gå till ditt skärmsprojekt —> **Enheter**.
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och klicka på **Aktivera** i åtgärdsfältet enligt bilden nedan.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>När du har aktiverat enheten kan du också redigera eller uppdatera server-URL:en genom att klicka på **Redigera server-URL** i åtgärdsfältet, vilket visas i bilden nedan, så sprids ändringarna till AEM Screens-spelaren.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Publiceringskontrolllista {#publishing-check-list}

Följande punkter sammanfattar publiceringskontrolllistan:

* *Skärmar som enhetsanvändare*  - Detta lagras som en AEM användare och aktiveras från  **Verktyg**  >  **Säkerhet**  >  **Användare**. Användaren får prefixet&quot;screens&quot; med en lång serialiserad sträng.

* *Project*  - The AEM Screens project.
* *Plats*  - Den plats där enheten är ansluten.
* *Kanaler*  - en eller flera kanaler som visas på platsen
* *Schema*  - Om du använder ett schema måste du se till att det publiceras
* *Plats, Scheman och Kanalmapp*  - om motsvarande resurser finns i en mapp.

Följ stegen nedan för att verifiera författarens/publiceringens beteende:

1. Uppdatera kanalinnehåll i författarinstans
1. Utför **Hantera publikation** för att publicera nya ändringar i alla publiceringsinstanser
1. Tryck på **Aktivera** för att aktivera enheten från **Enhetshanteraren**
1. **Redigera URL:** från författarinstansens URL till någon av publiceringsinstansernas URL
1. Verifiera att det uppdaterade kanalinnehållet visas i AEM Screens Player
1. Upprepa dessa steg med en annan publiceringsinstans


#### Steg 5: Peka på enheten för att publicera instansen på adminpanelen {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visa administratörsgränssnittet från Skärmspelaren, tryck länge på det övre vänstra hörnet för att öppna Admin-menyn, på din touchaktiverade AEM Screens-spelare eller genom att använda en mus.
1. Klicka på alternativet **Konfiguration** på sidopanelen.
1. Ändra författarinstansen till publiceringsinstans i **Server**.

Se ändringarna i din AEM Screens-spelare.

Du kan även uppdatera/redigera server-URL:en från enhetshanteringskonsolen genom att följa följande steg:

1. Gå till ditt AEM Screens-projekt och välj mappen **Enheter**.
1. Klicka på **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och klicka på **Redigera server-URL** i åtgärdsfältet, så som visas i figuren nedan, så sprids ändringarna till AEM Screens-spelaren.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

Med funktionen **Hantera publikation** kan du leverera innehållsuppdateringar från författare till publicering till enhet. Du kan publicera/avpublicera innehåll för hela AEM Screens-projektet eller bara för en av dina kanaler, platser, enheter, program eller scheman. Mer information om den här funktionen finns i [On-Demand Content Update](on-demand-content.md).


