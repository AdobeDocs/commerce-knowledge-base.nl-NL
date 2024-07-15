---
title: 2.3.4 Probleemoplossing voor PayPal
description: Dit artikel bevat een correctie voor fouten die tijdens de plaatsing van de bestelling zijn ontvangen bij het selecteren van een gebied in PayPal Express Checkout. Het probleem wordt veroorzaakt door wijzigingen die zijn aangebracht in de Adobe Commerce v2.3.4-release en houdt verband met de manier waarop adresvelden voor PayPal Express-afhandeling worden geparseerd.
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 Probleemoplossing voor PayPal

Dit artikel bevat een correctie voor fouten die tijdens de plaatsing van de bestelling zijn ontvangen bij het selecteren van een gebied in PayPal Express Checkout. Het probleem wordt veroorzaakt door wijzigingen die zijn aangebracht in de Adobe Commerce v2.3.4-release en houdt verband met de manier waarop adresvelden voor PayPal Express-afhandeling worden geparseerd.

## Betrokken versies en producten

* Adobe Commerce op cloudinfrastructuur v2.3.4
* Adobe Commerce op locatie v2.3.4

## Probleem

Er treedt een fout op bij het invoeren van het land en de regio tijdens het plaatsen van de bestelling in PayPal Express Checkout. De kwestie is reproduceerbaar voor om het even welk land waar het gebiedsgebied in de adressectie een tekstgebied (in tegenstelling tot een drop-down menu) is.

<u> Stappen om </u> te reproduceren:

1. Afhandeling via PayPal Express inschakelen.
1. Voeg een product toe aan de winkelwagen als gast of wanneer u bent aangemeld.
1. Ga naar Afrekenen.
1. Selecteer je verzendadres. Bijvoorbeeld, het *VK*. Dan ga een input in het **Staat/Provincie** gebied in. Bijvoorbeeld, *Nottinghamshire*.
1. Klik op de **knoop van de Orde van de Plaats** om orde te plaatsen. U ontvangt een pagina met succesvolle bestellingen en ontvangt een bevestigingsbericht.

<u> Verwacht Resultaat:</u>

De bestelling is geplaatst.

<u> Ware Resultaat:</u>

Wanneer op de volgordeknop wordt geklikt, wordt een fout weergegeven:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Oplossing

Voor Adobe Commerce op-gebouwhandelaren: Pas [ hotfix toe, ](https://magento.com/tech-resources/download#download2353) die van de sectie van Downloads op [ magento.com ](https://magento.com) portaal in Mijn rekening beschikbaar is.

Voor Adobe Commerce op producten met cloudinfrastructuur: Adobe heeft de oplossing opgenomen in de cloudpatches voor Commerce v1.0.2. Gelieve te verwijzen naar [ de versienota&#39;s van de Huur van de Wolk voor de versie van Commerce ](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) in onze ontwikkelaarsdocumentatie om instructies te vinden bij het toepassen van het recentste pakket.

## Hoe de pleister moet worden aangebracht

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Verwante lezing

* [ de informatie van de Versie > de Nota&#39;s van de Versie van Adobe Commerce 2.3.4 > pas de Uitdrukkelijke kwestie van de Afhandeling van PayPal met gebiedspatch voor Adobe Commerce 2.3.4 toe om een kritieke Uitdrukkelijke kwestie van de Afhandeling van PayPal ](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) in onze ontwikkelaarsdocumentatie te richten.
