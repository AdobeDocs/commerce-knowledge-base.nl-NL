---
title: 'ACSD-55004: de validator loopt vast tijdens het uploaden van een bestand dat groter is dan de waarde'
description: Pas de ACSD-55004-patch toe om het Adobe Commerce-probleem te verhelpen waarbij een validator vastloopt tijdens het uploaden van een importbestand dat groter is dan de waarde die in php.ini is geconfigureerd.
feature: Data Import/Export
role: Admin, Developer
exl-id: 03b7667e-9b5b-4319-9135-dbc7fda7861d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-55004: de validatiefunctie crasht tijdens het uploaden van een bestand dat groter is dan de waarde

De ACSD-55004-patch verhelpt het probleem waarbij een validator vastloopt tijdens het uploaden van een importbestand dat groter is dan de waarde die is geconfigureerd in `php.ini`. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.40 is geïnstalleerd. De patch-id is ACSD-55004. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De validator loopt vast tijdens het uploaden van een importbestand dat groter is dan de waarde die is geconfigureerd in `php.ini`.

<u>Stappen om te reproduceren</u>:

Probeer een importbestand te uploaden dat groter is dan geconfigureerd in `php.ini`.

<u>Verwachte resultaten</u>:

De bestandsgrootte wordt zonder fouten gevalideerd.

<u>Werkelijke resultaten</u>:

Validator crasht.

`var/log/exception.log` bevat:

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
