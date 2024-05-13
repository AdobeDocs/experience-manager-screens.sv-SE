---
title: Riktlinjer för val av maskinvara för spelarenheter
description: Läs mer om riktlinjer för val av maskinvara för AEM Screens Player-enheter.
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Riktlinjer för val av maskinvara för spelarenhet {#hardware-selection}

Följande avsnitt innehåller riktlinjer för val av maskinvara för en AEM Screens Player.

## Viktiga överväganden {#important-considerations}

* Alltid källa ***Kommersiellt*** eller ***Industriindustri*** Betygsätt komponenter för både PC Player och Display Panel eller Projector.

* Samarbeta alltid med leverantörer som levererar digitala signaturer.
* Ta alltid hänsyn till miljöfaktorer som omgivningstemperatur och relativ luftfuktighet.
* Granska alltid effektkrav och energikonditionering.
* Granska noggrant prestandabehoven och I/O-portarna som krävs för programmet.

## Maskinvarukonfigurationer {#hardware-configurations}

I följande tabell sammanfattas maskinvarukonfigurationerna med typiska användningsfall för ett AEM Screens-projekt:

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>Spelarkonfiguration</strong></td>
   <td><strong>Processor</strong></td>
   <td><strong>Minne</strong></td>
   <td><strong>Lagring SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>Visa</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>Vanliga användningsfall</strong></td>
  </tr>
  <tr>
   <td>Grundläggande</td>
   <td>Intel® Atom-processor med dubbla kärnor, i3 eller fyra kärnor på ingångsnivå</td>
   <td><p>4 GB minne</p> <p>2 MB cache</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet/trådlöst,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Helskärmsloop som standard<br /> </li>
     <li>Dag-parsning</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Intel® Core™ i5-processor med fyra kärnor</td>
   <td><p>8 GB minne</p> <p>4 MB cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Dynamiskt innehåll med en källa</li>
     <li>Enkel interaktiv</li>
     <li>1-3 zonlayouter</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avancerat</td>
   <td>Intel® Core™ i7-processor med fyra kärnor och hypertrådning</td>
   <td><p>16 GB minne</p> <p>8 MB cache</p> </td>
   <td>256 GB</td>
   <td>Dedikerad grafikprocessor</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet/trådlöst,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 eller fler innehållszoner, samtidiga videouppspelningar</li>
     <li>Flersidig interaktiv</li>
     <li>Datautlösare med flera källor</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
