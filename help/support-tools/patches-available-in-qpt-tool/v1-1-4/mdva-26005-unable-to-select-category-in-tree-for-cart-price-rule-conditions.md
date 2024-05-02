---
title: 'MDVA-26005: Kan categorie niet selecteren in boomstructuur voor de voorwaarden van de prijsregel voor winkelwagentjes'
description: Met de MDVA-26005-patch wordt het probleem opgelost waarbij gebruikers geen categorie in de categoriestructuur kunnen selecteren voor de regelvoorwaarden voor winkelwagenprijzen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MDVA-26005. De kwestie is opgelost in Adobe Commerce 2.3.6.
exl-id: d3b8efc3-fd0a-4706-8851-4cecb7d3126a
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-26005: Kan categorie niet selecteren in structuur voor de regelvoorwaarden voor winkelwagentjes

Met de MDVA-26005-patch wordt het probleem opgelost waarbij gebruikers geen categorie in de categoriestructuur kunnen selecteren voor de regelvoorwaarden voor winkelwagenprijzen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 is geïnstalleerd. De patch-id is MDVA-26005. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan geen categorie selecteren in de rubriekstructuur voor de regelvoorwaarden voor winkelwagentjes.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe regel of bewerk een bestaande regel voor winkelprijzen.
1. Ga naar de sectie Actie en kies een categorie in Voorwaarde.
1. Render de categoriestructuur en probeer een categorie te kiezen.

<u>Verwachte resultaten</u>:

Je kunt een rubriek selecteren.

<u>Werkelijke resultaten</u>:

U kunt geen categorie selecteren vanwege een JS-fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
