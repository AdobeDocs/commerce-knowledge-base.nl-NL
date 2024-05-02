---
title: 'MDVA-28409 patch: Adobe Commerce web server crashing - Out of memory'
description: De patch MDVA-28409 lost het probleem op waarbij de snijtaak voor het verwijderen van aanhalingstekens is gestopt omdat een groot aantal items moet worden verwerkt. Deze patch is beschikbaar wanneer het [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5 is geïnstalleerd.
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409 patch: Adobe Commerce web server crashing - Out of memory

De patch MDVA-28409 lost het probleem op waarbij de snijtaak voor het verwijderen van aanhalingstekens is gestopt omdat een groot aantal items moet worden verwerkt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) versie 1.0.5 is geïnstalleerd.

## Betrokken producten en versies

Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.4 - 2.3.5, 2.4.0

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het probleem is dat er onvoldoende geheugen beschikbaar is voor de uitsnijdtaak vanwege de hoeveelheid gegevens die de taak probeert te verwerken. Symptomen van dit probleem zijn onder andere trage prestaties als gevolg van het hoge schijfgebruik door MySQL en een laag geheugen voor de webserver.

<u>Stappen om te reproduceren:</u>

Voer de volgende query uit om te controleren of er een uitsnijdtaak is die verouderde aanhalingstekens niet kan verwijderen:

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>Verwacht resultaat:</u>

De status van `sales_clean_quotes` snijtaak moet `success`.

<u>Werkelijk resultaat:</u>

De status van `sales_clean_quotes` snijtaak is `running` of `error`.

Een andere manier om te bevestigen dat er een cron baan is die verouderde citaten niet kan verwijderen is de output van de vraag in kaart te brengen uit **Stap 1** (`executed_at`) op de tijdstempels van eventuele geheugenfouten in `/var/log/cron.log`. Als er een uitsnijdtaak is die niet in staat is de hoeveelheid gegevens te verwerken, ziet u mogelijk een bericht zoals:

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
