---
title: 'MDVA-38852: Catalogusinventarislijsten vergrendelen tabellen die de prestaties verminderen'
description: Met de MDVA-38852-patch wordt het probleem opgelost waarbij de catalogusvoorraad tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38852. De kwestie is opgelost in Adobe Commerce 2.3.6.
exl-id: 6ecee9c8-1f39-47de-8fbc-55e30cc936af
feature: Catalog Management, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-38852: Catalogusinventarislijsten vergrendelen tabellen die de prestaties verminderen

Met de MDVA-38852-patch wordt het probleem opgelost waarbij de catalogusvoorraad tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38852. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met Catalogusinventarisatie worden tabellen vergrendeld voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst.

<u>Stappen om te reproduceren</u>:

1. Voeg een product toe aan de kar.
1. Ga door met de kassa en probeer een bestelling te plaatsen.

<u>Verwachte resultaten</u>:

* Er zijn geen patstellingen.
* De prestaties worden niet verminderd wanneer meerdere parallelle orders worden geplaatst.

<u>Werkelijke resultaten</u>:

* Het plaatsen van een orde is uiterst langzaam wanneer er veelvoudige gezamenlijke gebruikers zijn.
* Er treden fouten op die er als volgt uitzien:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
