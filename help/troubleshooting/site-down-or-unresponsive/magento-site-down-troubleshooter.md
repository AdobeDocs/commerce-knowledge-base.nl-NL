---
title: Problemen oplossen op de Adobe Commerce-site
description: Klik op elke vraag om de antwoorddetails in elke stap van de probleemoplosser te onthullen.
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Problemen oplossen op de Adobe Commerce-site

Klik op elke vraag om de antwoorddetails in elke stap van de probleemoplosser te onthullen.

## Stap 1 {#step-1}

+++**toont <https://status.adobe.com> om het even welke kwesties?**

a. JA - als u [ Status van Adobe Commerce ](https://status.adobe.com/cloud/experience_cloud) controleerde, en het toonde een kwestie, open a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.\
b. NO - als u [ Status van Adobe Commerce ](https://status.adobe.com/cloud/experience_cloud) controleerde, en het geen kwestie toonde, aan [ Stap 2 ](#step-2) te werk gaat.

+++

## Stap 2 {#step-2}

+++**toont http://status.fastly.com om het even welke kwesties?**

a. JA - als u [[!DNL Fastly]  Status ](https://status.fastly.com/) controleerde en het een kwestie toonde, open a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.\
b. NO - als u [[!DNL Fastly]  Status ](https://status.fastly.com/) controleerde en het geen kwestie toonde, aan [ Stap 3 ](#step-3) te werk gaat.

+++

## Stap 3 {#step-3}

+++**controleer uw website in Webbrowser. Krijgt u een 200 (O.K.) code?**

Om foutencodes in **Firefox** te controleren: Klik het **Open pictogram van het Menu** > **Ontwikkelaar van het Web** > **Hulpmiddelen van de knevel** > **9&rbrace; lusje van het Netwerk** allen **filter >** van de Status **kolom.** Om foutencodes in **Chrome** te controleren: Klik het **Open pictogram van het Menu** > **Meer Hulpmiddelen** > **Hulpmiddelen van de Ontwikkelaar** > **lusje van het Netwerk** > **Alle** filter > **van de Status** kolom.

a. JA - Open a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.\
b. NO - ga aan [ Stap 4 ](#step-4) te werk.

+++

## Stap 4 {#step-4}

+++**welke code van de websitefout u ontving?**

a. Foutcode 500 - Controleer het logboek van `/var/log/platform/` . Als dit gegeven niet de kwestie aan u voorstelt, kunt u a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) openen en de het oplossen van problemeninformatie omvatten u tot nu toe voor verder onderzoek hebt.

b. Foutcode 503 - Logboek controleren van `var/reports` . Als dit gegeven niet de kwestie aan u voorstelt, kunt u a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) openen en de het oplossen van problemeninformatie omvatten u tot nu toe voor verder onderzoek hebt.

c. Code 404 van de fout - stel de volgende vraag in werking: `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` als de vraag een lijst terugkeert, waar `update_exists` de waarde &quot;0&quot;is, verwijs naar [ Fout 404 op alle pagina&#39;s, storefront en Admin, toe te schrijven aan de Staging van de Inhoud ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue) artikel. In alle andere gevallen ga aan [ Stap 5 ](#step-5) te werk.

d. Andere Codes van de Fout - ga aan [ Stap 5 ](#step-5) te werk.

+++

## Stap 5 {#step-5}

+++**is uw plaats langzaam, of het hebben hoge serverlading, hoge lading van cpu, langzame verzoekverwerking, of stroomonderbrekingen in [!DNL MySQL] of Redis?**

a. JA - ga met stappen voor [ die voor aanvallen DDOS van CLI ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli) controleren.\
b. NO - de logboeken van de controle van `/var/log/exception.log` en `/var/log/deploy.log`, en als dit gegeven niet de kwestie aan u voorstelt, ga aan [ Stap 6 ](#step-6) te werk.

+++

## Stap 6 {#step-6}

+++**hebt u plaatsingsfouten of plaatsingsmislukking?**

a. JA - ga aan [ Stap 13 ](#step-13) te werk.\
b. NO - ga aan [ Stap 7 ](#step-7) te werk.

+++

## Stap 7 {#step-7}

+++**hebt u de fouten van de Elasticsearch?**

a. JA - ga met stappen voor [ het controleren Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine) te werk.
b. NO - ga aan [ Stap 8 ](#step-8) te werk.

+++

## Stap 8 {#step-8}

+++**was uw [!DNL MySQL] gegevensbestand die langzame vragen of onjuiste vragen hebben?**

a. JA - ga met [ het controleren langzame vragen en Processen die te lang in  [!DNL MySQL]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) and checking your query structure in this [[!DNL MySQL]  vraagleerprogramma ](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html) nemen.\
b. NO - ga aan [ Stap 9 ](#step-9) te werk.

+++

## Stap 9 {#step-9}

+++**is uw statische inhoud niet beschikbaar?**

a. JA - ga met het raadplegen van het [ Controleren statische inhoud ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment) artikel te werk.\
b. NO - ga aan [ Stap 10 ](#step-10) te werk.

+++

## Stap 10 {#step-10}

+++**ziet u PHP Fatale Fouten in uw logboeken?**

a. JA - ga met het raadplegen van [ Gemeenschappelijke PHP Onherstelbare Fouten en oplossingen ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions) te werk.\
b. NO - ga aan [ Stap 11 ](#step-11) te werk.

+++

## Stap 11 {#step-11}

+++**ziet u terugkerende fouten?**

a. JA - ga met stappen te werk om [ te verifiëren  [!DNL Redis]  ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/redis-session#verify-redis-connection) loopt en voor [[!DNL Redis]  het oplossen van problemen ](https://redis.io/topics/problems).\
b. NO - ga aan [ Stap 12 ](#step-12) te werk.

+++

## Stap 12 {#step-12}

+++**ziet u de fouten van Indexer?**

a. JA - als uw Index door een ander proces wordt gesloten, raadpleeg [ Index wordt gesloten door een ander proces ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/index-is-locked-by-another-process). Als u andere fouten van Indexer hebt, te openen gelieve Ticket van de a [ Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.\
b. NO - Open a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.

+++

## Stap 13 {#step-13}

+++**hebt u kwesties met uw douanemodule(en)?**

a. JA - ga te raadplegen [ Algemene hulp van het oplossen van problemen van de douanemodule ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help).\
b. NO - ga aan [ Stap 14 ](#step-14) te werk.

+++

## Stap 14 {#step-14}

+++**hebt u post-haken mislukkingen?**

a. JA - ga met het controleren van uw [!DNL MySQL] fout in dit [[!DNL MySQL]  de berichtverwijzing van de serverfout ](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) te werk.\
b. NO - ga aan [ Stap 15 ](#step-15) te werk.

+++

## Stap 15 {#step-15}

+++**hebt u kwesties met componentenflarden?**

a. JA - ga aan het raadplegen [ te werk Toepassend een flard neemt uw plaats neer ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down).\
b. NO - ga aan [ Stap 16 ](#step-16) te werk.

+++

## Stap 16 {#step-16}

+++**hebt u SQL gegevensbestandfouten?**

a. JA - ga met het controleren van uw [!DNL MySQL] fout in dit [[!DNL MySQL]  de berichtverwijzing van de serverfout ](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html) te werk.\
b. NO - ga aan [ Stap 17 ](#step-17) te werk.

+++

## Stap 17 {#step-17}

+++**hebt u [!DNL MySQL] gegevensbestand dode sloten of een niet ontvankelijk [!DNL MySQL] gegevensbestand?**

a. JA - ga met het controleren op [!DNL MySQL] imloclocks in dit [ Deadlocks in  [!DNL MySQL] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/deadlocks-in-mysql) artikel.\
b. NO - Open a [ Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) voor verder onderzoek.

+++

[Terug naar stap 1](#step-1)

Klik [ HIER ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram) om het Stroomschema van het Oplossen van problemen van de Plaats te zien onderaan.

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
