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

<u>Stappen om te reproduceren</u> :

1. Afhandeling via PayPal Express inschakelen.
1. Voeg een product toe aan de winkelwagen als gast of wanneer u bent aangemeld.
1. Ga naar Afrekenen.
1. Selecteer je verzendadres. Bijvoorbeeld de *VK* . Voer vervolgens een invoer in het dialoogvenster **Staat/provincie** veld. Bijvoorbeeld: *Nottinghamshire*.
1. Klik op de knop **Opdracht plaatsen** om de volgorde te plaatsen. U ontvangt een pagina met succesvolle bestellingen en ontvangt een bevestigingsbericht.

<u>Verwacht resultaat:</u>

De bestelling is geplaatst.

<u>Werkelijk resultaat:</u>

Wanneer op de volgordeknop wordt geklikt, wordt een fout weergegeven:

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## Oplossing

Voor Adobe Commerce-handelaren in verkoopruimten: [hotfix,](https://magento.com/tech-resources/download#download2353) die beschikbaar is in de sectie Downloads op [magento.com](https://magento.com) in Mijn account.

Voor Adobe Commerce op producten met cloudinfrastructuur: Adobe heeft de oplossing opgenomen in de cloudpatches voor Commerce v1.0.2. Zie [Cloudpatches voor Commerce-releaseopmerkingen](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html?itm_source=devdocs&amp;itm_medium=quick_search&amp;itm_campaign=federated_search&amp;itm_term=cloud%20patche) in onze ontwikkelaarsdocumentatie om instructies te vinden over het toepassen van het recentste pakket.

## Hoe de pleister moet worden aangebracht

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Verwante lezing

* [Release-informatie > Opmerkingen bij de release van Adobe Commerce 2.3.4 > Het probleem met PayPal Express Checkout toepassen met de regionale patch voor Adobe Commerce 2.3.4 om een belangrijk probleem met PayPal Express-afhandeling op te lossen](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue) in onze ontwikkelaarsdocumentatie.
