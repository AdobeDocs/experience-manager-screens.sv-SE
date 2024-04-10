---
title: Konfigurera författare- och publiceringsinstanser i AEM Screens
description: Lär dig hur du konfigurerar en Author-instans och en Publish-instans för AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 0%

---


# Konfigurera författare- och publiceringsinstanser i AEM Screens {#configuring-author-and-publish-in-aem-screens}

På den här sidan beskrivs följande ämnen:

* **Konfigurera författare- och publiceringsinstanser**
* **Konfigurera publiceringstopologi**
* **Hantera publikation: Leverera innehållsuppdateringar från författare till publicering på enhet**

## Förutsättningar {#prerequisites}

Innan du börjar använda författar- och publiceringsservrar bör du ha kännedom om:

* **AEM Topology**
* **Skapa och hantera AEM Screens Project**
* **Enhetsregistreringsprocess**

>[!NOTE]
>
>Den här AEM Screens-funktionen är bara tillgänglig om du har AEM 6.4 Screens Feature Pack 2. Om du vill få tillgång till det här funktionspaketet måste du kontakta Adobe Support och begära åtkomst. När du har behörighet kan du hämta den från paketresursen.

>[!IMPORTANT]
>
>Om du vill använda mer än en Publish-instans med Dispatcher måste du uppdatera Dispatcher. Se [Aktivera anteckningssessioner](dispatcher-configurations-aem-screens.md#enable-sticky-session) för mer information.

## Konfigurera författare- och publiceringsinstanser {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Om du vill veta mer om arkitekturen Författare och Publicera och hur innehållet skapas i en AEM Författare-instans och sedan publiceras vidare till flera publiceringsinstanser går du till [Skapa och publicera arkitekturöversikt](author-publish-architecture-overview.md).

I följande avsnitt beskrivs hur du konfigurerar replikeringsagenter i topologin Författare och Publicera.

Du kan skapa ett enkelt exempel där du har en författare och två publiceringsinstanser:

* Författare > localhost:4502
* Publicera 1 (pub1) > localhost:4503
* Publicera 2 (pub2) > localhost:4504

## Konfigurera replikeringsagenter på författare {#setting-replication-agents}

Om du vill skapa replikeringsagenter måste du lära dig hur du skapar en standardredigeringsagent.

Det finns tre replikeringsagenter som behövs för skärmar:

1. **Standardreplikeringsagent ***(anges som*** Standardreplikeringsagent**)
1. **Raster Replication Agent**
1. **Agenten för omvänd replikering**

### Steg 1: Skapa en standardreplikeringsagent {#step-creating-a-default-replication-agent}

Följ stegen nedan om du vill skapa en standardsvar för replikering:

1. Navigera till AEM > hammikon > **Operationer** > **Konfiguration**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Välj **Replikering** från det vänstra navigeringsträdet.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Välj **Agenter på författare** från **Replikering** mapp och markera **Nytt** om du vill skapa en ny standardoperationsagent.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Ange **Titel** och **Namn** så att du kan skapa replikeringsagenten och sedan välja **Skapa**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Högerklicka på replikeringsagenten och välj **Öppna** om du vill redigera inställningarna.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Välj **Redigera**.

1. I **Agentinställningar** anger du informationen.

   >[!NOTE]
   >
   >Användaren måste kontrollera **Aktiverad** för att aktivera replikeringsagenten. Markera det här alternativet för standardagenter, skärmar och agenter för omvänd replikering.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navigera till **Transport** och ange **URI**, **Användare** och **Lösenord**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Du kan också kopiera och byta namn på en befintlig standardreplikeringsagent.


#### Skapar standardreplikeringsagenter  {#creating-standard-replication-agents}

1. Skapa en standardreplikeringsagent för pub1 (standardagenten som är färdig bör redan vara konfigurerad). Exempel: *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Skapa en standardslikeringsagent för pub2. Du kan kopiera som replikeringsagent för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen. Till exempel: *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Skapar agenter för skärmreplikering {#creating-screens-replication-agents}

1. Skapa en AEM Screens-replikeringsagent för pub1. Det finns en färdig Screens Replication Agent som pekar på port 4503. Aktivera det.
1. Skapa en AEM Screens-replikeringsagent för pub2. Kopiera skärmreplikeringsagenten för pub1 och ändra porten till 4504 för pub2.

   >[!NOTE]
   >Mer information om hur du konfigurerar agenter för skärmreplikering finns i [Konfigurerar agenten för skärmreplikering](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Skapar agenter för omvänd rasterreplikering {#creating-screens-reverse-replication-agents}

1. Skapa en omvänd replikeringsagent för pub1.
1. Skapa en omvänd replikeringsagent för pub2. Du kan kopiera agenten för omvänd replikering för pub1 och uppdatera transporten som ska användas för pub2 genom att ändra porten i transportkonfigurationen.

## Konfigurera publiceringstopologi {#setting-up-publish-topology}

### Steg 1: Konfigurera Apache Sling Oak-Based Discovery {#step-configure-apache-sling-oak-based-discovery}

Konfigurera Apache Sling Oak-Based Discovery för alla publiceringsinstanser i topologin

För varje publiceringsinstans:

1. Navigera till `https://<host>:<port>/system/console/configMgr`
1. Välj **Apache Sling Oak-Based Discovery Service** Konfiguration.
1. Uppdatera topologianslutnings-URL:er: lägg till URL:er för alla tolkande publiceringsinstanser:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Topologikoppling `Whitelist` Lista**: Anpassa till IP-adresser eller undernät som omfattar alla publiceringsinstanser. Se till att du `whitelist` IP-/värdnamnet för alla publiceringsinstanser utan portnummer.

1. Aktivera **Stoppa lokala loopar automatiskt**

Konfigurationen ska vara identisk för varje Publish-instans och Local-loop som automatiskt stoppar förhindrar en oändlig slinga.

#### Steg 2: Verifiera publiceringstopologi {#step-verify-publish-topology}

För alla publiceringsinstanser går du till `https://:/system/console/topology`. Du bör se varje Publish-instans som representeras i topologin under **Utgående topologianslutningar**.

#### Steg 3: Konfigurera ActiveMQ-objektkluster {#step-setup-activemq-artemis-cluster}

I det här steget kan du skapa krypterat lösenord för ActiveMQ Artemis-klustret.
Klusteranvändaren och lösenordet för alla publiceringsinstanser i topologin måste vara identiska. Lösenordet för ActiveMQ Artemis-konfigurationen måste vara krypterat. Eftersom varje instans har en egen krypteringsnyckel måste du använda krypteringsstöd för att skapa en krypterad lösenordssträng. Sedan kan det krypterade lösenordet användas i OSGi-konfigurationen för ActiveMQ.

På varje publiceringsinstans:

1. I OSGi Console går du till **HUVUDSAK** > **Krypteringsstöd** (`https://<host>:<port>/system/console/crypto`).
1. Skriv in lösenordet för oformaterad text (samma för alla förekomster) i **Oformaterad text**
1. Välj **Protect**.
1. Kopiera värdet **Skyddad text** till anteckningsblock eller textredigerare. Det här värdet kan användas i OSGi-konfigurationen för ActiveMQ.

Eftersom varje Publish-instans som standard har unika krypteringsnycklar, utför du det här steget på varje pub-instans och sparar den unika nyckeln för nästa konfiguration.

>[!NOTE]
>
>Lösenordet ska börja och sluta med klammerparenteser. Till exempel:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Steg 4: Aktivera ActiveMQ-artemis-kluster {#step-activate-activemq-artemis-cluster}

I varje publiceringsinstans:

1. Navigera till OSGi Config Manager `https://<host>:<port>/system/console/configMgr`
1. Välj **Apache ActiveMQ Artemis JMS Provider** Konfiguration
1. Uppdatera följande:

   * ***Klusterlösenord***: använd krypterat värde från föregående steg per instans
   * ***Ämnen***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verifiera ActiveMQ-objektkluster {#verify-activemq-artemis-cluster}

Följ stegen nedan för varje publiceringsinstans:

1. Navigera till OSGi Console > Main > ActiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verifiera och kontrollera om du vill visa portar för andra instanser under Klusterinformation > Topologi > noder=2, members=2.
1. Skicka ett testmeddelande (högst upp på skärmen under Information om mäklare)
1. Ange följande ändringar i fält:

   1. **Mål**: /com.adobe.cq.screens/devTestTopic
   1. **Text**: Hello World
   1. Visa `error.log` för varje instans så att du kan se att meddelandet skickades och togs emot i klustret.

>[!NOTE]
>
>Navigering till OSGi-konsolen kan ta några sekunder efter att konfigurationen sparats i föregående steg. Du kan också kontrollera error.log för mer information.

Följande bild visas till exempel när ActiveMQ Artemis Server har konfigurerats.

Om du inte ser följande konfiguration från */system/console/mq* navigera sedan till */system/console/mq* och markera **Starta om** för att starta om mäklaren.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Ta bort krav på referensrubrik {#remove-referrer-header-requirement}

Följ stegen för varje publiceringsinstans:

1. Navigera till **OSGi Console** > **Konfigurationshanteraren**
1. Välj **Apache Sling Referer-filter**
1. Uppdatera konfiguration och **Markera Tillåt tomt**

### Konfigurera författare och publiceringsinstans {#configuring-author-and-publish-instance}

När du har konfigurerat publiceringstopologin konfigurerar du författar- och publiceringsinstanserna för att visa de praktiska resultaten av implementeringen:

>[!NOTE]
>
>**Förutsättningar**
>
>För att komma igång med det här exemplet skapar du ett AEM Screens-projekt följt av att du skapar en plats, visning och kanal i ditt projekt. Lägg till innehåll i kanalen och tilldela kanalen till en skärm.

#### Steg 1: Starta en AEM Screens Player (enhet)

1. Starta ett separat webbläsarfönster.
1. Gå till Skärmspelaren med *webbläsare*, det vill säga`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` eller starta AEM Screens. När du öppnar enheten bör du observera att enhetens status är oregistrerad.

>[!NOTE]
>
>Du kan öppna en AEM Screens-spelare med den AEM Screens-app du hämtade eller med webbläsaren.

#### Steg 2: Registrera en enhet på författaren {#step-registering-a-device-on-author}

1. Gå till `https://localhost:4502/screens.html/content/screens/we-retail` eller välj projektet och gå till Enheter > Enhetshanteraren.
1. Välj **Registrera enhet**.
1. Välj **Enhetsregistrering**.
1. Välj den enhet som du vill registrera och välj sedan **Registrera enhet**.
1. Verifiera registreringskoden och välj **Validera**.
1. Ange en titel för enheten och välj **Registrera**.

#### Steg 3: Tilldela enheten till visning {#step-assigning-the-device-to-display}

1. Välj **Tilldela visning** i dialogrutan från föregående steg.
1. Välj visningsbanan för kanalen i dialogrutan **Platser** mapp.
1. Välj **Tilldela**.
1. Välj **Slutför** för att slutföra processen och nu tilldelas enheten.

Kontrollera spelaren och lägg märke till innehållet som du har lagt till i kanalen.

#### Steg 4: Publicera enhetskonfiguration för publiceringsinstanser {#step-publishing-device-configuration-to-publish-instances}

**Verifiera enheten**

Så här replikerar du enhetsanvändaren:

1. Gå till sidan för användaradministration. Till exempel: `https://localhost:4502/useradmin`.
1. Sök efter **`screens-devices-master`** grupp.
1. Högerklicka på gruppen och välj **Aktivera**.

>[!CAUTION]
>
>Aktivera inte författarpubliceringstjänsten eftersom det är en systemanvändare som används av författarjobbet.

Du kan även aktivera enheten från enhetshanteringskonsolen. Följ stegen nedan:

1. Navigera till ditt skärmsprojekt > **Enheter**.
1. Välj **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och välj **Aktivera** i åtgärdsfältet, som i bilden nedan.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>När du har aktiverat enheten kan du även redigera eller uppdatera serverns URL. Välj **Redigera server-URL** från åtgärdsfältet, som visas i figuren nedan, sprids dina ändringar till AEM Screens-spelaren.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Publiceringskontrolllista {#publishing-check-list}

Följande punkter sammanfattar publiceringskontrolllistan:

* *Skärmar enhetsanvändare* - Detta lagras som en AEM och aktiveras från **verktyg** > **Säkerhet** > **Användare**. Användaren har prefixet&quot;screens&quot; med en lång serialiserad sträng.

* *Projekt* - AEM Screens-projektet.
* *Plats* - Plats som enheten är ansluten till.
* *Kanaler* - en eller flera kanaler som visas på platsen
* *Schema* - om du använder ett schema, se till att det publiceras
* *Plats, scheman och kanalmapp* - om motsvarande resurser finns i en mapp.

Följ stegen nedan för att verifiera hur redigering och publicering fungerar:

1. Uppdatera visst kanalinnehåll på Author-instansen.
1. Utför **Hantera publikation** för att publicera nya ändringar i alla publiceringsinstanser.
1. Tryck **Aktivera** för att aktivera enheten från **Enhetshanteraren**.
1. **Redigera URL** från författarinstansens URL till en av publiceringsinstansens URL.
1. Kontrollera att det uppdaterade kanalinnehållet visas i AEM Screens Player.
1. Upprepa dessa steg med en annan Publish-instans.


#### Steg 5: Peka på enheten för att publicera instansen på Admin-panelen {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Visa administratörsgränssnittet från Skärmspelaren, tryck länge på det övre vänstra hörnet så att du kan öppna Admin-menyn, AEM Screens-spelaren med pekfunktion eller använda en mus.
1. Välj **Konfiguration** från sidopanelen.
1. Ändra författarinstans till Publicera instans i **Server**.

Se ändringarna i AEM Screens Player.

Du kan även uppdatera/redigera server-URL:en från enhetshanteringskonsolen genom att följa följande steg:

1. Navigera till ditt AEM Screens-projekt och välj **Enheter** mapp.
1. Välj **Enhetshanteraren** i åtgärdsfältet.
1. Markera enheten och välj **Redigera server-URL** från åtgärdsfältet, som visas i figuren nedan, och dina ändringar sprids till AEM Screens-spelaren.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

The **Hantera publikation** Med kan du leverera innehållsuppdateringar från författare till enhet. Du kan publicera/avpublicera innehåll för hela AEM Screens-projektet eller bara för en av dina kanaler, platser, enheter, program eller scheman. Mer information om den här funktionen finns i [On Demand Content Update](on-demand-content.md).

## Felsökning - tips {#troubleshoot-tips}

Följ avsnittet nedan för att få svar på vanliga frågor om författare/publiceringsinställningar.

### Hur lägger jag till en omdirigering från https till http efter den första registreringen och tilldelningen? {#add-redirect}

**Lösning**
Aktivera `Proxy/Load Balancer Connection in the Jetty configuration` till `true`.

### Så här uppdaterar du offlineinnehåll och problem med hämtning av spelare utanför `/content/dam/projects/<project>`? {#update-offline-content}

**Lösning**
Ge läsbehörighet för användare som har massvis-offline-update-screens-service och `screens-devices-master` grupp för alla `/content/dam` eller de specifika resurser som du vill använda, om du vill vara mer restriktiv.

### Hur åtgärdar jag fel i skärmreplikeringsagenten? {#replication-agent}

**Lösning**
Kontrollera att du inte har markerat Använd för omvänd replikering i agentkonfigurationen. Det går inte att använda agenten för skärmreplikering som en omvänd replikeringsagent och omfattningen av den här funktionen är att vidarebefordra enhetskommandon från Författare till Publicera.