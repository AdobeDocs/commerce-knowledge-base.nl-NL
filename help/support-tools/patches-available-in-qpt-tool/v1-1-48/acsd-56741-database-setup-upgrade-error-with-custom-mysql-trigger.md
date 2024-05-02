---
title: 'ACSD-56741: Problemen met fouten met de installatie van databases oplossen met aangepaste MySQL-triggers'
description: Pas ACSD-56741 flard toe om de kwestie van Adobe Commerce te bevestigen waar een foutenmelding *Poging om tot seriecompensatie op waarde van type ongeldig* te toegang te hebben "verschijnt tijdens opstelling:verbetering"wegens een douane MySQL trekker in het gegevensbestand niet verwant aan indexatie en [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Problemen met fouten in de installatie van databases oplossen met aangepaste MySQL-triggers

De ACSD-56741-patch verhelpt het probleem waarbij een foutbericht verschijnt *Arrayverschuiving benaderen bij waarde van type null* verschijnt tijdens `setup:upgrade` vanwege een aangepaste MySQL-trigger in de database die geen verband houdt met indexering en [!DNL MView]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-56741. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutbericht *Arrayverschuiving benaderen bij waarde van type null* verschijnt tijdens `setup:upgrade` vanwege een aangepaste MySQL-trigger in de database die geen verband houdt met indexering en [!DNL MView].

<u>Stappen om te reproduceren</u>:

1. Uitvoeren `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Uitvoeren `php bin/magento c:f`.
1. Uitvoeren `php bin/magento setup:upgrade`.

<u>Verwachte resultaten</u>:

De setup-upgrade wordt zonder fouten voltooid.

<u>Werkelijke resultaten</u>:

De setup-upgrade wordt afgesloten met een foutbericht:

*Waarschuwing: Arrayverschuiving proberen te benaderen bij waarde van type null*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
