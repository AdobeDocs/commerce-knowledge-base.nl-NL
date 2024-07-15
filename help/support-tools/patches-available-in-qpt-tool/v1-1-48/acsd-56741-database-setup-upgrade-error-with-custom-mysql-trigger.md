---
title: 'ACSD-56741: Problemen met fouten met de installatie van databases oplossen met aangepaste MySQL-triggers'
description: Pas ACSD-56741 flard toe om de kwestie van Adobe Commerce te bevestigen waar een foutenmelding *Poging tot seriecompensatie op waarde van type null* tijdens opstelling te toegang te hebben:verbetering ` toe te schrijven aan een douane MySQL trekker in het gegevensbestand niet verwant aan indexatie en  [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 97839140-03c5-44f0-ba75-935d62f5bf90
source-git-commit: 7cd830d9ba4af6350a14e0cdb50439d2d07084dc
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741: Problemen met fouten in de installatie van databases oplossen met aangepaste MySQL-triggers

ACSD-56741 flardmoeilijke situatie de kwestie waar een foutenmelding *probeert toegang te hebben tot matrixcompensatie op waarde van type ongeldig* verschijnt tijdens `setup:upgrade` toe te schrijven aan een douaneMySQL trekker in het gegevensbestand niet verwant aan indexatie en [!DNL MView]. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-56741. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutenmelding *die probeert om tot matrixcompensatie op waarde van type ongeldig* toegang te hebben verschijnt tijdens `setup:upgrade` toe te schrijven aan een douaneMySQL trekker in het gegevensbestand niet verwant aan indexatie en [!DNL MView].

<u> Stappen om </u> te reproduceren:

1. Voer `php bin/magento indexer:set-mode schedule` uit.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Voer `php bin/magento c:f` uit.
1. Voer `php bin/magento setup:upgrade` uit.

<u> Verwachte resultaten </u>:

De setup-upgrade wordt zonder fouten voltooid.

<u> Ware resultaten </u>:

De setup-upgrade wordt afgesloten met een foutbericht:

*Waarschuwing: Het proberen om tot matrixcompensatie op waarde van type ongeldig* toegang te hebben.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
