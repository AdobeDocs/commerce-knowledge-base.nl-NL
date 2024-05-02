---
title: Adobe Commerce-probleemoplosser
description: Deze functie voor het snel oplossen van problemen voor Adobe Commerce-gebruikers begeleidt u bij de oplossingen op basis van uw reactie op de symptomen die u ziet. Klik op de vragen om de volgende opties of antwoorden weer te geven.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Adobe Commerce-probleemoplosser

Deze functie voor het snel oplossen van problemen voor Adobe Commerce-gebruikers begeleidt u bij de oplossingen op basis van uw reactie op de symptomen die u ziet. Klik op de vragen om de volgende opties of antwoorden weer te geven.

## Stap 1 - Verifieer de Snelle dienst {#step-1}

+++**De klant rapporteert een probleem met Fastly. Is de Fastly service down?**

a. JA - Controle [Snelle servicestatus](https://status.fastly.com/), en [een Adobe Commerce-ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Doorgaan naar [Stap 2](#step-2).

+++

## Stap 2 - VCL-configuratiebestand controleren {#step-2}

+++**Hebt u om het even welke fouten wanneer u het Meetapparaat van de Rand in werking stelt?**

Voer de URL van uw project uit via [Achterste tester - snel](https://magento-tester.global.ssl.fastly.net/magento-tester/). Het toont de versie van het VCL configuratiedossier, als de pagina cacheable is, de versie van Fastly module en andere nuttige het oplossen van problemeninformatie. Hebt u fouten?

a. JA - U hebt het bericht _De versie van de insteekmodule VCL is verouderd! Upload het bestand opnieuw._ Voor de oplossing van deze fout raadpleegt u [Fastly Error: Plugin VCL version is verouderd! Please re-Upload](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b) NO - [Stap 3](#step-3).

+++

## Stap 3 - Controleren op optimalisatiefout van afbeelding {#step-3}

+++**Optimalisatiefout afbeelding?**

a. JA - [Fout bij inschakelen van optimalisatie afbeelding](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Controleer DNS door in CLI/terminal te lopen: `dig [your website.com] + short`. Doorgaan naar [Stap 4](#step-4).

+++

## Stap 4 - Verbeter DNS {#step-4}

+++**Wat gebeurt er wanneer u uitvoert `dig`?**

Wanneer u `dig` heeft het een verslag teruggegeven dat aan prod.magentocloud.map.fastly.net of één van de volgende IP adressen richt (zie [DNS-configuratie bijwerken met productieinstelling](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns) in onze documentatie voor ontwikkelaars):

* 15.10.1.124
* 151 101 65 124
* 15.10.129.124
* 15.10.193.124

a. JA - De kwestie heeft geen DNS betrekking. Doorgaan naar [Stap 5](#step-5).\
b. NO - De kwestie heeft waarschijnlijk betrekking op DNS. De klant moet [DNS-configuratie controleren](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns") of neem contact op met de DNS-provider voor meer informatie.

+++

## Stap 5 - Verbinding bevestigen {#step-5}

+++**Wordt het bericht &quot;Verbinding onbeveiligd&quot; of &quot;Niet beveiligd&quot; geretourneerd wanneer u een bewerking uitvoert `curl -svo /dev/null "https://website.com"` in de CLI/terminal?**

a. JA - Dit is waarschijnlijk een certificaatafgifte. Ga naar de website in een browser en selecteer het vergrendelingspictogram en zoek naar een vervaldatum van het certificaat. Doorgaan naar [Stap 6](#step-6).\
b. NO - Bezoek [http://fastly-debug.com](https://www.fastly-debug.com/) en deelt deze informatie in een [Adobe Commerce-ondersteuningsticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 6 - Bevestig dat u een geldig SLV-certificaat hebt {#step-6}

+++**Is het certificaat verlopen?**

a. JA - U moet uw TLS-certificaat vernieuwen met de certificeringsinstantie (CA).\
b. NEE - U mag helemaal geen certificaat hebben. Als u Adobe Commerce hebt, raden we u aan een TLS-certificaat aan te schaffen. Als u op Adobe Commerce op cloudinfrastructuur bent, kunt u beschikken over een door domein gevalideerd SSL/TLS-certificaat coderen om snel veilig HTTPS-verkeer te kunnen gebruiken. Zie [SSL/TLS-certificaten leveren](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) in onze ontwikkelaarsdocumentatie.

+++

[Terug naar stap 1](#step-1)
