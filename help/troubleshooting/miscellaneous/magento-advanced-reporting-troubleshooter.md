---
title: Advanced Reporting troubleshooter voor Adobe Commerce
description: Geavanceerde rapportproblemen op Adobe Commerce kunnen worden opgelost met dit hulpprogramma voor probleemoplossing. Dit omvat Geavanceerde Rapportering die geen gegevens en 404 fouten toont. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Advanced Reporting troubleshooter voor Adobe Commerce

Geavanceerde rapportproblemen op Adobe Commerce kunnen worden opgelost met dit hulpprogramma voor probleemoplossing. Dit omvat Geavanceerde Rapportering die geen gegevens en 404 fouten toont. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

## Stap 1 - bevestig de plaats voldoet aan de Geavanceerde Vereisten van de Rapportering {#step-1}

+++**Voldoet uw website aan de geavanceerde rapportagevereisten?**

U hebt een 404 pagina van de Fout wanneer het gebruiken van Geavanceerde Rapportering. Komt uw website samen [Geavanceerde rapportagevereisten](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)?

a. JA - Ga door naar [Stap 2](#step-2).\
b. NEE - Voltooi de Geavanceerde Rapportagevereisten voor uw plaats door de stappen te volgen in [Geavanceerde rapportagevereisten](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). Ga vervolgens verder met [Stap 2](#step-2).

+++

## Stap 2 - Zijn er orders in meerdere basisvaluta&#39;s? {#step-2}

+++**Worden meerdere basisvaluta&#39;s gebruikt?**

Worden meerdere basisvaluta&#39;s gebruikt (in orders en in configuratie)? Voer deze SQL-opdracht uit om de huidige configuratie te verkrijgen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. JA - als er veelvoudige rijen door de vraag zijn teruggekeerd, kunt u Geavanceerde Rapportering niet gebruiken, aangezien wij slechts één munt steunen.\
b. NO - Output toont slechts één valuta. Voorbeeld: `USD`. Zijn er ooit meerdere basisvaluta&#39;s gebruikt (in orders)? Voer deze SQL-opdracht uit om historische ordergegevens te verkrijgen:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: Dit bevel vereist een volledig lijstaftasten, zodat voor lijsten met hoge aantallen verslagen, dit een prestatieseffect zou kunnen hebben terwijl de vraag uitvoert** om historische ordergegevens te verkrijgen.
Als er meerdere basisvaluta&#39;s zijn gebruikt, kunt u Geavanceerde rapportage niet gebruiken, omdat we slechts één valuta ondersteunen. Als er slechts één valuta wordt weergegeven, gaat u verder met [Stap 3](#step-3).

+++

## Stap 3 - Controleren of gesplitste database in gebruik is {#step-3}

+++**Gebruikt u gesplitste databaseoplossing?**

Gebruikt u [gesplitste databaseoplossing](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)?

a. JA - De pleister gebruiken **26831** in [Advanced Reporting 404-fout bij gesplitste databaseoplossing](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) en cache wissen. Wacht 24 uur voordat de taak opnieuw wordt uitgevoerd en probeer het opnieuw.\
b. NO - Doorgaan naar [Stap 4](#step-4).

+++

## Stap 4 - Bevestig Geavanceerde toegelaten Rapportering {#step-4}

+++**Is Geavanceerde rapportering ingeschakeld?**

Controleren **Beheerder** > **Winkels** > **Instellingen** > **Configuratie** > **Algemeen** > **Geavanceerd**. Voor gedetailleerde stappen, herzie [Geavanceerde rapportage: Geavanceerde rapportage inschakelen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a. JA - Ga door naar [Stap 5](#step-5).\
b) NO - [Geavanceerde rapportage inschakelen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) en bespaar, en wacht 24 uur op Adobe Commerce en Geavanceerde Rapporten om te synchroniseren. Controleer of uw gegevens nu worden geladen. Als dat het geval is, hebt u het probleem opgelost. Indien niet verder wordt gegaan naar [Stap 5](#step-5).

+++

## Stap 5 - Controleren op token {#step-5}

+++**Is er een token?**

Controleer of er een token is door de volgende query uit te voeren: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Is er een token?

a. JA - Ga door naar [Stap 7](#step-7).\
b. NO - Als de symbolische waarde ONGELDIG is of er geen verslag in het gegevensbestand is, ga te werk aan [Stap 6](#step-6).

+++

## Stap 6 - De rij gebruiken {#step-6}

+++**Retourneert de query de rij?**

Controleer de tellerwaarde in vlaglijst door deze vraag in werking te stellen: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Retourneert de query de rij?

a. JA - Voer de volgende stappen uit: 1. Voer de query hieronder uit:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [De module Geavanceerde rapportage uit- en inschakelen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) in instellingen en [de token opnieuw autoriseren](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3 Wacht 24 uur op Adobe Commerce en de Geavanceerde Rapporten om te synchroniseren. Als u nog geen gegevens in Geavanceerde Rapportering kunt zien, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Als de query niets oplevert, voert u de volgende stappen uit: 1. [De module Geavanceerde rapportage uit- en inschakelen](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) in instellingen en [de token opnieuw autoriseren](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\. Wacht 24 uur op Adobe Commerce en de Geavanceerde Rapporten om te synchroniseren. Als u nog geen gegevens in Geavanceerde Rapportering kunt zien, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 7 - Controleren op records in `cron_schedule` table {#step-7}

+++**Zijn er records in de `cron_schedule` tafel?**

Controleer die taak `analytics_collect_data` is uitgevoerd door deze query uit te voeren: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. JA - Indien er gegevens zijn en **status** column: _gemist_, gebruik de pleister in dit KB-artikel [Geavanceerde rapportage bijwerken om op een eigen uitsnijdgroep te worden uitgevoerd](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b) JA - Indien er gegevens zijn en **status** column: _succes_, ga door naar [Stap 9](#step-9).\
c. JA - Indien er gegevens zijn en **status** column: _fout_, ga door naar [Stap 8.](#step-8)\
d. NO - Als er geen gegevens zijn, gaat u verder met [Stap 8](#step-8).

+++

## Stap 8 - Taak controleren in `support_report.log` {#step-8}

+++**Is de taak aangemeld? `support_report.log`?**

Voer de opdracht uit: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. JA - Als de output van de vraag op een succesvolle baan wijst, bijvoorbeeld `Cron Job analytics_collect_data is successfully finished` doorgaan naar [Stap 9](#step-9).\
b. NO - Indien het logboek geen gegevens bevat, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - Als er records zijn maar er een fout is, gaat u verder met [Stap 10](#step-10).

+++

## Stap 9 - Controleren op `data.tgz` file {#step-9}

+++**Hiermee wordt het bestand uitgevoerd `data.tgz` bestaan in het systeem en zijn er verslagen in toegangslogboeken?**

Controleren of het bestand `data.tgz` bestaat, opdracht uitvoeren:

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

Om te controleren dat er verslagen in access.logs zijn, stel bevel in werking:

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a. JA - Als het bestand `data.tgz` is aanwezig en er zijn verslagen in de toegangslogboeken, maar u hebt nog een fout 404, moet u [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Doorgaan naar [Stap 10](#step-10).

+++

## Stap 10 - Controleer het foutbericht {#step-10}

+++**Is er een foutbericht gegenereerd door de uitsnijdtaak?**

Voorbeeld: in het dialoogvenster `core_config_data` tabel die de fout bevat *Het bestand &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0 kan niet worden verwijderd*. Waarschuwing!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Geen dergelijk bestand of deze map*

a. JA - Gebruik de ACSD-50165-patch in [Het bestand kan niet worden verwijderd. Waarschuwing!unlink: bestands- of mapfout is niet beschikbaar in de beheerdersmap](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md), wacht 24 uur totdat de taak opnieuw wordt uitgevoerd en probeer het opnieuw.\
b. NO - Doorgaan naar [Stap 11](#step-11).

+++

## Stap 11 - verifieer of er de fout van de Bouwer van de Pagina is {#step-11}

+++**Is er een fout veroorzaakt door de Bouwer van de Pagina?**

Voorbeeld: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Gebruik de MDVA-19391-pleister in [Algemene fouten met snijtaken in Adobe Commerce melden](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md), wacht 24 uur totdat de taak opnieuw wordt uitgevoerd en probeer het opnieuw.\
b) NO - [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)
