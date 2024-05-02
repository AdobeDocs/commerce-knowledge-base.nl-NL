---
title: 'MDVA-42969: De regel betreffende verwante producten werkt alleen wanneer het klantensegment op alles wordt ingesteld.'
description: De patch MDVA-42969 verhelpt het probleem waarbij de gerelateerde productregel alleen werkt wanneer het klantensegment op iedereen is ingesteld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-42969. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969: Verwante productregel werkt alleen wanneer het klantensegment op alle

De patch MDVA-42969 verhelpt het probleem waarbij de gerelateerde productregel alleen werkt wanneer het klantensegment op iedereen is ingesteld. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 is geïnstalleerd. De patch-id is MDVA-42969. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verwante productregel werkt slechts wanneer het klantensegment aan allen wordt geplaatst.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkels** > **Configuratie** > **Catalogus** > **Op regels gebaseerde productrelaties** en instellen **Verwante producten tonen** = **Alleen op regel gebaseerd**.
1. Ga naar **Klanten** > **Segmenten** en maak een nieuw segment: **Toepassen op** = **Bezoekers en geregistreerde klanten**.
1. Ga naar **Marketing** > **Regels voor verwante producten** en maakt u een nieuwe regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Open het overeenkomende product in de winkel en controleer of de weer te geven producten worden weergegeven.
1. Wijzig de regel die in stap drie is gemaakt en stel de regel in **Klantsegmenten** = **Specifiek** > **Segment** vanaf stap twee.
1. Open het overeenkomende product op de winkel.

<u>Verwachte resultaten</u>:

Op regel-Gebaseerde Verwante Producten worden getoond op de winkel voor bezoekers op het product omdat het klantensegment met de volgende configuratie wordt gecreeerd:

**Toepassen op** = **Bezoekers en geregistreerde klanten**

<u>Werkelijke resultaten</u>:

Er worden geen verwante producten weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
