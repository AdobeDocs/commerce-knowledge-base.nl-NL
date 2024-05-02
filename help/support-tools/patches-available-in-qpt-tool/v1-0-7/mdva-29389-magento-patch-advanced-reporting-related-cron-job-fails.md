---
title: 'MDVA-29389: Advanced Reporting related cron job failed'
description: '"De flard MDVA-29389 lost het probleem op waar met Geavanceerde Rapportering waar "analytics_collect_data"cronjob zegt: "*Haven moet binnen gastheerparameter worden gevormd (zoals localhost:3306)*". Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De patch-id is MDVA-29389. Het probleem is opgelost in Adobe Commerce 2.4.2. "'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389: Advanced Reporting related cron job failed

Met de MDVA-29389-patch is het probleem verholpen waarbij met Advanced Reporting de `analytics_collect_data` cronjob zegt : &quot;*De haven moet binnen gastheerparameter (als localhost:3306) worden gevormd*&quot;. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 is geïnstalleerd. De patch-id is MDVA-29389. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4.

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Schakel Geavanceerde rapportage in uw Adobe Commerce-exemplaar in.
1. Voer de volgende query uit om analytics/general/token-waarde in te voegen in de DB:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Open env.php en voeg poort toe aan de hostparameter in de DB-configuratie in de volgende indeling: `'host' => 'hostname:port',`
1. Cache wissen.
1. Voer de `analytics_collect_data` snijtaak.

<u>Verwachte resultaten</u>:

De `analytics_collect_data` taak wordt met succes uitgevoerd wanneer de standaardpoort of niet-standaardpoort wordt gebruikt voor het maken van verbinding met MySQL in env.php.

<u>Werkelijke resultaten</u>:

De `analytics_collect_data` taak genereert een fout &quot;*De haven moet binnen gastheerparameter (als localhost:3306) worden gevormd*&quot; als u een niet-standaardpoort gebruikt om verbinding te maken met MySQL in env.php.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
