---
title: Adobe Commerce-probleemoplossing voor implementatie
description: Implementaties en mislukte implementaties op Adobe Commerce kunnen worden opgelost met behulp van het hulpprogramma voor probleemoplossing bij implementatie. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Adobe Commerce-probleemoplossing voor implementatie

Implementaties en mislukte implementaties op Adobe Commerce kunnen worden opgelost met behulp van het hulpprogramma voor probleemoplossing bij implementatie. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

## Stap 1 - verifieer de dienst loopt {#step-1}

+++**Is Adobe Commerce op de service voor cloudinfrastructuur opgestart?**

Implementatie van opslagplaatsen - Is Adobe Commerce op de service voor cloudinfrastructuur opgestart? Controleren [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a. JA - Ga door naar [Stap 2](#step-2).\
b. NO - Onderhoud of mondiale uitvallen. Controleren op geschatte duur en updates.

+++

## Stap 2 - Implementaties in andere omgevingen controleren {#step-2}

+++**Zijn er plaatsingen in andere milieu&#39;s die de plaatsing in het bestaande milieu blokkeren?**

Om een lijst van aan de gang zijnde activiteiten te krijgen stel het volgende bevel in werking gebruikend magento-cloud CLI (als u slechts aan één wolkenproject bent toegevoegd):

```bash
magento-cloud --state=in_progress
```

Om een lijst van aan de gang zijnde activiteiten te krijgen stel het volgende bevel in werking gebruikend magento-wolk CLI (als u aan veelvoudige projecten bent toegevoegd):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Om informatie over een bestaande plaatsingsactiviteit te vinden (verwijs naar [Implementatielogbestand controleren als in de gebruikersinterface van Cloud een fout met een &#39;log snipped&#39; is opgetreden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
voor details) kunt u dit bevel in werking stellen om een lopend logboek van die activiteit te verkrijgen:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. JA - Los de andere omgeving problemen op die implementatie in de bestaande omgeving blokkeren. Doorgaan naar [Stap 3](#step-3).

b. NO - Problemen met de huidige omgeving oplossen. Doorgaan naar [Stap 3](#step-3).

+++


## Stap 3 - verifieer SSH op alle knopen {#step-3}

+++**SSH succesvol aan alle knopen?**

a. JA - Ga door naar [Stap 4](#step-4).\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 4 - verifieer alle diensten die lopen {#step-4}

+++**Alle services die worden uitgevoerd?**

a. JA - Ga door naar [Stap 5](#step-5).\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 5 - De uitvoering van Bitmap controleren {#step-5}

+++**Bitemmertje gebruiken?**

a. JA - Controle [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO - Controleer de fouten in het implementatielogboek in het [Logboeken samenstellen en implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). Doorgaan naar [Stap 6](#step-6).

+++

## Stap 6 - Foutcodes controleren {#step-6}

+++**Foutcode gerapporteerd?**

a. JA - Ga door naar [Stap 7](#step-7).\
b. NO - Doorgaan naar [Stap 8](#step-8).

+++

## Stap 7 - 403 Verboden fout {#step-7}

+++**403 Verboden?**

a. JA - Ga door naar [Stap 16](#step-16).
b. NO - Doorgaan naar [Stap 9](#step-9).

+++

## Stap 8 - Controleren of taken voor uitsnijden worden uitgevoerd {#step-8}

+++**Zijn er momenteel taken voor uitsnijden actief?** Aanmelden bij ssh op de vertakking en uitvoeren `ps aufxx |grep cron`.

a. JA - Log in door ssh op de betrokken vertakking (bijvoorbeeld primair). Kill en ontgrendel banen. Dit zal kroonbanen doden en de status terugstellen. Uitvoeren `php vendor/bin/ece-tools cron:kill` en vervolgens `php vendor/bin/ece-tools cron:unlock`. Als u bezig was om één milieu in een andere samen te voegen, controleer beide milieu&#39;s op lopende mannetjes.\
b. NO - Doorgaan naar [Stap 17](#step-17).

+++

## Stap 9 - Toepassing implementeerbaar aan verre clusterfout {#step-9}

+++**Kan toepassing niet uploaden naar externe clusterfout?**

a. JA - Ga door naar [Stap 10](#step-10).\
b. NO - Doorgaan naar [Stap 11](#step-11).

+++

## Stap 10 - Controleer voldoende opslagruimte {#step-10}

+++**Beschikbare opslagruimte**

a. JA - Doorgaan met [Stap 11](#step-11).\
b. NEEN - Evaluatie [Schijfruimte beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## Stap 11 - Verifieer schijfruimte {#step-11}

+++**_bestand kan niet worden geschreven Waarschuwing _?**

a. JA - Gelieve [de schijfwaarde verhogen in .magento.app.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) en opnieuw implementeren. Als dit niet werkt, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Doorgaan met [Stap 12](#step-12).

+++

## Stap 12 - Fout bij herimplementatie van omgeving {#step-12}

+++**Fout bij opnieuw implementeren van omgeving?**

a. JA - Doorgaan met [Stap 13](#step-13).\
b. NO - Doorgaan met [Stap 8](#step-8).

+++

## Stap 13 - de Controle voor de verbetering van de Elasticsearch ontbreekt {#step-13}

+++**Elasticsearch die wordt bevorderd of wordt opgesteld?**

a. JA - upgradestappen voor Elasticsearch mislukt. Zie [Compatibiliteit met Elasticsearch-software](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Als de Elasticsearch upgrade nog steeds niet werkt, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Opmerking**: Op Adobe Commerce over cloudinfrastructuur moet u er rekening mee houden dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen het gewenste tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Dus 48 uur voor het moment dat uw veranderingen in productie moeten zijn, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het gedetailleerd van uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.\
b. NO - Doorgaan naar [Stap 14](#step-14).

+++

## Stap 14 - Spaties controleren {#step-14}

+++**Bestandssysteem heeft geen inodes of ruimte meer?**

a. JA - Zie [Schijfruimte beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b. NO - Doorgaan naar [Stap 15](#step-15).

+++

## Stap 15 - versiefout Elasticsearch {#step-15}

+++**Fout met Elasticseach-versies?**

a. JA - Ga door naar [Stap 16](#step-16).\
b. NO - Doorgaan naar [Stap 21](#step-21).

+++

## Stap 16 - Verifieer Composer config {#step-16}

+++**Composer config correct?**

a. JA - Ga door naar [Stap 10](#step-10).\
b. NEEN - Evaluatie [Webpagina Composer Troubleshooter](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Stap 17 - Controleren op langdurige processen {#step-17}

+++**Langlopende processen(sen)?**

a. JA - Identificeer lange lopende processen en dan doodt processen:
1. Voer de volgende opdracht in de terminal uit: `ps aufx`.
1. Zoek de PID van het langdurige proces.
1. Beëindig het proces gebruikend `kill -9 <PID>`.

Implementaties bewaken voor opnieuw optreden.

b. NO - Doorgaan naar [Stap 18](#step-18).

+++

## Stap 18 - Controleren op een storing van de posthaken {#step-18}

+++**Uitval/hangende nahaak?**

a. JA - Gegevensbestand: [Vrije schijfruimte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space), beschadiging, onvolledige/beschadigde tabellen.\
b. NO - Doorgaan naar [Stap 19](#step-19).

+++

## Stap 19 - controleer of de plaatsing van de derdeuitbreidingen blokkeert {#step-19}

+++**Extensies van derden gebruiken?**

a. JA, probeer het [De extensies van derden uitschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) en het uitvoeren van de plaatsing (om te zien of zijn zij de oorzaak van het probleem), vooral als er uitbreidingsnamen in om het even welke fouten zijn.\
b. NO - Doorgaan naar [Stap 20](#step-20).

+++

## Stap 20 - Controle voor langzame vragen {#step-20}

+++**Langdurige zoekopdrachten?**

[Logbestand voor langzame query&#39;s en de lijst met MySQL-showprocessen controleren](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. JA - Vernietig alle slepende vragen. Controleren [MySQL doodt Syntax.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 21 - Versie Elasticsearch downgraden {#step-21}

+++**Versies van Elasticsearch verlagen?**

a. JA - Kan niet door configuratie worden gedaan. [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)
