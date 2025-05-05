---
title: Implementatieproblemen met betrekking tot accountmachtigingen en toegangssleutels
description: Dit artikel biedt een oplossing voor problemen met de implementatie van Adobe Commerce op cloudinfrastructuur die worden veroorzaakt door een conflict met sleuteleigendom.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Implementatieproblemen met betrekking tot accountmachtigingen en toegangssleutels

Dit artikel biedt een oplossing voor problemen met de implementatie van Adobe Commerce op cloudinfrastructuur die worden veroorzaakt door een conflict met sleuteleigendom.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle ondersteunde versies

## Probleem

<u> Eerste vereisten </u>:

De vergunning van de Wolk wordt geassocieerd met Contact A (e-mailadres: *<u>first@e.mail</u>*)

<u> Stappen om </u> te reproduceren:

1. Neem contact op met de Adobe Commerce-toegangstoetsen die u hebt gemaakt voor hun account (Key X) en installeer deze op de cloud.
1. Contact B (e-mailadres: *<u>second@e.mail</u>*) kocht een uitbreiding gebruikend zijn rekening en creeerde de toegangstoetsen voor het installeren van de uitbreiding (Zeer belangrijke Y).
1. Contact A verliet toen het bedrijf, en de vergunning (eigendom) werd dan overgebracht naar Contact B.
1. Systeemintegrator probeert de extensie met Key X in de cloud-omgeving te installeren.

<u> Verwacht resultaat </u>:

De extensie is geïnstalleerd.

<u> Werkelijk resultaat </u>:

De extensie is niet geïnstalleerd omdat de implementatie mislukt.

## Oorzaak

Beide sleutels worden toegewezen aan de contactrol, die een conflict veroorzaakt.

## Oplossing

Als een implementatie is mislukt nadat een wijziging is aangebracht in de primaire contactpersoon op de account (waarbij zowel de oorspronkelijke account als de nieuwe account elk hun eigen toegangstoetsen hebben) en de sleutels zijn overgedragen van de oorspronkelijke account naar de nieuwe account, moet u de sleutels van de oorspronkelijke account uitschakelen. In het bovenstaande voorbeeld moet de toets X worden uitgeschakeld.

### Hoe te om de toegangssleutel onbruikbaar te maken

Als u geen toegang tot de [ Commerce Marketplace ](https://marketplace.magento.com/) rekening verbonden aan de oude sleutel hebt, [ contacteer de Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om de sleutel gehandicapt te hebben.

Als u toegang hebt tot het Marketplace-account dat aan de oude toets is gekoppeld, voert u de volgende stappen uit om de toets uit te schakelen:

1. Login aan de [ Commerce Marketplace ](https://marketplace.magento.com/) gebruikend de geloofsbrieven van de oude rekening.
1. Klik de rekeningsnaam in het hoogste recht van de pagina en selecteer **Mijn Profiel**.
1. Klik **Sleutels van de Toegang** in het lusje van de Marketplace.

   ![ magento_products_access_keys_2.4.1.png ](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Klik **onbruikbaar maken** naast de toegangssleutel.

## Gerelateerde lezing

* [ krijgt uw authentificatietoetsen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) in onze ontwikkelaarsdocumentatie.
