---
title: Adobe Commerce-probleemoplossing voor implementatie
description: Implementaties en mislukte implementaties op Adobe Commerce kunnen worden opgelost met behulp van het hulpprogramma voor probleemoplossing bij implementatie. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: d2c37f4465d5ba4f4b4878eae292fa805d1dc45b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Adobe Commerce-probleemoplossing voor implementatie

Implementaties en mislukte implementaties op Adobe Commerce kunnen worden opgelost met behulp van het hulpprogramma voor probleemoplossing bij implementatie. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen.

## Stap 1 - verifieer de dienst loopt {#step-1}

+++**is Adobe Commerce op de dienst van de wolkeninfrastructuur omhoog?**

Implementatie van opslagplaatsen - Is Adobe Commerce op de service voor cloudinfrastructuur opgestart? Controle [&#x200B; de Wolk van de Handel van Adobe &#x200B;](https://status.adobe.com/products/3350/).

a. JA - ga aan [&#x200B; Stap 2 &#x200B;](#step-2) te werk.\
b. NO - Onderhoud of mondiale uitvallen. Controleren op geschatte duur en updates.

+++

## Stap 2 - Implementaties in andere omgevingen controleren {#step-2}

+++**zijn er plaatsingen in andere milieu&#39;s die de plaatsing in het bestaande milieu blokkeren?**

Om een lijst van aan de gang zijnde activiteiten te krijgen stel het volgende bevel in werking gebruikend magento-wolk CLI (als u slechts aan één wolkenproject bent toegevoegd). **Nota**: Controle u bent op de recentste versie van magento-wolk CLI. Voor stappen, verwijs naar [&#x200B; Update CLI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/dev-tools/cloud-cli/cloud-cli-overview) in Commerce op de gids van de Infrastructuur van de Wolk.

```bash
magento-cloud --state=in_progress
```

Om een lijst van aan de gang zijnde activiteiten te krijgen stel het volgende bevel in werking gebruikend magento-wolk CLI (als u aan veelvoudige projecten bent toegevoegd):

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

Om informatie over een bestaande plaatsingsactiviteit te vinden (verwijs naar [&#x200B; Controlerend plaatsingslogboek als de Wolk UI &quot;logboek &quot;gesnipte&quot;fout &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) heeft
voor details) kunt u dit bevel in werking stellen om een lopend logboek van die activiteit te verkrijgen:

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a. JA - Los de andere omgeving problemen op die implementatie in de bestaande omgeving blokkeren. Ga aan [&#x200B; Stap 3 &#x200B;](#step-3) te werk.

b. NO - Problemen met de huidige omgeving oplossen. Ga aan [&#x200B; Stap 3 &#x200B;](#step-3) te werk.

+++


## Stap 3 - verifieer SSH op alle knopen {#step-3}

+++**SSH succesvol aan alle knopen?**

a. JA - ga aan [&#x200B; Stap 4 &#x200B;](#step-4) te werk.\
b. NO - [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 4 - verifieer alle diensten die lopen {#step-4}

+++**Alle diensten die lopen?**

a. JA - ga aan [&#x200B; Stap 5 &#x200B;](#step-5) te werk.\
b. NO - [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 5 - De uitvoering van Bitmap controleren {#step-5}

+++**Gebruikend Bitbucket?**

a. JA - controleer [&#x200B; status.bitbucket.com &#x200B;](https://bitbucket.status.atlassian.com/).\
b. NO - de fouten van het plaatsingslogboek van de controle in [&#x200B; bouwt en stelt logboeken &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/test/log-locations) op. Ga aan [&#x200B; Stap 6 &#x200B;](#step-6) te werk.

+++

## Stap 6 - Foutcodes controleren {#step-6}

+++**gemelde code van de Fout?**

a. JA - ga aan [&#x200B; Stap 7 &#x200B;](#step-7) te werk.\
b. NO - ga aan [&#x200B; Stap 8 &#x200B;](#step-8) te werk.

+++

## Stap 7 - 403 Verboden fout {#step-7}

+++**403 Verboden?**

a. JA - ga aan [&#x200B; Stap 16 &#x200B;](#step-16) te werk.
b. NO - ga aan [&#x200B; Stap 9 &#x200B;](#step-9) te werk.

+++

## Stap 8 - Controleren of taken voor uitsnijden worden uitgevoerd {#step-8}

+++**Worden de cron banen momenteel lopend?** Log in door ssh op de vertakking en voer `ps aufxx |grep cron` uit.

a. JA - Log in door ssh op de betrokken vertakking (bijvoorbeeld primair). Kill en ontgrendel banen. Dit zal kroonbanen doden en de status terugstellen. Voer `php vendor/bin/ece-tools cron:kill` uit en vervolgens `php vendor/bin/ece-tools cron:unlock` . Als u bezig was om één milieu in een andere samen te voegen, controleer beide milieu&#39;s op lopende mannetjes.\
b. NO - ga aan [&#x200B; Stap 17 &#x200B;](#step-17) te werk.

+++

## Stap 9 - Toepassing implementeerbaar aan verre clusterfout {#step-9}

+++**Onbekwaam om toepassing aan de verre clusterfout te uploaden?**

a. JA - ga aan [&#x200B; Stap 10 &#x200B;](#step-10) te werk.\
b. NO - ga aan [&#x200B; Stap 11 &#x200B;](#step-11) te werk.

+++

## Stap 10 - Controleer voldoende opslagruimte {#step-10}

+++**Beschikbare opslag oké?**

* [&#x200B; Controle voor het milieu van de Integratie/van de Aanzet &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-integration-environment)
* [&#x200B; Controle voor het Pro Staging/het milieu van de Productie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space?lang=en#check-dedicated-clusters)

a. JA - ga met [&#x200B; Stap 11 &#x200B;](#step-11) te werk.\
b. NO - het Overzicht [&#x200B; beheert schijfruimte &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space).

+++

## Stap 11 - Verifieer schijfruimte {#step-11}

+++**_dossier kon geen Waarschuwing _worden geschreven?**

a. JA

* Voor integratie-/starteromgevingen:

   * Gelieve te verhogen [&#x200B; de schijfwaarde in .magento.app.yaml &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=nl-NL#application-disk-space) en herstelt. Als dit niet werkt, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
   * U kunt ook de map `var/log` controleren en eventuele logbestanden van meer dan 1 MB verwijderen. Voer deze opdracht uit om de bestandsgrootte te controleren:

     ```bash
     ls -la var/log
     ```

* Voor Pro Staging/Production-omgevingen:

   1. Verzend een ondersteuningsticket om opslag toe te voegen.

b. NO - ga met [&#x200B; Stap 12 &#x200B;](#step-12) te werk.

+++

## Stap 12 - Fout bij herimplementatie van omgeving {#step-12}

+++**Ontbroken fout van de Herplaatsing van het Milieu?**

a. JA - ga met [&#x200B; Stap 13 &#x200B;](#step-13) te werk.\
b. NO - ga met [&#x200B; Stap 8 &#x200B;](#step-8) te werk.

+++

## Stap 13 - Controleren of Elasticsearch-upgrade mislukt {#step-13}

+++**Elasticsearch die wordt bevorderd of wordt opgesteld?**

a. JA - Elasticsearch heeft de upgrade niet uitgevoerd. Verwijs naar [&#x200B; de softwareverenigbaarheid van Elasticsearch &#x200B;](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). Als de verbetering van Elasticsearch nog niet werkt, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **Nota**: Op Adobe Commerce op wolkeninfrastructuur, gelieve zich ervan bewust te zijn dat de dienstverbeteringen niet aan het productiemilieu zonder 48 bedrijfsuren&#39; bericht aan ons infrastructuurteam kunnen worden geduwd. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen het gewenste tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn, [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) detailerend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.\
b. NO - ga aan [&#x200B; Stap 14 &#x200B;](#step-14) te werk.

+++

## Stap 14 - Spaties controleren {#step-14}

+++**systeem van het Dossier uit inodes of ruimte?**

a. JA - zie [&#x200B; schijfruimte beheren &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=nl-NL#application-disk-space).\
b. NO - ga aan [&#x200B; Stap 15 &#x200B;](#step-15) te werk.

+++

## Stap 15 - Elasticsearch-versiefout {#step-15}

+++**Fout over Elasticseach versies?**

a. JA - ga aan [&#x200B; Stap 16 &#x200B;](#step-16) te werk.\
b. NO - ga aan [&#x200B; Stap 21 &#x200B;](#step-21) te werk.

+++

## Stap 16 - Verifieer Composer config {#step-16}

+++**Conposer config correct?**

a. JA - ga aan [&#x200B; Stap 10 &#x200B;](#step-10) te werk.\
b. NO - de Webpagina van de Troubleshooter van de Samensteller van het Overzicht [&#128279;](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## Stap 17 - Controleren op langdurige processen {#step-17}

+++**Lange lopende processen(en)?**

a. JA - Identificeer lange lopende processen en dan doodt processen:
1. Voer de volgende opdracht in de terminal uit: `ps aufx`.
1. Zoek de PID van het langdurige proces.
1. Beëindig het proces met `kill -9 <PID>`.

Implementaties bewaken voor opnieuw optreden.

b. NO - ga aan [&#x200B; Stap 18 &#x200B;](#step-18) te werk.

+++

## Stap 18 - Controleren op een storing van de posthaken {#step-18}

+++**de hakenmislukking/hang van het Post?**

a. JA - Gegevensbestand: [&#x200B; vrije schijfruimte &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html?lang=nl-NL#allocate-disk-space), corruptie, onvolledige/bedorven lijsten.\
b. NO - ga aan [&#x200B; Stap 19 &#x200B;](#step-19) te werk.

+++

## Stap 19 - controleer of de plaatsing van de derdeuitbreidingen blokkeert {#step-19}

+++**Gebruikend derdextensies?**

a. JA - probeer [&#x200B; onbruikbaar makend de derdextensies &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure-store/extensions) en in werking stellend de plaatsing (om te zien of zijn zij de oorzaak van het probleem), vooral als er uitbreidingsnamen in om het even welke fouten zijn.\
b. NO - ga aan [&#x200B; Stap 20 &#x200B;](#step-20) te werk.

+++

## Stap 20 - Controle voor langzame vragen {#step-20}

+++**Lange lopende vragen?**

[&#x200B; de langzame vraaglogboek van de Controle en MySQL tonen proceslijst &#x200B;](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a. JA - Vernietig alle slepende vragen. Herzie [&#x200B; Syntaxis van de Kill MySQL.](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b. NO - [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Stap 21 - Elasticsearch-versie downgraden {#step-21}

+++**de versies van Elasticsearch degraderen?**

a. JA - Kan niet door configuratie worden gedaan. [&#x200B; leg een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voor.\
b. NO - [&#x200B; voorlegt een steunkaartje &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[Terug naar stap 1](#step-1)
