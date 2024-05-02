---
title: Problemen oplossen op de Adobe Commerce-site
description: Klik op elke vraag om de antwoorddetails in elke stap van de probleemoplosser te onthullen.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Problemen oplossen op de Adobe Commerce-site

Klik op elke vraag om de antwoorddetails in elke stap van de probleemoplosser te onthullen.

## Stap 1 {#step-1}

+++**doet <https://status.adobe.com> problemen tonen?**

a. JA - Als u hebt gecontroleerd [Status Magento Adobe](https://status.adobe.com/products/3350) en het toonde een probleem, open een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.\
b. NO - Als u hebt gecontroleerd [Status Magento Adobe](https://status.adobe.com/products/3350) en er is geen probleem weergegeven, ga door naar [Stap 2](#step-2).

+++

## Stap 2 {#step-2}

+++**Geeft http://status.fastly.com problemen?**

a. JA - Als u hebt gecontroleerd [Snelle status](https://status.fastly.com/) en het toonde een probleem, open een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.\
b. NO - Als u hebt gecontroleerd [Snelle status](https://status.fastly.com/) en er is geen probleem weergegeven, ga door naar [Stap 3](#step-3).

+++

## Stap 3 {#step-3}

+++**Controleer uw website in een webbrowser. Krijg je een 200 (OK) code?**

Om foutcodes te controleren in **Firefox**: Klik op de knop **Menu openen** pictogram > **Webontwikkelaar** > **Gereedschappen in-/uitschakelen** > **Netwerk** tab > **Alles** filter > **Status** kolom. Om foutcodes te controleren in **Chroom**: Klik op de knop **Menu openen** pictogram > **Meer gereedschappen** > **Gereedschappen voor ontwikkelaars** > **Netwerk** tab > **Alles** filter > **Status** kolom.

a. JA - Een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.\
b. NO - Doorgaan naar [Stap 4](#step-4).

+++

## Stap 4 {#step-4}

+++**Welke code van de websitefout ontving u?**

a. Foutcode 500 - Logboek controleren van `/var/log/platform/`. Als deze gegevens de uitgave niet weergeven, kunt u een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en neem de informatie op over het oplossen van problemen die u tot nu toe hebt voor verder onderzoek.

b. Foutcode 503 - Logboek controleren van `var/reports`. Als deze gegevens de uitgave niet weergeven, kunt u een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en neem de informatie op over het oplossen van problemen die u tot nu toe hebt voor verder onderzoek.

c. Foutcode 404 - Voer de volgende query uit: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` Als de query een tabel retourneert, waarbij `update_exists` waarde is &quot;0&quot;, verwijs naar de [Fout 404 op alle pagina&#39;s, opslagront en Admin, wegens de kwestie van de Staging van de Inhoud](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) artikel. In alle andere gevallen: [Stap 5](#step-5).

d. Andere foutcodes - Ga door naar [Stap 5](#step-5).

+++

## Stap 5 {#step-5}

+++**Is uw plaats langzaam, of het hebben hoge serverlading, hoge lading van cpu, langzame verzoekverwerking, of stroomonderbrekingen in MySQL of Redis?**

a. JA - Ga door met stappen voor [Controleren op DDOS-aanvallen van CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b) NO - Logboek controleren van `/var/log/exception.log` en `/var/log/deploy.log`en als deze gegevens de kwestie niet aan u voorleggen, ga te werk aan [Stap 6](#step-6).

+++

## Stap 6 {#step-6}

+++**Hebt u implementatiefouten of implementatiefouten?**

a. JA - Ga door naar [Stap 13](#step-13).\
b. NO - Doorgaan naar [Stap 7](#step-7).

+++

## Stap 7 {#step-7}

+++**Hebt u fouten in de Elasticsearch?**

a. JA - Ga door met stappen voor [Elasticsearch controleren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b. NO - Doorgaan naar [Stap 8](#step-8).

+++

## Stap 8 {#step-8}

+++**Heeft uw MySQL-database langzame query&#39;s of onjuiste query&#39;s?**

a. JA - Doorgaan met [Het controleren van langzame vragen en Processen die te lang in MySQL nemen](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) en de querystructuur in deze [MySQL-queryzelfstudie](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b. NO - Doorgaan naar [Stap 9](#step-9).

+++

## Stap 9 {#step-9}

+++**Is uw statische inhoud niet beschikbaar?**

a. JA - Ga verder met het raadplegen van de [Statische inhoud controleren](https://support.magento.com/hc/en-us/articles/360031624091) artikel.\
b. NO - Doorgaan naar [Stap 10](#step-10).

+++

## Stap 10 {#step-10}

+++**Ziet u PHP Fatale Fouten in uw logboeken?**

a. JA - Ga verder met de raadpleging [Veelvoorkomende fatale fouten en oplossingen in PHP](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b. NO - Doorgaan naar [Stap 11](#step-11).

+++

## Stap 11 {#step-11}

+++**Ziet u Herdis-fouten?**

a. JA - Ga door met stappen naar [Controleren of Redis actief is](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) en voor [Redis-probleemoplossing](https://redis.io/topics/problems).\
b. NO - Doorgaan naar [Stap 12](#step-12).

+++

## Stap 12 {#step-12}

+++**Ziet u Indexerfouten?**

a. JA - Als uw index is vergrendeld door een ander proces, raadpleegt u [Index is vergrendeld door een ander proces](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). Als u andere Indexer-fouten hebt, opent u een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.\
b) NEE - Open een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.

+++

## Stap 13 {#step-13}

+++**Hebt u problemen met uw aangepaste module(s)?**

a. JA - Ga verder met de raadpleging [Algemene hulp bij het oplossen van problemen in de aangepaste module](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b. NO - Doorgaan naar [Stap 14](#step-14).

+++

## Stap 14 {#step-14}

+++**Heb je posthakfouten?**

a. JA - Ga door met het controleren van uw MySQL-fout in dit [MySQL Server error message reference](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Doorgaan naar [Stap 15](#step-15).

+++

## Stap 15 {#step-15}

+++**Hebt u problemen met componentpatches?**

a. JA - Ga door met de raadpleging [Als u een patch toepast, wordt uw site uitgeschakeld](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b. NO - Doorgaan naar [Stap 16](#step-16).

+++

## Stap 16 {#step-16}

+++**Hebt u SQL-databasefouten?**

a. JA - Ga door met het controleren van uw MySQL-fout in dit [MySQL Server error message reference](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b. NO - Doorgaan naar [Stap 17](#step-17).

+++

## Stap 17 {#step-17}

+++**Hebt u MySQL database dode locks of een MySQL database die niet reageert?**

a. JA - Ga verder met controleren op dode MySQL-vergrendelingen in deze [Deadlocks in MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md) artikel.\
b) NEE - Open een [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor verder onderzoek.

+++

[Terug naar stap 1](#step-1)

Klikken [HIER](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) om het Stroomschema van het Oplossen van problemen van de Plaats neer te zien.
