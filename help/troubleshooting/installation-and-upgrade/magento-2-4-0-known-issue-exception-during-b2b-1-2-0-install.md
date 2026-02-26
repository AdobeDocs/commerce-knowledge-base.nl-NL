---
title: 'Adobe Commerce 2.4.0: uitzondering tijdens installatie B2B 1.2.0'
description: Dit artikel biedt een oplossing voor een bekende Adobe Commerce-probleem voor een uitzondering die tijdens de installatie van B2B 1.2.0 wordt gegenereerd.
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
source-git-commit: 7705b6030d2f0877c228dae1707916ad38c9d587
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce 2.4.0: uitzondering tijdens installatie B2B 1.2.0

Dit artikel bevat een oplossing voor een bekende Adobe Commerce-probleem voor een uitzondering die tijdens `setup:upgrade` wordt gegenereerd bij de installatie van B2B 1.2.0.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.0
* Adobe Commerce over cloudinfrastructuur 2.4.0
* B2B 1.2.0

## Probleem

<u> Stappen om te reproduceren </u>

1. Installeer Adobe Commerce met meer dan één winkel gemaakt.
1. Maak een extra winkel.
1. B2B 1.2.0 installeren.

>[!WARNING]
>
>De upgrade van elke B2B-instantie met meer dan één winkel van een versie onder 1.2.0 of Commerce-instantie onder 2.4.0 wordt ook beïnvloed.

<u> Verwacht resultaat </u>

B2B 1.2.0-installaties.

<u> Werkelijk resultaat </u>

Wanneer `setup:upgrade` wordt uitgevoerd om B2B 1.2.0 te installeren, wordt deze fout weergegeven in de module `PurchaseOrder` :

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## Oplossing

Pas de patch toe die in dit artikel is opgenomen.

## Reparatie

De patch is gekoppeld aan dit artikel en kan zowel in `.composer` - als in `.git` -indeling worden gedownload (nadat u de bestanden hebt uitgepakt).

Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op een van de volgende koppelingen:

* [Composer patch B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git patch B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## Hoe een pleister aanbrengen

<u> Composer-patch </u>

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor composer flardinstructies wordt verstrekt.

<u> Git patch </u>

* Zie [ flarden ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in ontwikkelaarsdocumentatie voor het flardinstructies van de it voor Adobe Commerce op wolkeninfrastructuur toepassen.
* Zie [ Toepassend flarden: De flarden van de Douane ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) in ontwikkelaarsdocumentatie voor de instructies van het git flardflard voor Adobe Commerce.

## Gerelateerde lezing

* [Bekende uitgave van Adobe Commerce 2.4.0: Betalingsmethoden van Braintree worden niet weergegeven bij de afhandeling van meerdere adressen](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Bekende uitgave van Adobe Commerce 2.4.0: Foutbericht dat lokale betalingsmethode selecteert die in sommige landen wordt weergegeven tijdens het afrekenen](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
