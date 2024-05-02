---
title: EU-klanten kunnen betalingen niet voltooien
description: Dit artikel bevat een oplossing voor het probleem dat klanten uit de Europese Unie de betalingen niet kunnen voltooien.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# EU-klanten kunnen betalingen niet voltooien

Dit artikel bevat een oplossing voor het probleem dat klanten uit de Europese Unie de betalingen niet kunnen voltooien.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies
* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Probleem

Klanten uit de EU klagen dat hun creditcardtransacties worden geweigerd.

## Oorzaak

De Europese Unie heeft een verordening met de naam Richtlijn Betalingsdiensten (PSD) herzien met een bijgewerkte versie [PSD 2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Dit is een richtlijn van de Europese Unie (EU) die verplicht is betalingsdiensten en betalingsdienstaanbieders in de hele EU en de Europese Economische Ruimte (EER) te reguleren. De sterke Authentificatie van de Klant (SCA) is een vereiste van PSD2 om de veiligheid van betalingsgegevens en authentificatie te verhogen. Als uw betalingsoplossingen niet voldoen aan de vereisten van de richtlijn, kan dit ertoe leiden dat klanten de betalingen niet kunnen voltooien. Meer informatie vindt u in het gedeelte [verwant Adobe Commerce DevBlog-bericht](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Oplossing

Volg de aanbevelingen van de [Adobe Commerce Payment Provider Recommendations sectie van DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
