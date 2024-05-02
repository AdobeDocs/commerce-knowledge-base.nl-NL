---
title: 'MDVA-30945: een fatale fout tijdens het toevoegen en bijwerken van winkelwagentjes'
description: De patch MDVA-30945 lost het probleem op waarbij u een fatale fout *Call aan een lidfunctie getValue() op ongeldig in module-configureerbaar-product CartItemProcessor.php* ontvangt wanneer het bijwerken van kaarten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945: een fatale fout tijdens het toevoegen en bijwerken van winkelwagentjes

De MDVA-30945-patch verhelpt het probleem waarbij een fatale fout optreedt *Aanroep van een lidfunctie getValue() op null in module-configureerbaar-product CartItemProcessor.php* bij het bijwerken van winkelwagentjes. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een fatale PHP fout nadat producten in het winkelwagentje zijn bijgewerkt in Admin.

<u>Stappen om te reproduceren</u>:

1. Maak in Commerce Admin een configureerbaar product zonder opties.
1. Voeg het toe aan het winkelwagentje op de winkel.
1. Ga terug naar Admin, voeg configureerbare opties aan het product toe en sla de veranderingen op.
1. Vernieuw de winkelwagentje pagina.

<u>Verwachte resultaten</u>:

Het volgende validatiebericht wordt weergegeven op de winkelwagentje pagina: *Niet alle onderstaande producten beschikken over alle vereiste opties*.

<u>Werkelijke resultaten</u>:

De startpagina is leeg. In het PHP `error.log`, wordt de volgende fout geregistreerd: *Uncaught exception &#39;Error&#39; met message &#39;Call to a member function getValue() on null&#39; in vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php:76*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
