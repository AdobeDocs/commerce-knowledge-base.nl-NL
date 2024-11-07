---
title: 'MDVA-39993: inventariswijzigingen via API worden niet weerspiegeld in de winkel.'
description: De MDVA-39993-patch lost het probleem op waarbij de inventariswijzigingen die via de API worden uitgevoerd, niet in de winkel worden doorgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 is geïnstalleerd. De patch-id is MDVA-3993. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: inventariswijzigingen via API worden niet weerspiegeld in de winkel

De MDVA-39993-patch lost het probleem op waarbij de inventariswijzigingen die via de API worden uitgevoerd, niet in de winkel worden doorgevoerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 geïnstalleerd is. De patch-id is MDVA-3993. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.3.7-p2, en 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventariswijzigingen die via de API worden uitgevoerd, worden niet weergegeven op de productpagina van de winkel.

<u> Eerste vereisten </u>:

Installeren van inventarismodules.

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor dat de wachtrij is ingesteld op Uitvoeren met uitsnijden en uitsnijden is geïnstalleerd en uitgevoerd.
1. Maak een configureerbaar product (COC001) met twee kleuren (zwart en rood) en twee formaten (M en L).
1. Maak één optie uit voorraad (COC001-rood-M).
1. Laad de configureerbare productpagina in de winkel en klik op elke kleur. Wanneer u **Rood** klikt, zou de grootte **M** moeten worden gekruist omdat het uit voorraad is.
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
1. Laad het configureerbare product vanaf de voorzijde en klik op elke kleur. Merk de grootte **M** op wanneer u op **Rood** klikt.

<u> Verwachte resultaten </u>:

De optie COC001-Red-M wordt niet doorgehaald omdat we deze optie via de API hebben bijgewerkt naar In stock.

<u> Ware resultaten </u>:

De optie COC001-Red-M wordt nog steeds doorgehaald, ook al is deze optie in voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
