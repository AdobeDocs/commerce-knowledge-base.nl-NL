---
title: 'MDVA-37984: Visuele Merchandiser werkt niet correct wanneer het opvoeren van updates wordt toegepast'
description: De flard MDVA-37984 lost de kwestie op waar de de "product van de Gelijke Merchandiser door regel"functionaliteit niet correct filtert wanneer de het opvoeren updates worden toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-37984. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984: Visuele Merchandiser die niet correct werkt wanneer het opvoeren van updates wordt toegepast

De flard MDVA-37984 lost de kwestie op waar de de &quot;product van de Gelijke Merchandiser door regel&quot;functionaliteit niet correct filtert wanneer de het opvoeren updates worden toegepast. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 is geïnstalleerd. De patch-id is MDVA-37984. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De &quot;product van de Gelijke van de Merchandisator van Visual Merchandiser door regel&quot;functionaliteit filtert correct geen producten wanneer het opvoeren van updates worden toegepast.

<u>Stappen om te reproduceren</u>:

1. Een update voor een bestaand product maken.
   * Verschillende waarden instellen voor `entity_id` en `row_id`.
1. Maak een nieuw configureerbaar product en een eenvoudig product (dus het nieuwe product `entity_id` en `row_ids` zijn ook verschillend).
   * Om het makkelijker te maken om de kwestie te herhalen, plaats een merkbare kwaliteitswaarde voor het eenvoudige product - bijvoorbeeld 5000.
1. Ga naar een categorie > **Producten in categorie** en **Producten op regel afstemmen**.
1. Selecteer nu &quot;Quantity&quot; als kenmerk, &quot;Groter&quot; als operator en &quot;4500&quot; als waarde.
1. Klikken **opslaan**.

<u>Verwachte resultaten</u>:

Het nieuwe configureerbare product wordt vermeld.

<u>Werkelijke resultaten</u>:

Het nieuwe configureerbare product wordt niet vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
