---
title: Säkerhetschecklista för AEM-skärmar
seo-title: Säkerhetschecklista för AEM-skärmar
description: Sidan beskriver säkerhetschecklistan för AEM-skärmar
seo-description: Sidan beskriver säkerhetschecklistan för AEM-skärmar
translation-type: tm+mt
source-git-commit: 72551a4b56d1db851cad71abd2ce8c0b02bbbc30

---


# Systemsäkerhetsfrågor för AEM-skärmar {#security-checklist}

På den här sidan visas systemsäkerhetsaspekter för AEM-skärmar.


## White Paper for AEM Screens Security {#white-paper}

I det här avsnittet beskrivs rapporten. (Väntande vitpappersbilaga)


## Frågor och svar för AEM Screens Security {#faqs-screens}

Följande frågor och svar förutsätter en autentiserad, registrerad spelararkitektur med HTTPS som kommunikationsprotokoll mellan spelare och AEM Server.

### Vanliga frågor 1 {#faq1}

Kan spelartrafik dirigeras om till en skadlig server och instrueras att hämta och spela upp skadligt mediematerial?

**Svar**

Det är inte möjligt eftersom HTTP-anslutningen identifierar båda ändar av anslutningen och krypterar den. Om du försöker vara i mitten och tolka det visas bara krypterat innehåll, och om du försöker personifiera servern kommer spelaren att neka dig eftersom ditt certifikat är annorlunda.


### Frågor och svar 2 {#faq2}

Ska jag använda HTTP eller HTTP?

**Svar**

Använd HTTP. Detta är ett måste om ni är oroliga för säkerheten. Med HTTP krypteras kommunikationen mellan spelare och server, och det blir i princip omöjligt att fånga upp innehållet eller modifiera det.


### Vanliga frågor 3 {#faq3}

Finns det någon form av signering av innehållet eller hash när du laddar ned det?

**Svar**

Alla resurser signeras (SHA) av servern och valideras sedan av spelaren för samma hash för att garantera integriteten.
Om hashen inte matchar försöker vi verifiera igen 3 gånger. Efter tre försök anser vi att nedladdningskommandot är ogiltigt.


### Frågor och svar 4 {#faq4}

Är AEM Server säker?

**Svar**

Ans 4. Om du använder AMS tar vi hand om all serversäkerhet med samma funktioner som Sites eller Assets.


### Frågor och svar 5 {#faq5}

Är enheten säker?

**Svar**

En fysiskt komprometterad spelare kan teoretiskt manipuleras för att spela upp vilket innehåll som helst. Du kan också ansluta spelaren och ansluta en USB/HDMI-styrenhet.

Vi rekommenderar därför att enheterna är utom räckhåll, helst i en skyddad behållare, med kabeldragningen även skyddad. Inaktivera även IR-fjärrportar.

Om enhetens operativsystem inte uppdateras regelbundet kan operativsystemet lämnas utsatt för säkerhetshål och tillåta fjärråtkomst över nätverket.
>[!NOTE]
>Vi rekommenderar att du instrumenterar enheterna med lämpliga fjärruppdaterings- och kontrollfunktioner (fjärrskrivbordsdator, MDM-lösning osv.). Vi rekommenderar även att du använder ett privat nätverk som inte är exponerat för den offentliga WIFI-filen.


### Vanliga frågor 6 {#faq6}

Hur skulle en hackare försöka äventyra en spelare?

**Svar**

Det enda sättet att kompromissa med en spelarenhet är att:

1. kompromissa med DNS för att personifiera servern på sitt värdnamn, och,
1. kompromiss
   1. certifikatservern för att personifiera servern
   1. och personifiera certifikatet på klientsidan

>[!IMPORTANT]
>Även om en enhet är komprometterad kan du ändå enkelt återkalla dess autentiseringsuppgifter så att den inte kan ansluta till AEM längre.




