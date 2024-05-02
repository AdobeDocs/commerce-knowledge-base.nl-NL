---
title: '"MDVA-43718: "De consument is niet gemachtigd om tot middelen toegang te hebben"fout verschijnt wanneer het toegang tot van gedeelde catalogus"'
description: De patch MDVA-43718 lost het probleem op waar de fout *consumer geen toegang heeft tot %resources.* wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-43718. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: De fout &quot;De consument is niet gemachtigd om tot middelen toegang te hebben&quot;verschijnt wanneer het toegang tot van gedeelde catalogus

De MDVA-43718-patch lost het probleem op waarbij de fout *de consument heeft geen toegang tot %resources.* wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-43718. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie: *De consument heeft geen toegang tot %resources*.

<u>Stappen om te reproduceren</u>:

1. Een nieuwe integratie maken via Beheer > **Systeem** > **Integratie** > **Integratie toevoegen**.
1. Voeg toegang toe voor de volgende bronnen en activeer de integratie:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog:manage
   * Magento_catalogus:catalogus

1. De integratietoegang gebruiken: `rest/default/V1/sharedCatalog/1`

<u>Verwachte resultaten</u>:

Details van de gedeelde catalogus worden geretourneerd.

<u>Werkelijke resultaten</u>:

De volgende fout wordt geretourneerd:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
