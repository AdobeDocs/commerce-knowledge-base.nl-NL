---
title: 'MDVA-34189: Visuele handelaar stelt lange vragen MySQL in werking'
description: De patch MDVA-34189 lost de kwestie op waar Adobe Commerce grote vragen van Visual Merchandiser wanneer het laden van de Admin categoriepagina uitvoert.
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189: Visuele handelaardiser stelt lange vragen MySQL in werking

De patch MDVA-34189 lost de kwestie op waar Adobe Commerce grote vragen van Visual Merchandiser wanneer het laden van de Admin categoriepagina uitvoert.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 is geïnstalleerd. De patch-id is MDVA-34189. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.5-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De website stelt grote vragen MySQL op de server van de Productie in werking.

<u>Stappen om te reproduceren</u>:

1. Om tot Visuele Merchandiser toegang te hebben ga naar *Beheerder* zijbalk, klikken **Catalogus** > **Categorieën**.
1. Laad de **Categorieën** in het deelvenster Beheer (de eerste hoofdcategorie die wordt geladen) en bekijk de query&#39;s die worden uitgevoerd.

<u>Verwacht resultaat</u>:

De beheerder **Categorieën** Deze pagina moet worden geladen zonder dat er langzame query&#39;s worden gegenereerd.

<u>Werkelijk resultaat</u>:

Dit hangt af van uw PHP configuratie. Het meest voorkomende voorbeeld van deze fout is dat de **Categorieën** pagina wordt niet geopend en er is een fout opgetreden *Fout 503 eerste byte timeout* worden weergegeven.

Afwisselend wanneer Adobe Commerce Visuele Merchandiser laadt, voert het een langzame vraag MySQL uit. Deze query bevat veel product-id&#39;s die zijn ingevoegd in `ORDER BY FIELD(`e`.`entity_id`,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
