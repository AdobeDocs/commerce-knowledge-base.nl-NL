---
title: Adobe Commerce vraagt klanten zich aan te melden bij ongeldige koppeling
description: Het artikel bevat een koppeling naar de patch voor een bekend Adobe Commerce 2.3.5-probleem, waarbij klanten worden gevraagd zich aan te melden, maar de koppeling om een bevestigingsbericht opnieuw te verzenden werkt niet.
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce vraagt klanten zich aan te melden bij ongeldige koppeling

Het artikel bevat een koppeling naar de patch voor een bekend Adobe Commerce 2.3.5-probleem, waarbij klanten worden gevraagd zich aan te melden, maar de koppeling om een bevestigingsbericht opnieuw te verzenden werkt niet.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.5

## Probleem

Adobe Commerce vraagt klanten zich aan te melden door dit bericht weer te geven: *&quot;Dit account wordt niet bevestigd. Klik hier om het bevestigingsbericht opnieuw te verzenden.&quot;*. De **Klik hier** De koppeling moet de pagina voor de bevestigingskoppeling verzenden openen, maar is inactief.

## Oplossing

Een patch voor dit probleem is beschikbaar in Adobe Commerce Technical Resources: [Geef de patch voor het verzenden van een e-mailkoppelingenbericht voor Adobe Commerce 2.3.5 opnieuw op](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368). In Adobe Commerce 2.3.6 is een permanente oplossing beschikbaar, die in het vierde kwartaal van 2020 zal worden uitgebracht.

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies over het aanbrengen van een componentpatch.

## Gerelateerde lezing

Artikelen in onze documentatie over ondersteuningskennis en -ontwikkelaars voor bekende problemen van Adobe Commerce 2.3.5:

* [Bekende uitgave van Adobe Commerce 2.3.5: bestellingen van meerdere bestellingen voor virtuele producten](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Bekende kwestie in Adobe Commerce 2.3.5 voor de vergelijking van producten](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5, 2.3.5-p1-patch: probleem met landbetaling](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce vraagt klanten zich aan te melden bij ongeldige koppeling](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Bulkactie product count known issue in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Adobe Commerce 2.3.5 Bekende problemen](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
