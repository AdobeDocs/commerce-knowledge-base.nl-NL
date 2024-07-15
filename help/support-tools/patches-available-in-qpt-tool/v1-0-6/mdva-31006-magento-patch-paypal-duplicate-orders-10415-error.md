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

De MDVA-31006-patch verhelpt het probleem dat het gebruik van de PayPal Express-betaling dubbele bestellingen maakt met een fout van 10415. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 geïnstalleerd is. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker wordt niet verzonden naar de pagina met succesmeldingen voor Adobe Commerce-bestellingen, zodat deze de lege pagina vernieuwt en de tweede volgorde wordt geplaatst, hetgeen dubbele bestellingen veroorzaakt.

<u> Eerste vereisten </u>:

* Adobe Commerce is geïnstalleerd.
* Betaling via PayPal Express is geconfigureerd.
* Meld u aan bij de Commerce-beheerder. Ga naar **Opslag** > **Configuratie** > **Verkoop** > **de Methoden van de Betaling** > selecteren **Uitdrukkelijke Controle van de Woorden** > **vormt** > **Geavanceerde Montages** > **de Stap van het Overzicht van de Volgorde 15} > *Nr. 17}.***

<u> Stappen om </u> te reproduceren:

1. Meld u aan als gebruiker.
1. Selecteer een punt en klik **toevoegen aan Kar**.
1. Klik op de kar en klik **ga aan Controle** te werk.
1. Ga naar het venster PayPal Express en voer een betaling uit.
1. U wordt omgeleid naar de pagina Adobe Commerce Order Review.
1. Druk de **knoop van de Orde van de Plaats**.
1. Systeemfout emuleren vanwege problemen met de serverinfrastructuur. De gebruiker ziet een lege pagina.
1. Vernieuw de pagina.

<u> Verwachte resultaten </u>:

* De klant wordt opnieuw gericht aan de pagina van het Overzicht van de Orde en ziet een foutenmelding &quot;*een succesvolle betalingstransactie reeds is voltooid. Gelieve te controleren of is de orde geplaatst.*&quot;
* In payment.log, die zich in `/var/log/payment.log` bevindt, is er een fout 10415, maar er is slechts één bestelling gemaakt.

<u> Ware resultaten </u>:

* Aangezien de klant niet naar de pagina met succesmeldingen voor Adobe Commerce-bestellingen wordt verzonden, vernieuwt deze de lege pagina en wordt een tweede bestelling geplaatst. Er worden dus twee gedupliceerde bestellingen gemaakt.
* In payment.log, dat zich bevindt in `/var/log/payment.log`, is er een fout 10415.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
