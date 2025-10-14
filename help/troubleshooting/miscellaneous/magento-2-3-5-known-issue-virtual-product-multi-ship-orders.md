---
title: 'Bekende uitgave van Adobe Commerce 2.3.5: bestellingen van meerdere bestellingen voor virtuele producten'
description: In dit artikel wordt een bekend probleem in Adobe Commerce 2.3.5 uitgelegd, waarbij een order met meerdere verzendingen die een virtueel product bevat, niet correct wordt verwerkt.
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 60f68b9edabd13a69e84705b85d84fd10ee6e2be
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Bekende uitgave van Adobe Commerce 2.3.5: bestellingen van meerdere bestellingen voor virtuele producten

In dit artikel wordt een bekend probleem in Adobe Commerce 2.3.5 uitgelegd, waarbij een order met meerdere verzendingen die een virtueel product bevat, niet correct wordt verwerkt.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.5
* Adobe Commerce over wolkeninfrastructuur 2.3.5

## Probleem

<u> Stappen om </u> te reproduceren:

1. Voeg fysieke en virtuele producten aan de winkelwagentje toe.
1. Ga aan controle te werk en **Controle met Veelvoudige Adressen** te selecteren.
1. Voeg alle vereiste informatie toe en plaats de orde.

<u> Verwacht resultaat </u>:

Bestellingen worden voor alle producten correct geplaatst.

<u> Werkelijk resultaat </u>:

De volgorde voor het virtuele product is leeg.

## Repareren

Een oplossing is beschikbaar in Adobe Commerce 2.3.6, dat volgens de planning in het vierde kwartaal van 2020 zal worden uitgebracht.

## Gerelateerde lezing

In onze kennisbasis voor ondersteuning:

* [Bulkactie product count known issue in Adobe Commerce 2.3.5](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

In onze documentatie voor ontwikkelaars:

* [&#x200B; Adobe Commerce 2.3.5 de Nota&#39;s van de Versie &#x200B;](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
