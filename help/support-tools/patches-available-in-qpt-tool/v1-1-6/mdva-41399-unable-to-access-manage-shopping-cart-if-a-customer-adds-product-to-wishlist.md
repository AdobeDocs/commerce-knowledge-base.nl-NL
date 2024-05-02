---
title: 'MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt.'
description: Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt

Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers hebben geen toegang tot de pagina Winkelwagentje beheren als een klant een product aan de verlanglijst toevoegt.

<u>Vereisten</u>:

1. Maak twee of meer producten.
1. Maak een klant.
1. Schakel de modus Ontwikkelaar in.

<u>Stappen om te reproduceren</u>:

1. Ga naar Storefront en meld u aan als klant onder de voorwaarden.
1. Voeg een product toe aan de Gewenste lijst.
1. Ga naar het deelvenster Beheer en navigeer naar de bewerkingspagina van de gemaakte klant en klik op de knop **Winkelwagentje beheren** knop.

<u>Verwachte resultaten</u>:

Admin-gebruiker kan het winkelwagentje beheren.

<u>Werkelijke resultaten</u>:

Admin-gebruiker krijgt een foutbericht: *Er is een fout opgetreden. Zie foutenlogboek voor details.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
