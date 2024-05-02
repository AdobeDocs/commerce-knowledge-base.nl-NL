---
title: '''MDVA-43414: PHP-fout met fatale afloop bij het uitvoeren van "voorraad.reserveringen.updateSalabilityStatus"'
description: De patch MDVA-43414 lost de PHP fatale fout op die voorkomt wanneer het runnen van de ` voorraad.reserveringen.updateSalabilityStatus' rijconsument op numerieke SKUs. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43414. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 197c5db1-36bc-41a7-a5ca-f026600da786
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43414: PHP fatale fout bij het uitvoeren van &quot;voorraad.reserveringen.updateSalabilityStatus&quot;

De MDVA-43414 patch lost de fatale fout op die optreedt bij het uitvoeren van de PHP `inventory.reservations.updateSalabilityStatus` rij consument op numerieke SKUs. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43414. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fatale fout op in PHP wanneer de wachtrijconsument voor &quot;voorraad.reserveringen.updateSalabilityStatus&quot; wordt uitgevoerd op numerieke SKU&#39;s.

<u>Vereisten</u>:

Installeren van inventarismodules.

<u>Stappen om te reproduceren</u>:

1. Maak een aangepaste inventarisbron en wijs deze toe aan een nieuw voorraadbestand.
1. Maak een product met de aangepaste inventarisbron.
1. Zorg ervoor dat productSKU een geheelwaarde is.
1. Plaats een bestelling.
1. Voer de `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus` gebruiken.

<u>Verwachte resultaten</u>:

De wachtrij wordt zonder fout gestart.

<u>Werkelijke resultaten</u>:

Er treedt een fatale fout op in PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
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
