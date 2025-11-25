---
title: Advanced Reporting troubleshooter voor Adobe Commerce
description: Geavanceerde rapportproblemen op Adobe Commerce kunnen worden opgelost met dit hulpprogramma voor probleemoplossing. Dit omvat Geavanceerde Rapportering die geen gegevens en 404 fouten toont. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 3761e9b337ae5b3c07fb23a0bdf191b96efe55ba
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Advanced Reporting troubleshooter voor Adobe Commerce

Geavanceerde rapportproblemen op Adobe Commerce kunnen worden opgelost met dit hulpprogramma voor probleemoplossing. Dit omvat Geavanceerde Rapportering die geen gegevens en 404 fouten toont. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

## Stap 1 - bevestig de plaats voldoet aan de Geavanceerde Vereisten van de Rapportering {#step-1}

+++**voldoet uw website Geavanceerde Rapportagevereisten?**

U hebt een 404 pagina van de Fout wanneer het gebruiken van Geavanceerde Rapportering. Voldoet uw website [&#x200B; Geavanceerde het Melden Vereisten &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)?

a. JA - ga aan [&#x200B; Stap 2 &#x200B;](#step-2) te werk.\
b. NO - voltooi de Geavanceerde Rapportagevereisten voor uw plaats door de stappen in [&#x200B; Geavanceerde Rapportagevereisten &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements) te volgen. Dan, ga aan [&#x200B; Stap 2 &#x200B;](#step-2) te werk.

+++

## Stap 2 - Zijn er orders in meerdere basisvaluta&#39;s? {#step-2}

+++**zijn veelvoudige basismunten gebruikt?**

Worden meerdere basisvaluta&#39;s gebruikt (in orders en in configuratie)? Voer deze [!DNL SQL] -opdracht uit om de huidige configuratie te verkrijgen: `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a. JA - Als de query meerdere rijen retourneert, kunt u **[!UICONTROL Advanced Reporting]** niet gebruiken omdat we slechts één valuta ondersteunen. U zult [&#x200B; Adobe Commerce Intelligence &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/guide-overview) moeten gebruiken. Neem contact op met uw accountteam om dit in te stellen.
b. NO - Output toont slechts één valuta. Voorbeeld: `USD` . Zijn er ooit meerdere basisvaluta&#39;s gebruikt (in orders)? Voer deze opdracht [!DNL SQL] uit om historische ordergegevens te verkrijgen:\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**NOTA: Dit bevel vereist een volledig lijstaftasten, zodat voor lijsten met hoge aantallen verslagen, dit een prestatieseffect zou kunnen hebben terwijl de vraag** uitvoert om historische ordegegevens te verkrijgen.
Als er meerdere basisvaluta&#39;s zijn gebruikt, kunt u Geavanceerde rapportage niet gebruiken, omdat we slechts één valuta ondersteunen. Als de output slechts één munt toont ga aan [&#x200B; Stap 3 &#x200B;](#step-3) te werk.

+++

## Stap 3 - Controleren of gesplitste database in gebruik is {#step-3}

+++**gebruikt u gespleten gegevensbestandoplossing?**

Gebruikt u [&#x200B; gespleten gegevensbestandoplossing &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)?

a. JA - gebruik het flard **MDVA-26831** in Geavanceerde Rapportering 404 fout op gespleten gegevensbestandoplossing en duidelijk geheime voorgeheugen. Wacht 24 uur voordat de taak opnieuw wordt uitgevoerd en probeer het opnieuw.\
b. NO - ga aan [&#x200B; Stap 4 &#x200B;](#step-4) te werk.

+++

## Stap 4 - Bevestig Geavanceerde toegelaten Rapportering {#step-4}

+++**wordt Geavanceerde toegelaten Rapportering?**

Controle **Admin** > **Slaat** > **Montages** > **Configuratie** > **Algemeen** > **Geavanceerde het Melden** op. Voor gedetailleerde stappen, overzicht [&#x200B; Geavanceerde Rapportering: laat Geavanceerde Rapportering &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) toe.

a. JA - ga aan [&#x200B; Stap 5 &#x200B;](#step-5) te werk.\
b. NO - [&#x200B; laat Geavanceerde Rapportering &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) toe en sparen, en wacht 24 uren op Adobe Commerce en Geavanceerde Rapportering om te synchroniseren. Controleer of uw gegevens nu worden geladen. Als dat het geval is, hebt u het probleem opgelost. Als het niet aan [&#x200B; Stap 5 &#x200B;](#step-5) te werk gaat.

+++

## Stap 5 - Controleren op token {#step-5}

+++**is er een teken?**

Controleer of er een token is door de volgende query uit te voeren: `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` Is er een token?

a. JA - ga aan [&#x200B; Stap 7 &#x200B;](#step-7) te werk.\
b. NO - als de symbolische waarde ONGELDIG is of er geen verslag in het gegevensbestand is, ga aan [&#x200B; Stap 6 &#x200B;](#step-6) te werk.

+++

## Stap 6 - De rij gebruiken {#step-6}

+++**keert de vraag de rij terug?**

Controleer de tellerwaarde in de vlaglijst door deze vraag in werking te stellen: ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` Keert de vraag de rij terug?

a. JA - Voer de volgende stappen uit: 1. Voer de query hieronder uit:\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\. [&#x200B; onbruikbaar maken en laat Geavanceerde Meldingsmodule &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in montages toe en [&#x200B; machtigt het teken &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active) opnieuw.\
3 Wacht 24 uur op Adobe Commerce en de Geavanceerde Rapporten om te synchroniseren. Als u nog geen gegevens in Geavanceerde Rapportering kunt zien, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Als de query niets oplevert, voert u de volgende stappen uit: 1. [&#x200B; onbruikbaar maken en laat Geavanceerde Meldingsmodule &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting) in montages toe en [&#x200B; machtigt het teken &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active) opnieuw.\
2\. Wacht 24 uur op Adobe Commerce en de Geavanceerde Rapporten om te synchroniseren. Als u nog geen gegevens in Geavanceerde Rapportering kunt zien, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 7 - Controleren op records in de tabel `cron_schedule` {#step-7}

+++**zijn er verslagen in de `cron_schedule` lijst?**

Controleer of taak `analytics_collect_data` is uitgevoerd door deze query uit te voeren: `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a. JA - als er verslagen zijn en de **status** kolom zegt _gemist_, gebruik het flard in dit KB- artikel Update Geavanceerde Rapportering om op zijn eigen kroongroep in werking te stellen.\
b. JA - als er verslagen zijn en de **status** kolom zegt _succes_, ga aan [&#x200B; Stap 9 &#x200B;](#step-9) te werk.\
c. JA - als er verslagen zijn en de **status** kolom zegt _fout_, ga aan [&#x200B; Stap 8 te werk.](#step-8)\
d. NO - als er geen verslagen zijn, ga aan [&#x200B; Stap 8 &#x200B;](#step-8) te werk.

+++

## Stap 8 - Controleren op taak in `support_report.log` {#step-8}

+++**was de baan het programma geopend `support_report.log`?**

Voer de opdracht uit: `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a. JA - als de output van de vraag op een succesvolle baan wijst, bijvoorbeeld `Cron Job analytics_collect_data is successfully finished` te werk gaat aan [&#x200B; Stap 9 &#x200B;](#step-9).\
b. NO - als er geen verslagen in het logboek zijn, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c. JA - als er verslagen maar er een fout zijn, ga aan [&#x200B; Stap 10 &#x200B;](#step-10) te werk.

+++

## Stap 9 - Controleren op bestand `data.tgz` {#step-9}

+++**bestaat het dossier `data.tgz` in het systeem en zijn er verslagen in toegangslogboeken?**

Als u wilt controleren of het bestand `data.tgz` bestaat, voert u deze opdracht uit. De opdracht retourneert een of meer mappen met een of meer hashnamen:

```
ls -ltr pub/media/analytics/
```

Om te controleren dat er verslagen in access.logs zijn, stel dit bevel in werking:

* Op Commerce Cloud:

  ```
  zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI
  ```

* Vervang bij Op locatie het bestandspad dienovereenkomstig:
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a. JA - als het dossier `data.tgz` aanwezig is en er verslagen in de toegangslogboeken zijn, maar u hebt nog een fout 404, moet u [&#x200B; een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.\
b. NO - ga aan [&#x200B; Stap 10 &#x200B;](#step-10) te werk.

+++

## Stap 10 - Controleer het foutbericht {#step-10}

+++**is er een foutenmelding die door de cron baan wordt geworpen?**

Voorbeeld: In de `cron_schedule` lijst ziet u de fout *&quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0 dossier kan niet worden geschrapt*. Waarschuwing!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a000850c0?lang=en): Geen dergelijk bestand of deze map*

a. JA - gebruik het ACSD-50165 flard in [&#x200B; het dossier kan niet worden geschrapt. Waarschuwing!unlink: Geen dergelijk dossier of folderfout van Admin &#x200B;](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26887), wacht 24 uur op de baan om opnieuw te lopen en dan opnieuw te proberen.\
b. NO - ga aan [&#x200B; Stap 11 &#x200B;](#step-11) te werk.

+++

## Stap 11 - verifieer of er de fout van de Bouwer van de Pagina is {#step-11}

+++**is er een fout die door de Bouwer van de Pagina wordt veroorzaakt?**

Voorbeeld: `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a. JA - Gebruik de MDVA-19391-patch in Common Advanced Reporting cron job errors op Adobe Commerce, wacht 24 uur tot de taak opnieuw wordt uitgevoerd en probeer het opnieuw.\
b. NO - [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)

## Gerelateerde lezing

[&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
