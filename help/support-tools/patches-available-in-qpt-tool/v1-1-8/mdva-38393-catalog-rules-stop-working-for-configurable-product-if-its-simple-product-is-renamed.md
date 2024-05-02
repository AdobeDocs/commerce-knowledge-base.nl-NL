---
title: 'MDVA-38393: De regels van de Catalogus werken niet meer voor configureerbaar product als zijn eenvoudig product wordt hernoemd.'
description: De patch MDVA-38393 verhelpt het probleem waarbij de catalogusregels niet meer werken voor een configureerbaar product als het eenvoudige product een andere naam krijgt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-38393. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393: De regels van de Catalogus werken niet meer voor configureerbaar product als zijn eenvoudig product wordt hernoemd

De patch MDVA-38393 verhelpt het probleem waarbij de catalogusregels niet meer werken voor een configureerbaar product als het eenvoudige product een andere naam krijgt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8 is geïnstalleerd. De patch-id is MDVA-38393. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De regels van de catalogus werken niet meer voor een configureerbaar product als zijn eenvoudig product wordt hernoemd.

<u>Stappen om te reproduceren</u>:

1. Creeer een configureerbaar product met een bijbehorend eenvoudig product.
1. Maak een categorie.
1. Wijs slechts het configureerbare product aan de nieuwe categorie toe.
1. Nieuwe catalogusregels maken:
   * Voorwaarde = categorie bevat \&lt;new category=&quot;&quot; id=&quot;&quot;>
   * Actie = 50% korting
   * Actief = Ja
1. Voer opnieuw index uit.
1. Controleer het configureerbare product op de frontend (de korting zou moeten worden toegepast).
1. Controleer de `catalogrule_product` tabel (het eenvoudige product moet een korting hebben).
1. Ga naar Admin en wijzig de naam van het eenvoudige product. Hiermee voegt u een record toe aan de `catalogrule_product_cl` tabel.
1. De kroon of het `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` gebruiken.
1. Controleer de `catalogrule_product` tabel.

<u>Verwachte resultaten</u>:

Het configureerbare product heeft een korting.

<u>Werkelijke resultaten</u>:

* De kortingsrecords die voor de eenvoudige producten zijn gemaakt, ontbreken in het dialoogvenster `catalogrule_product` tabel.
* Het configureerbare product aan de voorzijde heeft de volledige originele prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
