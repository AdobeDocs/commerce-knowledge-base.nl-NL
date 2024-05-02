---
title: '''MDVA-34886: geen zoekresultaten wanneer kenmerk "weight" wordt gebruikt.'
description: De patch MDVA-34886 lost het probleem op waar het onderzoek resultaten terugkeert wanneer het gewichtattribuut als doorzoekbaar wordt gevormd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
exl-id: e6f33772-0167-4a54-9d62-0ab89edb5d1d
feature: Attributes, Cache, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-34886: geen zoekresultaten bij gebruik van het kenmerk &quot;weight&quot;

De patch MDVA-34886 lost het probleem op waar het onderzoek resultaten terugkeert wanneer het gewichtattribuut als doorzoekbaar wordt gevormd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.2 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Zoekopdracht retourneert wel resultaten wanneer het gewichtskenmerk is geconfigureerd als doorzoekbaar.

<u>Stappen om te reproduceren</u>:

1. Elasticsearch configureren.
1. Navigeren naar **Beheerder** > **Winkels** > **Attributen** > **Product**. Bewerk de **Dikte** kenmerk en het kenmerk instellen **Doorzoekbaar** = *Ja*.
1. Sla het kenmerk op en wis de configuratiecache.
1. Zoek op de voorzijde naar een tekstwaarde (voorbeeld: *zak*).
1. Let erop dat de zoekopdracht geen resultaten oplevert.
1. Het uitzonderingslogboek zal een foutenmelding zoals bevatten:

```php
{"type":"number_format_exception","reason":"For input string: \"bag\""}
```

<u>Verwachte resultaten</u>:

De zoekopdracht retourneert resultaten, zelfs als het gewichtskenmerk is geconfigureerd als doorzoekbaar, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

De zoekopdracht retourneert geen resultaten wanneer het gewichtskenmerk is geconfigureerd als doorzoekbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
