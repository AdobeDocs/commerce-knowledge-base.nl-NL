---
title: "MDVA-40609: Afwezige gegevens van uitgeschakelde producten in catalogusvoorraad_stock_status table"
description: De patch MDVA-40609 lost het probleem op waar de gegevens van gehandicapte producten niet in de "catalogvoorraad_stock_status"indexlijst worden getoond die tot onjuiste producthoeveelheden leidt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40609. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609: Afgeschakelde productgegevens ontbreken in catalogusvoorraad_voorraad_status tabel

Met de MDVA-40609-patch wordt het probleem opgelost waarbij de gegevens over uitgeschakelde producten niet worden weergegeven in het dialoogvenster `cataloginventory_stock_status` indextabel waarin onjuiste producthoeveelheden worden weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40609. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gehandicapte productgegevens worden niet getoond in `cataloginventory_stock_status` indextabel waarin onjuiste producthoeveelheden worden weergegeven.

<u>Vereisten</u>:

De voorraadmodule is geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Stel twee websites in met winkels en winkelweergaven.
1. Maak een extra bron en voorraad.
1. Voeg een eenvoudig product toe:
   * Product inschakelen instellen op *Nee*.
   * Wijs twee bronnen met Source Item Status = Instock en Aantal groter dan nul toe.
1. Sla het product op.
1. Controleer de **Aankoopbare hoeveelheid product** tab.

<u>Verwachte resultaten</u>:

Beide bestanden hebben waarden ingevoerd die groter zijn dan nul.

<u>Werkelijke resultaten</u>:

Eén voorraad heeft een nulwaarde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
