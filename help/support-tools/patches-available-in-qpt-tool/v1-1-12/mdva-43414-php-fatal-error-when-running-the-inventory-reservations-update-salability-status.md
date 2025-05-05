---
title: 'MDVA-43414: PHP fatale fout bij het uitvoeren van "voorraad.reserveringen.updateSalabilityStatus"'
description: De patch MDVA-43414 lost de PHP fatale fout op die voorkomt wanneer het runnen van de &grave; voorraad.reserveringen.updateSalabilityStatus' rijconsument op numerieke SKUs. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43414. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 197c5db1-36bc-41a7-a5ca-f026600da786
feature: Inventory, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-43414: PHP fatale fout bij het uitvoeren van &quot;voorraad.reserveringen.updateSalabilityStatus&quot;

De patch MDVA-43414 lost de fatale fout op die optreedt wanneer de `inventory.reservations.updateSalabilityStatus` rijconsument op numerieke SKU&#39;s wordt uitgevoerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43414. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fatale fout op in PHP wanneer de wachtrijconsument voor &quot;voorraad.reserveringen.updateSalabilityStatus&quot; wordt uitgevoerd op numerieke SKU&#39;s.

<u> Eerste vereisten </u>:

Installeren van inventarismodules.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepaste inventarisbron en wijs deze toe aan een nieuw voorraadbestand.
1. Maak een product met de aangepaste inventarisbron.
1. Zorg ervoor dat productSKU een geheelwaarde is.
1. Plaats een bestelling.
1. Voer de opdracht `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus` uit.

<u> Verwachte resultaten </u>:

De wachtrij wordt zonder fout gestart.

<u> Ware resultaten </u>:

Er treedt een fatale fout op in PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
