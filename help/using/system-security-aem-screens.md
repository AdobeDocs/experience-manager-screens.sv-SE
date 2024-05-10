---
title: Säkerhetschecklista för AEM Screens
description: Läs mer om säkerhetschecklistan för AEM Screens.
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Systemsäkerhetsfrågor för AEM Screens {#security-checklist}

>[!IMPORTANT]
>En intern Git-resurs.

På den här sidan visas systemsäkerhetsfrågor för AEM Screens.


## White Paper for AEM Screens Security {#white-paper}

I det här avsnittet beskrivs vitboken. (Väntande vitpappersbilaga)


## Frågor och svar om AEM Screens Security {#faqs-screens}

Följande frågor och svar förutsätter en autentiserad, registrerad spelararkitektur. HTTPS används som kommunikationsprotokoll mellan spelaren och AEM.

### Vanliga frågor 1 {#faq1}

Kan spelartrafik dirigeras om till en skadlig server och instrueras att hämta och spela upp skadligt mediematerial?

**Svar**

Det är inte möjligt eftersom HTTP-anslutningen identifierar båda ändar av anslutningen och krypterar den. Om du försöker vara i mitten och tolka det så ser du bara krypterat innehåll. Om du försöker personifiera servern, kommer spelaren att neka dig eftersom ditt certifikat är annorlunda.


### Frågor och svar 2 {#faq2}

Ska jag använda HTTP eller HTTP?

**Svar**

Använd HTTP. Detta protokoll är ett måste om ni är oroliga för säkerheten. Med HTTP krypteras kommunikationen mellan spelare och server, och det är omöjligt att fånga upp innehållet eller modifiera det.


### Vanliga frågor 3 {#faq3}

Finns det någon form av signering av innehållet eller hash när du laddar ned det?

**Svar**

Varje resurs signeras (SHA) av servern. Spelaren validerar den sedan för samma hash för att garantera integriteten.
Om hashen inte matchar försöker programmet att validera tre gånger. Efter tre försök betraktas kommandot download som ogiltigt.


### Frågor och svar 4 {#faq4}

Är AEM server säker?

**Svar**

Förutsatt att du använder AMS tar programmet hand om all serversäkerhet med samma funktioner som Sites eller Assets.


### Frågor och svar 5 {#faq5}

Är enheten säker?

**Svar**

En fysiskt komprometterad spelare kan teoretiskt manipuleras för att spela upp allt innehåll. Du kan också koppla ur spelaren och ansluta en USB/HDMI-styrenhet.

Placera enheterna utom räckhåll, helst i en skyddad behållare, med kabeldragning även skyddad. Inaktivera även IR-fjärrportar.

Om enhetens operativsystem inte uppdateras regelbundet kan operativsystemet lämnas utsatt för säkerhetshål och tillåta fjärråtkomst över nätverket.

>[!NOTE]
>
>Vi rekommenderar att du instrumenterar enheterna med lämpliga funktioner för fjärruppdatering och fjärrstyrning (fjärrskrivbordsdator, MDM-lösning osv.). Vi rekommenderar även att du använder ett privat nätverk som inte är exponerat för den offentliga WIFI-filen.


### Vanliga frågor 6 {#faq6}

Hur skulle en hackare försöka äventyra en spelare?

**Svar**

Det enda sättet att kompromissa med en spelarenhet är att

1. kompromissa med DNS för att personifiera servern på det här värdnamnet, och,
1. kompromissa
   1. certifikatservern för att personifiera servern
   1. och personifiera certifikatet på klientsidan

>[!IMPORTANT]
>Även om en enhet är komprometterad kan du ändå enkelt återkalla dess autentiseringsuppgifter så att den inte kan ansluta till AEM längre.





