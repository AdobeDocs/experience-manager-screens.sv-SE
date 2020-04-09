---
title: Säkerhetschecklista för AEM-skärmar
seo-title: Säkerhetschecklista för AEM-skärmar
description: Sidan beskriver säkerhetschecklistan för AEM-skärmar
seo-description: Sidan beskriver säkerhetschecklistan för AEM-skärmar
translation-type: tm+mt
source-git-commit: aa597424104880a79a8fcec4cfd08cd1a13a8aba

---


# Systemsäkerhetsfrågor för AEM-skärmar {#security-checklist}

På den här sidan visas systemsäkerhetsaspekter för AEM-skärmar.


## White Paper for AEM Screens Security {#faqs-screens}

I det här avsnittet beskrivs rapporten.


## Frågor och svar för AEM Screens Security {#faqs-screens}

Följande frågor och svar förutsätter en autentiserad, registrerad spelararkitektur med HTTPS som kommunikationsprotokoll mellan spelare och AEM Server.

### Vanliga frågor 1 {#faq1}

Kan spelartrafik dirigeras om till en skadlig server och instrueras att hämta och spela upp skadligt mediematerial?

**Svara** Det går inte eftersom HTTP-anslutningen identifierar båda ändar av anslutningen och krypterar den. Om du försöker vara i mitten och tolka det visas bara krypterat innehåll, och om du försöker personifiera servern kommer spelaren att neka dig eftersom ditt certifikat är annorlunda.


### Frågor och svar 2 {#faq2}

Ska jag använda HTTP eller HTTP?
**Svara** Använd HTTP. Detta är ett måste om ni är oroliga för säkerheten. Med HTTP krypteras kommunikationen mellan spelare och server, och det blir i princip omöjligt att fånga upp innehållet eller modifiera det.


### Vanliga frågor 3 {#faq3}

Finns det någon form av signering av innehållet eller hash när du laddar ned det?
**Svara på**varje resurs signeras (SHA) av servern och valideras sedan av spelaren för samma hash för att garantera integriteten.
Om hashen inte matchar försöker vi verifiera igen 3 gånger. Efter tre försök anser vi att nedladdningskommandot är ogiltigt.


### Frågor och svar 4 {#faq4}

Är AEM Server säker?
**Svar** 4. Om du använder AMS tar vi hand om all serversäkerhet med samma funktioner som Sites eller Assets.


### Frågor och svar 5 {#faq5}

Är enheten säker?
**Svar:** En fysiskt komprometterad spelare kan teoretiskt manipuleras för att spela upp vilket innehåll som helst. Du kan också ansluta spelaren och ansluta en USB/HDMI-styrenhet.

Därför rekommenderar vi att enheterna är utom räckhåll, helst i en säker behållare, med kabeldragningen även skyddad. Inaktivera även IR-fjärrportar.

Om enhetens operativsystem inte uppdateras regelbundet kan operativsystemet lämnas utsatt för säkerhetshål och tillåta fjärråtkomst över nätverket.
[!NOTE]
>Vi rekommenderar att du instrumenterar enheterna med lämpliga funktioner för fjärruppdatering och fjärrstyrning (fjärrskrivbordsdator, MDM-lösning osv.)

Dessutom skulle det vara bra att placera dem i ett privat nätverk som inte exponeras för det offentliga wifi-nätverket.


### Vanliga frågor 6 {#faq6}

Hur skulle en hackare försöka äventyra en spelare?
**Svar** Det enda sättet att kompromissa med en spelarenhet är att:

1. kompromissa med DNS för att personifiera servern på sitt värdnamn och
1. kompromiss
   1. certifikatservern för att personifiera servern
   1. och personifiera certifikatet på klientsidan

1 och 2a är mest opraktiskt i verkligheten, och med 2b kräver du i alla fall åtkomst till enheten, så du kan lika gärna byta ut den för din egen enhet som kör falskt innehåll.

Vi är alltså bara lika säkra som deras nätverk och deras lokaler.

>[!IMPORTANT]
>Även om en enhet är komprometterad kan du ändå enkelt återkalla dess autentiseringsuppgifter så att den inte kan ansluta till AEM längre.





