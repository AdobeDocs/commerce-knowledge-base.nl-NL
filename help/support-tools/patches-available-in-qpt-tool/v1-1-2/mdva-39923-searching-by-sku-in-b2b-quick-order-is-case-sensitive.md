---
title: 'MDVA-39923: Search by SKU in B2B quick order functionaliteit is case-sensitive'
description: De patch MDVA-39923 verhelpt het probleem waarbij klanten een fout krijgen wanneer ze de bestelling via SKU doorzoeken in de functie voor snelle bestelling van B2B met een ander geval dan het geval waarin de naam wordt opgeslagen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39923. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: Onderzoek door SKU in B2B snelle orde functionaliteit is case-sensitive

De patch MDVA-39923 verhelpt het probleem waarbij klanten een fout krijgen wanneer ze de bestelling via SKU doorzoeken in de functie voor snelle bestelling van B2B met een ander geval dan het geval waarin de naam wordt opgeslagen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-39923. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het zoeken door SKU in B2B snelle orde functionaliteit is case-sensitive en toont een fout wanneer een verschillend geval wordt gebruikt dan waarmee SKU wordt bewaard.

<u>Vereisten</u>:

B2B-modules worden geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder en ga naar **Winkels** > **Configuratie** > **B2B**.
1. Inschakelen **Gedeelde catalogus** en **Snelle bestelling**.
1. Een product maken met SKU in hoofdletters, bijvoorbeeld TEST20-1234
1. Maak een product aan de **Gedeelde catalogus**.
1. Meld u aan als klant en klik op **Snelle bestelling**.
1. Voer de SKU in kleine letters in, bijvoorbeeld test20-1234.

<u>Verwachte resultaten</u>:

Het product moet ongeacht het gebruikte geval worden gevonden.

<u>Werkelijke resultaten</u>:

Het volgende foutbericht wordt ontvangen: *1 product(en) vereisen uw aandacht*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
