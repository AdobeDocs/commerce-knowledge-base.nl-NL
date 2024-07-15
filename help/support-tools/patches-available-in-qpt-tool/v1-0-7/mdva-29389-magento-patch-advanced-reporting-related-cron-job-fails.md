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

MDVA-29389 flard moeilijke situatie waar met Geavanceerde Rapportering waar `analytics_collect_data` kronjob zegt: &quot;*de Haven moet binnen gastheerparameter (als localhost worden gevormd:3306)*&quot;. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 geïnstalleerd is. De patch-id is MDVA-29389. Het probleem is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4.

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Schakel Geavanceerde rapportage in uw Adobe Commerce-exemplaar in.
1. Voer de volgende query uit om analytics/general/token-waarde in te voegen in de DB:

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. Open het bestand env.php en voeg poort toe aan de hostparameter in de DB-configuratie in de volgende indeling: `'host' => 'hostname:port',`
1. Cache wissen.
1. Voer de `analytics_collect_data` -uitsnijdtaak uit.

<u> Verwachte resultaten </u>:

De `analytics_collect_data` -taak wordt uitgevoerd als de standaardpoort of niet-standaardpoort wordt gebruikt om verbinding te maken met MySQL in env.php.

<u> Ware resultaten </u>:

De `analytics_collect_data` baan werpt een fout &quot;*Haven moet binnen gastheerparameter (als localhost worden gevormd:3306)*&quot;wanneer het gebruiken van een niet-standaardhaven om met MySQL in env.php te verbinden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
