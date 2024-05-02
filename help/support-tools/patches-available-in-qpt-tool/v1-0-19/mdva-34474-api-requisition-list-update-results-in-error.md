---
title: 'MDVA-34474: Update van API-aanvraaglijst leidt tot een fout'
description: De patch MDVA-34474 verhelpt het probleem dat het toevoegen van een product aan de aanvraaglijst met behulp van API tot een fout leidt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-34474. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474: Update van API-aanvraaglijst resulteert in een fout

De patch MDVA-34474 verhelpt het probleem dat het toevoegen van een product aan de aanvraaglijst met behulp van API tot een fout leidt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 is geïnstalleerd. De patch-id is MDVA-34474. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 - 2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het toevoegen van een product aan de aanvraaglijst met behulp van API resulteert in een fout.

<u>Stappen om te reproduceren</u>:

1. Aanvraaglijst activeren in Admin (**Winkels** > **Configuratie** > **Algemeen** > **B2B-functies** > **Aanvraaglijst inschakelen** = *Ja*).
1. Maak een klant.
1. Creeer een nieuwe verzoeklijst voor deze klant die vraag verzendt ```json    POST rest/all/V1/requisition_lists``` met de json payload bijgevoegd.

<u>Verwachte resultaten</u>:

Geen fout en de lijst wordt gemaakt.

<u>Werkelijke resultaten</u>:

400 fout.

```json
{"message":"Could not save Requisition List"}
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
