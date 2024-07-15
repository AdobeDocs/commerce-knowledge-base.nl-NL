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

Het flard MDVA-37224 bevestigt de kwestie wanneer de klanten niet voor a **Negotiable Citate** met Paypal PayFlow Pro kunnen betalen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23 geïnstalleerd is. De patch-id is MDVA-37224. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

* De patch is ontworpen voor Adobe Commerce op cloudinfrastructuur 2.3.6-p1
* De patch is ook compatibel met Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.3-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

* Adobe Commerce met geïnstalleerde B2B-module
* Bedrijfsfunctionaliteit ingeschakeld
* **Negotiable toegelaten functionaliteit van het Citaat**
* Een bedrijfsgebruiker bestaat
* PayPal PayFlow Pro-betalingsmethode is ingeschakeld en geconfigureerd
* PayPal PayFlow Pro-betalingsmethode is toegestaan voor B2B
* Er zijn 2 producten met verschillende prijzen gecreëerd

<u> Stappen om </u> te reproduceren:

1. Open de Storefront.
1. Voeg **Product 1** aan het winkelwagentje toe.
1. Creeer a **Negotiable Citaat** voor **Product 1**.
1. Voeg **Product 2** aan het winkelwagentje toe.
1. Van Admin, keur het **Negotiable Citaat** goed dat in Stap 3 wordt gecreeerd.
1. Van de Storefront, open dit **Negotiable Citaat** en ga aan controle te werk.
1. Selecteer de **Methode van de Betaling** = *PayPal PayFlow Pro* bij de **Controle en de stap van Betalingen**.
1. Plaats de bestelling.

<u> Verwachte resultaten </u>:

* De bestelling wordt correct geplaatst.
* PayPal stuurt e-mail met de juiste gegevens naar de klant, zoals verwacht.

<u> Ware resultaten </u>:

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

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* 
   * [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
