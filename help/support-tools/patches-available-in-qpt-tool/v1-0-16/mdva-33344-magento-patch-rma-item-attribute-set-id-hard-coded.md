---
title: 'MDVA-33344 patch: "rma-item" attribute set ID hard-coded'
description: De patch MDVA-33344 verhelpt het probleem waarbij de hard gecodeerde 'rma\_item' entiteit standaard ingestelde ID wordt gebruikt in plaats van de waarde uit de database. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost of zal worden opgelost in Adobe Commerce 2.4.3.
exl-id: 2ef894a3-eea0-4f9f-8d26-984cd408458c
feature: Attributes, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# MDVA-33344 patch: &quot;rma-item&quot; attribute set ID hard-coded

De patch MDVA-33344 verhelpt het probleem waarbij de hard gecodeerde &#39;rma\_item&#39; entiteit standaard ingestelde ID wordt gebruikt in plaats van de waarde uit de database. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost of zal worden opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:** Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `/rest/default/V1/returnsAttributeMetadata` Het eindpunt WebAPI keert leeg resultaat terug, als &quot;rma\_item&quot;entiteit standaard geplaatste identiteitskaart van de entiteitsreeks van de standaardinstallatieID verschillend is.

<u>Stappen om te reproduceren</u>:

Maak een API vraag aan `/rest/default/V1/returnsAttributeMetadata`.

<u>Verwacht resultaat</u>:

Gegevens worden geretourneerd.

<u>Werkelijk resultaat</u>:

Leeg resultaat wordt geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
