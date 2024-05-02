---
title: "MDVA-44100: Alle FPT's worden toegewezen aan het laatste product in het winkelwagentje."
description: De MDVA-44100-patch lost het probleem op waarbij alle FPT's zijn toegewezen aan het laatste product in het winkelwagentje. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-44100. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100: alle FPT&#39;s worden toegewezen aan het laatste product in het winkelwagentje

De MDVA-44100-patch lost het probleem op waarbij alle FPT&#39;s zijn toegewezen aan het laatste product in het winkelwagentje. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-44100. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Alle FPT&#39;s worden toegewezen aan het laatste product in het winkelwagentje en de FPT-waarden voor de rest van de producten worden opnieuw ingesteld.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Verkoop** > **Belasting** en instellen:
   * FPT = Ja inschakelen
   * Belasting toepassen op FPT = Ja
   * FPT opnemen in subtotaal = Ja
1. Ga naar **Winkels** > **Kenmerk** > **Product** en maak een nieuw kenmerk met type = Vaste productbelasting.
1. Voeg het kenmerk toe aan een kenmerkset.
1. Maak twee producten van de kenmerkset en configureer het kenmerk FPT voor uw land en staat.
1. Voeg beide punten aan de orde toe.
1. Voer een adres in waarvoor FPT moet worden betaald.
1. Plaats de bestelling.
1. Controleer de lijst met items op de bestelling.

<u>Verwachte resultaten</u>:

De FPT&#39;s worden onder elk product weergegeven.

<u>Werkelijke resultaten</u>:

De FPT-waarden van beide items worden onder het tweede item weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
