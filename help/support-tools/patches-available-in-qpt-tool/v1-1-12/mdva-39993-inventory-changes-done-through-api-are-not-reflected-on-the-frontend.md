---
title: 'MDVA-39993: inventariswijzigingen via API worden niet weerspiegeld in de winkel.'
description: De MDVA-39993-patch lost het probleem op waarbij de inventariswijzigingen die via de API worden uitgevoerd, niet in de winkel worden doorgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-3993. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: inventariswijzigingen via API worden niet weerspiegeld in de winkel

De MDVA-39993-patch lost het probleem op waarbij de inventariswijzigingen die via de API worden uitgevoerd, niet in de winkel worden doorgevoerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-3993. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.3.7-p2, en 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventariswijzigingen die via de API worden uitgevoerd, worden niet weergegeven op de productpagina van de winkel.

<u>Vereisten</u>:

Installeren van inventarismodules.

<u>Stappen om te reproduceren</u>:

1. Zorg ervoor dat de wachtrij is ingesteld op Uitvoeren met uitsnijden en uitsnijden is geïnstalleerd en uitgevoerd.
1. Maak een configureerbaar product (COC001) met twee kleuren (zwart en rood) en twee formaten (M en L).
1. Maak één optie uit voorraad (COC001-rood-M).
1. Laad de configureerbare productpagina in de winkel en klik op elke kleur. Wanneer u op **Rood**, de grootte **M** moeten worden doorgehaald omdat het bestand uit voorraad is.
1. Maak COC001-rood-M in voorraad gebruikend het volgende API eindpunt en de lading:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Controleer dit eenvoudige product vanaf de achtergrond en controleer of het is bijgewerkt naar In Stock.
1. Laad het configureerbare product vanaf de voorzijde en klik op elke kleur. Let op de grootte **M** wanneer u klikt op **Rood**.

<u>Verwachte resultaten</u>:

De optie COC001-Red-M wordt niet doorgehaald omdat we deze optie via de API hebben bijgewerkt naar In stock.

<u>Werkelijke resultaten</u>:

De optie COC001-Red-M wordt nog steeds doorgehaald, ook al is deze optie in voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
