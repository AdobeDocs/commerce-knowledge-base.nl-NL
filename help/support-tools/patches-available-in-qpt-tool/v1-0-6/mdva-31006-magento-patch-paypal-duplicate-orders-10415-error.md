---
title: 'MDVA-31006: fout 10415 wegens dubbele betaling van PayPal.'
description: De MDVA-31006-patch verhelpt het probleem dat het gebruik van de PayPal Express-betaling dubbele bestellingen maakt met een fout van 10415. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006: fout 10415 wegens dubbele betalingsopdracht

De MDVA-31006-patch verhelpt het probleem dat het gebruik van de PayPal Express-betaling dubbele bestellingen maakt met een fout van 10415. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker wordt niet verzonden naar de pagina met succesmeldingen voor Adobe Commerce-bestellingen, zodat deze de lege pagina vernieuwt en de tweede volgorde wordt geplaatst, hetgeen dubbele bestellingen veroorzaakt.

<u>Vereisten</u>:

* Adobe Commerce is geïnstalleerd.
* Betaling via PayPal Express is geconfigureerd.
* Meld u aan bij de Commerce-beheerder. Ga naar **Winkels** > **Configuratie** > **Verkoop** > **Betalingsmethoden** > selecteren **Afhandeling via PayPal Express** > **Configureren** > **Geavanceerde instellingen** > **Revisiestap bestelling overslaan** > *Nee*.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als gebruiker.
1. Selecteer een item en klik op **Toevoegen aan winkelwagentje**.
1. Klik op het winkelwagentje en klik **Doorgaan naar Afhandeling**.
1. Ga naar het venster PayPal Express en voer een betaling uit.
1. U wordt omgeleid naar de pagina Adobe Commerce Order Review.
1. Druk op **Opdracht plaatsen** knop.
1. Systeemfout emuleren vanwege problemen met de serverinfrastructuur. De gebruiker ziet een lege pagina.
1. Vernieuw de pagina.

<u>Verwachte resultaten</u>:

* De klant wordt omgeleid naar de pagina Order Review (Controle bestellen) en krijgt een foutbericht &quot;*Een geslaagde betalingstransactie is al voltooid. Controleer of de bestelling is geplaatst.*&quot;
* In het bestand payment.log, dat zich bevindt in `/var/log/payment.log`, er is een fout 10415, maar er is slechts één bestelling gemaakt.

<u>Werkelijke resultaten</u>:

* Aangezien de klant niet naar de pagina met succesmeldingen voor Adobe Commerce-bestellingen wordt verzonden, vernieuwt deze de lege pagina en wordt een tweede bestelling geplaatst. Er worden dus twee gedupliceerde bestellingen gemaakt.
* In het bestand payment.log, dat zich bevindt in `/var/log/payment.log`, er is een fout 10415.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
