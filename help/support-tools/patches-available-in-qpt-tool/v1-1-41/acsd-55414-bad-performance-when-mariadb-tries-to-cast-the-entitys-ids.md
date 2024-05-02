---
title: 'ACSD-55414: Slechte prestaties wanneer MariaDB probeert de machtigys_ids te casten'
description: Pas de ACSD-55414-patch toe om het Adobe Commerce-probleem op te lossen wanneer de MariaDB 'machtigys_ids' probeert om te zetten van string naar integer, wat de herindexering belemmert.
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414: Slechte prestaties wanneer MariaDB probeert het `entitys_ids`

De ACSD-55414-patch verhelpt het probleem waarbij het opnieuw indexeren wordt belemmerd wanneer de MariaDB probeert om te zetten `entitys_ids` van tekenreeks naar geheel getal. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.41 is geïnstalleerd. De patch-id is ACSD-55414. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van opnieuw indexeren worden belemmerd wanneer MariaDB probeert om het `entitys_ids` van tekenreeks naar geheel getal.

<u>Stappen om te reproduceren</u>:

1. Bijwerken `setup/performance-toolkit/profiles/ce/small.xml` door *50000* eenvoudige producten.
1. Genereer dit profiel door opdracht uit te voeren: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Herindex uitvoeren: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Verwachte resultaten</u>:

De herindexering duurt redelijk lang.

<u>Werkelijke resultaten</u>:

Het duurt te lang om de redex te voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
