---
title: Adobe Commerce-probleemoplosser
description: Deze functie voor het snel oplossen van problemen voor Adobe Commerce-gebruikers begeleidt u bij de oplossingen op basis van uw reactie op de symptomen die u ziet. Klik op de vragen om de volgende opties of antwoorden weer te geven.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Adobe Commerce-probleemoplosser

Deze functie voor het snel oplossen van problemen voor Adobe Commerce-gebruikers begeleidt u bij de oplossingen op basis van uw reactie op de symptomen die u ziet. Klik op de vragen om de volgende opties of antwoorden weer te geven.

## Stap 1 - Verifieer de Snelle dienst {#step-1}

+++**de Klant meldt een probleem dat Fastly impliceert. Is de dienst van de Fastly neer?**

a. JA - controleer [ de Snelle Status van de Dienst ](https://status.fastly.com/), en [ voorlegt een de steunkaartje van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - ga aan [ Stap 2 ](#step-2) te werk.

+++

## Stap 2 - VCL-configuratiebestand controleren {#step-2}

+++**hebt u om het even welke fouten wanneer u het Meetapparaat van het Achterste in werking stelt?**

Stel uw project URL door het [ Achterste Meetapparaat in werking - snel ](https://magento-tester.global.ssl.fastly.net/magento-tester/). Het toont de versie van het VCL configuratiedossier, als de pagina cacheable is, de versie van Fastly module en andere nuttige het oplossen van problemeninformatie. Hebt u fouten?

a. JA - U hebt de versie van de Insteekmodule VCL van het bericht _verouderd! Upload het bestand opnieuw._ Voor de oplossing aan deze fout, verwijs naar [ Fastly Fout: De versie van de stop VCL is verouderd! Please re-Upload ](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NO - [ Stap 3 ](#step-3).

+++

## Stap 3 - Controleren op optimalisatiefout van afbeelding {#step-3}

+++**fout van de optimalisering van het Beeld?**

a. JA - [ Fout wanneer het toelaten van beeldoptimalisering ](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Controleer DNS door in CLI/terminal te lopen: `dig [your website.com] + short`. Ga aan [ Stap 4 ](#step-4) te werk.

+++

## Stap 4 - Verbeter DNS {#step-4}

+++**wat gebeurt wanneer u `dig` in werking stelt?**

Wanneer u `dig` in werking stelde het een verslag terugkwam dat aan prod.magentocloud.map.fastly.net of één van de volgende IP adressen richt (zie [ DNS van de Update configuratie met productie plaatsend ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) in onze ontwikkelaarsdocumentatie):

* 15.10.1.124
* 151 101 65 124
* 15.10.129.124
* 15.10.193.124

a. JA - De kwestie heeft geen DNS betrekking. Ga aan [ Stap 5 ](#step-5) te werk.\
b. NO - De kwestie heeft waarschijnlijk betrekking op DNS. De klant zou DNS configuratie ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist#update-dns-configuration-with-production-settings) moeten controleren [ of hun DNS leverancier voor meer informatie contacteren.

+++

## Stap 5 - Verbinding bevestigen {#step-5}

+++**krijgt u een &quot;Verbinding onveilig&quot;of &quot;niet Veilig&quot;bericht teruggekeerd wanneer het lopen `curl -svo /dev/null "https://website.com"` in CLI/terminal?**

a. JA - Dit is waarschijnlijk een certificaatafgifte. Ga naar de website in een browser en selecteer het vergrendelingspictogram en zoek naar een vervaldatum van het certificaat. Ga aan [ Stap 6 ](#step-6) te werk.\
b. NO - Bezoek [ http://fastly-debug.com ](https://www.fastly-debug.com/) en deel deze informatie in een [ de steunkaartje van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 6 - Bevestig dat u een geldig SLV-certificaat hebt {#step-6}

+++**is het certificaat verlopen?**

a. JA - U moet uw TLS-certificaat vernieuwen met de certificeringsinstantie (CA).\
b. NEE - U mag helemaal geen certificaat hebben. Als u Adobe Commerce hebt, raden we u aan een TLS-certificaat aan te schaffen. Als u op Adobe Commerce op cloudinfrastructuur bent, kunt u beschikken over een door domein gevalideerd SSL/TLS-certificaat coderen om snel veilig HTTPS-verkeer te kunnen gebruiken. Zie [ voorziening SSL/TLS certificaten ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) in onze ontwikkelaarsdocumentatie.

+++

[Terug naar stap 1](#step-1)
