---
title: Implementatieproblemen met betrekking tot accountmachtigingen en toegangssleutels
description: Dit artikel biedt een oplossing voor problemen met de implementatie van Adobe Commerce op cloudinfrastructuur die worden veroorzaakt door een conflict met sleuteleigendom.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Implementatieproblemen met betrekking tot accountmachtigingen en toegangssleutels

Dit artikel biedt een oplossing voor problemen met de implementatie van Adobe Commerce op cloudinfrastructuur die worden veroorzaakt door een conflict met sleuteleigendom.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle ondersteunde versies

## Probleem

<u>Vereisten</u>:

De cloudlicentie is gekoppeld aan contact A (e-mailadres: *<u>first@e.mail</u>*)

<u>Stappen om te reproduceren</u>:

1. Neem contact op met de Adobe Commerce-toegangstoetsen die u hebt gemaakt voor hun account (Key X) en installeer deze op de cloud.
1. Contactpersoon B (e-mailadres: *<u>second@e.mail</u>*) heeft een extensie gekocht met zijn account en de toegangstoetsen gemaakt voor de installatie van de extensie (sleutel Y).
1. Contact A verliet toen het bedrijf, en de vergunning (eigendom) werd dan overgebracht naar Contact B.
1. Systeemintegrator probeert de extensie met Key X in de cloud-omgeving te installeren.

<u>Verwacht resultaat</u>:

De extensie is geïnstalleerd.

<u>Werkelijk resultaat</u>:

De extensie is niet geïnstalleerd omdat de implementatie mislukt.

## Oorzaak

Beide sleutels worden toegewezen aan de contactrol, die een conflict veroorzaakt.

## Oplossing

Als een implementatie is mislukt nadat een wijziging is aangebracht in de primaire contactpersoon op de account (waarbij zowel de oorspronkelijke account als de nieuwe account elk hun eigen toegangstoetsen hebben) en de sleutels zijn overgedragen van de oorspronkelijke account naar de nieuwe account, moet u de sleutels van de oorspronkelijke account uitschakelen. In het bovenstaande voorbeeld moet de toets X worden uitgeschakeld.

### Hoe te om de toegangssleutel onbruikbaar te maken

Als u geen toegang hebt tot de [Commerce Marketplace](https://marketplace.magento.com/) aan de oude sleutel gekoppelde account; [contact opnemen met Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de toets uit te schakelen.

Als u toegang hebt tot het Marketplace-account dat aan de oude toets is gekoppeld, voert u de volgende stappen uit om de toets uit te schakelen:

1. Aanmelden bij de [Commerce Marketplace](https://marketplace.magento.com/) de aanmeldingsgegevens van het oude account gebruiken.
1. Klik op de accountnaam rechtsboven op de pagina en selecteer **Mijn profiel**.
1. Klikken **Toegangssleutels** op het tabblad Marktplaats.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klikken **Uitschakelen** naast de toegangstoets.

## Gerelateerde lezing

* [Uw verificatietoetsen ophalen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html) in onze ontwikkelaarsdocumentatie.
