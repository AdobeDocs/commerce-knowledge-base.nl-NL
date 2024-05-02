---
title: "MDVA-32313 patch: products added to wishlist with wrong configuration"
description: De flard MDVA-32313 lost de kwestie op waar de configureerbare producten niet correct aan verlanglijst kunnen worden toegevoegd, omdat zij verkeerde configuraties wanneer zij aan verlanglijst worden toegevoegd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313 patch: products added to wishlist with wrong configuration

De flard MDVA-32313 lost de kwestie op waar de configureerbare producten niet correct aan verlanglijst kunnen worden toegevoegd, omdat zij verkeerde configuraties wanneer zij aan verlanglijst worden toegevoegd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.3.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Maak een klant.
1. Meld u aan bij de klantenaccount.
1. Ga naar de **Productaanbieding** pagina.
1. Kies een configureerbaar product (voorbeeld: *configureerbaar\_1* ) en selecteert u de gewenste kleur- en formaatopties op de **Productaanbieding** pagina (**Open de productpagina niet.**).
1. Klik op het pictogram verlanglijst van een ander configureerbaar product (Voorbeeld: *configureerbaar\_2*) op dezelfde pagina zonder opties voor kleur/grootte te selecteren.

<u>Verwachte resultaten</u>:

De *configureerbaar\_2* het product wordt toegevoegd aan de verlanglijst zonder geselecteerde opties, zoals verwacht.

<u>Werkelijke resultaten</u>:

De *configureerbaar\_2* product toegevoegd aan de verlanglijst met de configuratie uit de *configureerbaar\_1* product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
