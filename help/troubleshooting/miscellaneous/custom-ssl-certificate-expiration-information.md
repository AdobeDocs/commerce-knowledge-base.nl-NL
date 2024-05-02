---
title: Aangepaste SSL-certificaatvervalgegevens
description: Dit artikel biedt een oplossing voor het moment dat een aangepast SSL-certificaat is bijgewerkt met een door de Adobe opgegeven SSL-certificaat.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Aangepaste SSL-certificaatvervalgegevens

Dit artikel biedt een oplossing voor het moment dat een aangepast SSL-certificaat is bijgewerkt met een door de Adobe opgegeven SSL-certificaat.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Adobe Commerce werkt SSL-certificaten 30 dagen voor het verlopen automatisch bij. Deze automatisering controleert niet of het certificaat dat wordt vervangen een interne SSL of een douane-derde SSL is en zal het met geldige interne SSL na opsporing van vervaldatum vervangen. Dit kan verwarring veroorzaken voor eigenaren en exploitanten van sites die verwachten dat het aangepaste certificaat op de site aanwezig is, en het potentieel voor andere functionele problemen zoals, maar niet beperkt tot, een uitval van een site.

<u>Stappen om te reproduceren</u>

1. Aangepast SSL-certificaat geïnstalleerd voor de website.
1. Automatisering detecteert dat het aangepaste SSL-certificaat 30 dagen verwijderd is.
1. Adobe Commerce vervangt het aangepaste certificaat automatisch door ons interne certificaat.

<u>Verwachte resultaten</u>

Adobe Commerce slaat aangepaste certificaten over wanneer de automatische SSL-certificaatupdate wordt uitgevoerd.

<u>Werkelijke resultaten</u>

Adobe Commerce werkt een certificaat bij als dit 30 dagen is verlopen.

## Oplossing

Wanneer een handelaar verkiest om hun eigen douaneSSL certificaat te gebruiken, moet het meer dan 30 dagen vóór de certificaatvervaldatum worden bijgewerkt om ervoor te zorgen dat het niet door een intern SSL van Adobe Commerce SSL certificaat zal worden vervangen.

Als u zich in een situatie bevindt waarin uw aangepaste SSL is vervangen door onze interne SSL en u wilt dit vervangen door uw bijgewerkte aangepaste SSL-certificaat, [een steunaanvraag indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) met de locatie waar u de nieuwe certificaatbestanden hebt geüpload. Neem de begindatum van de nieuwe SSL op. Zodra wij deze informatie hebben, kunnen wij met de installatie van het nieuwe SSL certificaat verdergaan.

## Gerelateerde lezing

* [SSL-certificaten (TLS) voor Magento Commerce Cloud: Veelgestelde vragen](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) in onze kennisbasis voor ondersteuning.
* [Referentie voor opdrachtregelprogramma&#39;s: magento-cloud-certificaat:toevoegen](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-cloud.html#certificateadd) in onze ontwikkelaarsdocumentatie.
* [Checklist starten](https://devdocs.magento.com/cloud/live/site-launch-checklist.html)in onze ontwikkelaarsdocumentatie.
* [Toegang tot het hulpmiddel Analyse voor de hele site](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html#step-2-access-site-wide-analysis-tool) in onze gebruikershandleiding.
