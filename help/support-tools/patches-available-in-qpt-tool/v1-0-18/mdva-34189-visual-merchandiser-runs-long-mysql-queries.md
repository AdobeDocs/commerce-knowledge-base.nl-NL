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

Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18 geïnstalleerd is. De patch-id is MDVA-34189. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:** Adobe Commerce op wolkeninfrastructuur 2.3.5-p2

**Compatibel met de versies van Adobe Commerce:** Adobe Commerce op-gebouw en Adobe Commerce op wolkeninfrastructuur 2.3.4-2.4.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De website stelt grote vragen MySQL op de server van de Productie in werking.

<u> Stappen om </u> te reproduceren:

1. Om tot Visuele Merchandiser toegang te hebben ga naar *Admin* sidebar, klik **Catalogus** > **Categorieën**.
1. Laad de **pagina van Categorieën** in het Admin paneel (de aanvankelijke lading van de wortelcategorie) en neem de vragen waar die het uitvoert.

<u> Verwacht resultaat </u>:

Admin **de Categorieën** pagina zouden moeten laden zonder langzame vragen te produceren.

<u> Werkelijk resultaat </u>:

Dit hangt af van uw PHP configuratie. Het gemeenschappelijkste voorbeeld van deze fout is dat de **pagina van de Categorieën** niet en een fout *Fout 503 eerste byteonderbreking* vertoningen opent.

Afwisselend wanneer Adobe Commerce Visuele Merchandiser laadt, voert het een langzame vraag MySQL uit. Deze vraag omvat vele product IDs die binnen aan `ORDER BY FIELD(` wordt opgenomen e `.` entity_id `,  ...)`

in `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in hulpmiddel QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
