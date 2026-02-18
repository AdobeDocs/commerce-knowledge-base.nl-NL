---
title: Aangepaste SSL-certificaatvervalgegevens
description: Dit artikel biedt een oplossing voor het moment dat een aangepast SSL-certificaat is bijgewerkt met een door Adobe verstrekt SSL-certificaat.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Aangepaste SSL-certificaatvervalgegevens

Dit artikel biedt een oplossing voor het moment dat een aangepast SSL-certificaat is bijgewerkt met een door Adobe verstrekt SSL-certificaat.

## Betrokken producten en versies

Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

Adobe Commerce werkt SSL-certificaten 30 dagen voor het verlopen automatisch bij. Deze automatisering controleert niet of het certificaat dat wordt vervangen een interne SSL of een douane-derde SSL is en zal het met geldige interne SSL na opsporing van vervaldatum vervangen. Dit kan verwarring veroorzaken voor eigenaren en exploitanten van sites die verwachten dat het aangepaste certificaat op de site aanwezig is, en het potentieel voor andere functionele problemen zoals, maar niet beperkt tot, een uitval van een site.

<u> Stappen om te reproduceren </u>

1. Aangepast SSL-certificaat geïnstalleerd voor de website.
1. Automatisering detecteert dat het aangepaste SSL-certificaat 30 dagen verwijderd is.
1. Adobe Commerce vervangt het aangepaste certificaat automatisch door ons interne certificaat.

<u> Verwachte resultaten </u>

Adobe Commerce slaat aangepaste certificaten over wanneer de automatische SSL-certificaatupdate wordt uitgevoerd.

<u> Ware resultaten </u>

Adobe Commerce werkt een certificaat bij als dit 30 dagen is verlopen.

## Oplossing

Wanneer een handelaar verkiest om hun eigen douaneSSL certificaat te gebruiken, moet het meer dan 30 dagen vóór de certificaatvervaldatum worden bijgewerkt om ervoor te zorgen dat het niet door een intern SSL van Adobe Commerce SSL certificaat zal worden vervangen.

Als u in een situatie bent waar uw douaneSSL door uw interne SSL werd vervangen en u het met uw bijgewerkt douaneSSL certificaat wilt vervangen, gelieve [ een steunverzoek ](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) met de plaats voorleggen u uw nieuwe certificaatdossiers uploadde. Neem de begindatum van de nieuwe SSL op. Zodra wij deze informatie hebben, kunnen wij met de installatie van het nieuwe SSL certificaat verdergaan.

## Gerelateerde lezing

* [ SSL (TLS) certificaten voor de Wolk van de Handel van de Magento: Veelgestelde vragen ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) in onze basis van de steunkennis.
* [ bevel-lijn hulpmiddelen verwijzing: magento-wolk certificaat :add ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) in onze ontwikkelaarsdocumentatie.
* [ checklist van de Lancering ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist) in onze ontwikkelaarsdocumentatie.
* [ Toegang plaats-brede het Hulpmiddel van de Analyse ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) in onze gebruikersgids.
