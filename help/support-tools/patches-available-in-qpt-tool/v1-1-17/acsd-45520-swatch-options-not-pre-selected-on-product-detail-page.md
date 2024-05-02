---
title: 'ACSD-45520: Staalopties niet geselecteerd op pagina met productdetails'
description: De ACSD-45520-patch verhelpt het probleem dat staalopties niet vooraf zijn geselecteerd op de pagina met productdetails wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 941f4a45-bc3c-44c0-a582-ddfe179fa8c3
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45520: Staalopties zijn niet geselecteerd op de pagina met productdetails

De ACSD-45520-patch verhelpt het probleem dat staalopties niet vooraf zijn geselecteerd op de pagina met productdetails wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Staalopties worden niet op de pagina met productdetails geselecteerd wanneer een gebruiker configureerbare producten uit de winkelwagentje bewerkt.

<u>Stappen om te reproduceren</u>:

1. Maak een configureerbaar product met productopties (bijvoorbeeld kleur).
1. Voeg het configureerbare product aan de kar toe.
1. Ga naar de pagina Mijn winkelwagentje.
1. Klik op de knop Bewerken op het configureerbare product dat in Stap 1 wordt toegevoegd.
1. Bekijk de productopties op de bewerkingspagina.

<u>Verwachte resultaten</u>:

Er zijn productopties geselecteerd.

<u>Werkelijke resultaten</u>:

Productopties zijn niet geselecteerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
