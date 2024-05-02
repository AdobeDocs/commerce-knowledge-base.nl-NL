---
title: 'MDVA-38468: Een foutbericht ontvangen bij het opslaan van CMS-pagina'
description: '''De MDVA-38468 Adobe Commerce-patch verhelpt het probleem waarbij gebruikers het foutbericht krijgen: *Item met dezelfde id bestaat al,* wanneer een CMS-pagina wordt opgeslagen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 is geïnstalleerd. De patch-id is MDVA-38468. Dit probleem is opgelost in Adobe Commerce 2.3.6. "'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468: Ontvang een foutbericht wanneer u CMS-pagina opslaat

De MDVA-38468 Adobe Commerce-patch verhelpt het probleem waarbij gebruikers het foutbericht krijgen: *Item met dezelfde id &quot;PAGE_ID&quot; bestaat al.* bij het opslaan van een CMS-pagina. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26 is geïnstalleerd. De patch-id is MDVA-38468. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**Compatibel met Adobe Commerce-versies:**
Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.2-2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u probeert een CMS-pagina op te slaan, ontvangt u het volgende foutbericht: *Item met dezelfde id &quot;PAGE_ID&quot; bestaat al.*

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website + Winkel + Voorvertoning.
1. Maak nog een website + Winkel + Winkelweergave.
1. Ga naar **Inhoud** > **Hiërarchie** > Voeg een bestaande CMS-pagina toe aan de hiërarchiestructuur.
1. Ga naar **Inhoud** > **Pagina&#39;s** > **Nieuwe pagina toevoegen**:
   * Voeg een titel toe.
   * In de sectie Pagina in websites wijst u beide gemaakte winkels toe.
   * Wijs in de sectie Hiërarchie aan elke gewenste categorie toe.
   * **Opslaan en doorgaan met bewerken**.

<u>Verwachte resultaten</u>:

De pagina wordt zonder fout opgeslagen.

<u>Werkelijke resultaten</u>:

De pagina wordt opgeslagen, maar u krijgt het volgende foutbericht: *Item (Magento\VersionsCms\Model\Hierarchy\Node) met dezelfde id bestaat al &quot;PAGE_ID&quot;.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
