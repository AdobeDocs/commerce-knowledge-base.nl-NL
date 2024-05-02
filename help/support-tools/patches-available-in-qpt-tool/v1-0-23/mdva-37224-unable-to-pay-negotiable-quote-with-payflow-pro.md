---
title: '''MDVA-37224: Kan geen "verhandelbaar aanhalingsteken" betalen met PayFlow Pro.'
description: De MDVA-37224-patch verhelpt het probleem wanneer klanten niet kunnen betalen voor een **Negotiable Quote** met Paypal PayFlow Pro. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37224. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224: Kan &quot;verhandelbaar aanhalingsteken&quot; niet betalen met PayFlow Pro

De MDVA-37224-patch verhelpt het probleem wanneer klanten niet kunnen betalen voor een **Onderhandelbare offerte** met PayPal Pro. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 is geïnstalleerd. De patch-id is MDVA-37224. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloudinfrastructuur 2.3.6-p1
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Vereisten</u>:

* Adobe Commerce met geïnstalleerde B2B-module
* Bedrijfsfunctionaliteit ingeschakeld
* **Onderhandelbare offerte** functionaliteit ingeschakeld
* Een bedrijfsgebruiker bestaat
* PayPal PayFlow Pro-betalingsmethode is ingeschakeld en geconfigureerd
* PayPal PayFlow Pro-betalingsmethode is toegestaan voor B2B
* Er zijn 2 producten met verschillende prijzen gecreëerd

<u>Stappen om te reproduceren</u>:

1. Open de Storefront.
1. Toevoegen **Product 1** op de winkelwagentje.
1. Een **Onderhandelbare offerte** for **Product 1**.
1. Toevoegen **Product 2** op de winkelwagentje.
1. Neem bij de beheerder de **Onderhandelbare offerte** gemaakt in Stap 3.
1. Open vanuit de Storefront deze **Onderhandelbare offerte** en doorgaan met afrekenen.
1. Selecteer de **Betalingsmethode** = *PayPal PayFlow Pro* bij de **Controle en betalingen** stap.
1. Plaats de bestelling.

<u>Verwachte resultaten</u>:

* De bestelling wordt correct geplaatst.
* PayPal stuurt e-mail met de juiste gegevens naar de klant, zoals verwacht.

<u>Werkelijke resultaten</u>:

* De webpagina loopt vast en voltooit de volgorde niet.
* PayPal stuurt een bevestiging naar de klant met nulwaarden, vergelijkbaar met dit voorbeeld:

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* 
   * [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
