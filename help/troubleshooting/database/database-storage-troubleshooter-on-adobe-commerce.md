---
title: Problemen met opslagproblemen voor databases op Adobe Commerce oplossen
description: Dit artikel is een hulpprogramma voor het oplossen van problemen voor klanten in Adobe Commerce die problemen hebben met databases. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen en configuratie, zal de probleemoplosser verklaren hoe te om ruimte en configuratiekwesties met gegevensbestanden problemen op te lossen.
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Problemen met opslagproblemen voor databases op Adobe Commerce oplossen

Dit artikel is een hulpprogramma voor het oplossen van problemen voor klanten in Adobe Commerce die problemen hebben met databases. Klik op elke vraag om het antwoord in elke stap van de probleemoplosser te onthullen. Afhankelijk van uw symptomen en configuratie, zal de probleemoplosser verklaren hoe te om ruimte en configuratiekwesties met gegevensbestanden problemen op te lossen.

## Stap 1 - Identificeer de folder met een ruimtekwestie {#step-1}

+++**Heeft u een `/tmp` een probleem dat te wijten is aan een gebrek aan ruimte?**

Dit kan geïndiceerd worden door een reeks symptomen waaronder de `/tmp` koppelen die volledig, plaats neer zijn, of niet in staat om SSH in een knoop te zijn. Er kunnen ook fouten optreden zoals _Geen ruimte meer op apparaat (28)_. Voor een lijst met fouten die het resultaat zijn van `/tmp` volledig zijn, herbekijken [/tmp mount full](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

Of u hebt een `/data/mysql` een probleem dat te wijten is aan een gebrek aan ruimte? Dit kan ook door een verscheidenheid van symptomen zoals plaatsstroomonderbreking, klanten niet kunnen toevoegen producten aan karretje, verbindingsmislukking aan gegevensbestand, en Galeria fouten zoals _SQLSTATE\[08S01\]: Fout bij communicatie-koppeling: 1047 WSREP_. Voor een lijst van fouten die uit lage MySQL schijfruimte voortvloeien, verwijs naar [MySQL-schijfruimte is te klein voor Adobe Commerce op cloudinfrastructuur](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

Als u niet zeker weet of u een probleem hebt met de schijfruimte en u een New Relic-account hebt, gaat u naar [Pagina met hosts voor New Relic-infrastructuurbewaking](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). Klik hier op de knop **Opslag** tabblad, wijzigt u de **Diagrammen** daling neer van 5 tot 20 resultaten, en kijk in de lijst voor hoog schijfgebruik in de Schijf Gebruikte % grafiek of de lijst. Voor meer gedetailleerde stappen raadpleegt u [New Relic Infrastructure Monitoring > Storage tab]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage).

Als u een van de hierboven beschreven symptomen heeft, controleert u de toestand van de inodes om te controleren of dit niet wordt veroorzaakt door problemen met het bestandsnummer. Dit doen stelt het volgende bevel in CLI/Terminal in werking:\
`df -ih`

Is IUse% > 90%?

a. JA - Dit wordt veroorzaakt door te veel bestanden. Controleer de stappen om bestanden veilig te verwijderen in [Bestanden veilig verwijderen wanneer onvoldoende schijfruimte beschikbaar is, Adobe Commerce op cloudinfrastructuur](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). Doorgaan naar [Stap 2](#step-2) nadat u deze stappen hebt voltooid. Als u meer ruimte wilt aanvragen, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO. - Ruimte controleren. Uitvoeren `df -h | grep mysql` en vervolgens `df -h | grep tmp` in CLI/Terminal om het gebruik van de schijfruimte in te controleren `/tmp` en `/data/mysql` mappen. Doorgaan naar [Stap 3](#step-3).

+++

## Stap 2 - Schijfruimte controleren {#step-2}

+++**Schijfruimtegebruik controleren?**

Als u het aantal bestanden hebt verkleind, voert u `df -h | grep mysql` en vervolgens `df -h | grep tmp` in CLI/Terminal om het gebruik van de schijfruimte in te controleren `/tmp` en `/data/mysql`. Is groter dan 70% gebruikt voor `/tmp` of `/data/mysql`?

a. JA - Ga door naar [Stap 3](#step-3).
b. NO - De vraag kan de beschikbare opslag uitputten. Dit kan de knoop crashen, die de vraag doden en verwijdert `tmp` bestanden. Onderzoek de output van `SHOW PROCESSLIST;` in MySQL CLI voor vragen die de oorzaak van het probleem kunnen zijn. [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), waarin om meer ruimte wordt gevraagd.

+++

## Stap 3 - Identificeer directory met hoog gebruik {#step-3}

+++**Welke folder heeft meer dan 70% gebruikt?**

Welke folder heeft meer dan 70% gebruikt? `/tmp` of `/data/mysql`?

>[!NOTE]
>
>Standaard schrijft tmpdir naar de database `/tmp`. Om uw gegevensbestandconfiguratie te controleren is nog op dit gebrek, stel het volgende bevel in MySQL CLI in werking: `SHOW VARIABLES LIKE "TMPDIR";` Als de databasetmpdir nog steeds waarnaar wordt geschreven `/tmp`, ziet u `/tmp` in de kolom Waarde.

a. `/tmp` - Ga door naar [Stap 4](#step-4). \
b. `/data/mysql` - Ga door naar [Stap 5](#step-5).

+++

## Stap 4 - los /tmp volledige onderstel problemen op {#step-4}

+++**Los /tmp volledig probleem op**

[Problemen met /tmp-montage oplossen: vol voor Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md)Blader omlaag in het artikel en probeer de oplossingen en beste praktijken. Dan uitvoeren `df -h | grep mysql` en vervolgens `df -h | grep tmp` in CLI/Terminal om het gebruik van de schijfruimte in te controleren `/tmp` en `/data/mysql` mappen\
  &lt; 70% gebruikt?

>[!NOTE]
>
>De oplossingen in [Problemen met /tmp-montage oplossen: vol voor Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) zijn ontworpen voor handelaren die de variabelen voor database tmpdir niet hebben gewijzigd, waarnaar standaard wordt geschreven `/tmp`. Als u de tmpdir-waarde hebt gewijzigd, worden de instructies in [Problemen met /tmp-montage oplossen: vol voor Adobe Commerce](/help/troubleshooting/miscellaneous/tmp-mount-full.md) helpt niet.

a. JA - U hebt de kwestie opgelost. \
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), waarin om meer ruimte wordt gevraagd.

+++

## Stap 5 - standaard controleren {#step-5}

+++**Standaardwaarde controleren**

Uw databaseconfiguratie bevindt zich mogelijk niet meer op de oorspronkelijke standaard. Vind het gegevensbestand tmpdir config door in MySQL CLI in werking te stellen: `SELECT @@DATADIR;`. Indien `/data/mysql/` is uitgevoerd, schrijft de database-tmpdir nu naar `/data/mysql/`. Vergroot de ruimte in deze map door de stappen in [MySQL-schijfruimte is te klein voor Adobe Commerce in onze cloud-infrastructuur](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). Dan uitvoeren `df -h | grep mysql` en vervolgens `df -h | grep tmp` in CLI/Terminal om het gebruik van de schijfruimte in te controleren `/data/mysql` en `/tmp`.\
  &lt; 70% gebruikt?

a. JA - U hebt de kwestie opgelost. \
b) NO - [Een ondersteuningsticket verzenden](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), waarin om meer ruimte wordt gevraagd.

+++

[Terug naar stap 1](#step-1)
