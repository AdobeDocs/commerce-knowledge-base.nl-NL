---
title: '''MDVA-43601: Triggers worden verwijderd uit de tabel ''catalogrule_product_price'' na volledige herindex'''
description: De flard MDVA-43601 lost de kwestie op waar de trekkers uit lijst ` catalogrule_product_price ` na een volledige herindex van catalogrule_rule of ` catalogrule_product ` worden verwijderd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601: Triggers worden verwijderd uit de tabel &quot;catalogrule_product_price&quot; na volledige herindex

De MDVA-43601-patch verhelpt het probleem waarbij triggers worden verwijderd uit `catalogrule_product_price` tabel na een volledige redex van `catalogrule_rule` of `catalogrule_product`. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-43601. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Triggers worden verwijderd uit `catalogrule_product_price` tabel na een volledige redex van `catalogrule_rule` of `catalogrule_product`.

<u>Stappen om te reproduceren</u>:

1. Alle indexen instellen op *Bijwerken op schema*.
1. Controleer de triggers die zijn gemaakt voor `catalogrule_product_price` tabel door de volgende SQL-aanvraag uit te voeren:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Handmatig opnieuw indexeren `catalogrule_rule` of `catalogrule_product` door de volgende opdracht uit te voeren: `bin/magento indexer:reindex catalogrule_rule`
1. Controleer de triggers van `catalogrule_product_price` opnieuw.

<u>Verwachte resultaten</u>:

Triggers in `catalogrule_product_price` tabel blijft behouden na een volledige herindex.

<u>Werkelijke resultaten</u>:

Er zijn geen triggers gevonden voor `catalogrule_product_price` tabel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
