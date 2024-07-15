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

De patch MDVA-42969 verhelpt het probleem waarbij de gerelateerde productregel alleen werkt wanneer het klantensegment op iedereen is ingesteld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 geïnstalleerd is. De patch-id is MDVA-42969. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verwante productregel werkt slechts wanneer het klantensegment aan allen wordt geplaatst.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Catalogus** > **regel-Gebaseerde Betrekkingen van het Product** en reeks **toont Verwante Producten** = **regel-Gebaseerd slechts**.
1. Ga naar **Klanten** > **Segmenten** en creeer een nieuw segment: **ben op** van toepassing = **Bezoekers en Geregistreerde Klanten**.
1. Ga naar **de Marketing** > **Verwante Regels van het Product** en creeer een nieuwe regel.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Open het overeenkomende product in de winkel en controleer of de weer te geven producten worden weergegeven.
1. Wijzig de regel die in stap drie wordt gecreeerd en plaats **Segmenten van de Klant** = **Specifieke** > **Segment** van stap twee.
1. Open het overeenkomende product op de winkel.

<u> Verwachte resultaten </u>:

Op regel-Gebaseerde Verwante Producten worden getoond op de winkel voor bezoekers op het product omdat het klantensegment met de volgende configuratie wordt gecreeerd:

**is op** toe = **Bezoekers en Geregistreerde Klanten**

<u> Ware resultaten </u>:

Er worden geen verwante producten weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
