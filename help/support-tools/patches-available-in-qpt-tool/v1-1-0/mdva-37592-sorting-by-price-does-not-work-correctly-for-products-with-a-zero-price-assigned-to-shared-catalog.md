---
title: "MDVA-37592: Sorteren op prijs zonder producten met prijs nul"
description: De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 is geïnstalleerd. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592: Sorteren op prijs die niet werkt voor producten met prijs nul

De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 is geïnstalleerd. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op onze cloudarchitectuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatietypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Sorteren op prijs werkt niet correct voor producten met prijs nul die aan een gedeelde catalogus wordt toegewezen.

<u>Vereisten</u>:

B2B is geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Gedeelde catalogus inschakelen.
1. Maak vier producten met de volgende prijzen en wijs deze toe aan een categorie: $50, $60, $70 en $80.
1. Maak een gedeelde catalogus met de bovenstaande producten.
1. Stel de aangepaste prijs in op nul voor het product met een prijs van $70.
1. Creëer nu een bedrijfgebruiker en wijs het aan de gedeelde gemaakte catalogus toe.
1. Meld u aan met het bedrijfsaccount en blader naar de categorie waaraan de producten zijn toegewezen.
1. Probeer te sorteren op prijs.

<u>Verwachte resultaten</u>:

Het product met prijs nul wordt correct gesorteerd.

<u>Werkelijke resultaten</u>:

Het product met prijs nul wordt NIET correct gesorteerd. In plaats daarvan wordt het gesorteerd op basis van de oorspronkelijke prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce op locatie: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op onze cloudarchitectuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
