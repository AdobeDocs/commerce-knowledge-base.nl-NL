---
title: 'Problemen met /tmp-montage oplossen: vol voor Adobe Commerce'
description: Dit artikel biedt een oplossing voor het geval de `-/tmp'-montage vol is, de site mogelijk is ingedrukt en u geen SSH in een knooppunt kunt plaatsen.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Problemen met /tmp-montage oplossen: vol voor Adobe Commerce

Dit artikel biedt een oplossing voor de `/tmp` De montage is vol, de site kan omlaag zijn en u kunt SSH niet in een knooppunt plaatsen.

## Betrokken producten en versies

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Probleem

De `/tmp` het vol zijn van de montage kan tot een waaier van mogelijke symptomen, met inbegrip van de volgende fouten leiden:

* *SQLSTATE[HY000]: Algemene fout: 3 Fout bij schrijven van bestand*
* *Foutcode: 28*
* *Geen ruimte meer op apparaat (28)*
* *error session_start(): failed: No space left on device*
* *FOUT 1 (HY000): Kan niet maken/schrijven naar bestand &#39;/tmp/*
* *SQL-fout: 3, SQLState: HY000*
* *Algemene fout: 1021 schijf vol (/tmp)*
* *Geen toegang tot knooppunt via SSH:*
  *bash: kan geen tijdelijk bestand maken voor dit document: geen ruimte meer over op apparaat*
* *fout: 28 &quot;Geen ruimte meer op apparaat&quot;*
* *mysqld: De schijf is vol en schrijft &#39;/tmp&#39;*
* *[FOUT] mysqld: Schijf vol (/tmp)*
* *SQLSTATE[HY000]: Algemene fout: 1 kan niet maken/schrijven naar bestand &#39;/tmp/&#39;*
* *SQLSTATE[HY000]: Algemene fout: 23 Onvoldoende bronnen bij het openen van bestand &#39;/tmp/&#39;*
* *Fout: 24 &quot;Te veel geopende bestanden&quot;*
* *Fout: 23: onvoldoende bronnen bij openen van bestand*


<u>Stappen om te reproduceren:</u>

Om te controleren hoe vol de `/tmp` de montage is, in CLI schakelaar aan `/tmp` en voer de volgende opdracht uit:

```bash
 df -h
```

<u>Verwacht resultaat</u>:

Minder dan 80%.

<u>Werkelijk resultaat</u>:

Ongeveer 100%.

## Oorzaak

De `/tmp` mount heeft te veel bestanden, die kunnen worden veroorzaakt door:

* Onjuiste SQL-query&#39;s die grote en/of te veel tijdelijke tabellen genereren.
* Services die schrijven naar de `/tmp` directory.
* Databaseback-ups/dumps die nog in de `/tmp` directory.

## Oplossing

Er zijn dingen u kunt doen om één keer wat ruimte vrij te maken en er zijn beste praktijken die zouden verhinderen `\tmp` niet vol te worden.

### Inodes controleren en vrijmaken

Zorg ervoor dat er voldoende inodes beschikbaar zijn. Voer hiertoe de volgende opdracht uit:

```bash
df -i
```

De uitvoer ziet er ongeveer als volgt uit:

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

Controleer of Use% &lt;70% is. De knooppunten zijn gecorreleerd met bestanden. Als u bestanden uit de partitie verwijdert, worden de inodes vrijgemaakt.

### Opslagruimte controleren en vrijmaken

Er zijn verscheidene diensten die dossiers zouden kunnen opslaan aan `/tmp`.

#### MySQL-ruimte inchecken en vrijmaken

Volg de instructies in [MySQL-schijfruimte is te klein voor Adobe Commerce op cloudinfrastructuur > Opslagruimte controleren en vrijmaken](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) in onze kennisbasis voor ondersteuning.

#### Hapdumpen van Elasticsearch controleren

>[!WARNING]
>
>Heapdumps bevatten logboekinformatie die nuttig zou kunnen zijn voor het onderzoeken van kwesties. U kunt overwegen ze ten minste 10 dagen op een aparte locatie op te slaan.

Heapdumps verwijderen (`*.hprof`) met behulp van systeemshell:

```bash
find /tmp/*.hprof -type f -delete
```

Als u geen machtigingen hebt om bestanden te verwijderen die door een andere gebruiker zijn gemaakt (in dit geval Elasticsearch), maar u ziet dat bestanden groot zijn, [een ondersteuningsticket maken](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om ze aan te pakken.

#### Database-dumps/back-ups controleren

>[!WARNING]
>
>De steunen van het gegevensbestand worden gewoonlijk gecreeerd voor een doel. Als u niet zeker weet of het bestand nog steeds nodig is, kunt u het naar een andere locatie verplaatsen in plaats van het te verwijderen.

Controleren `/tmp` for `.sql` of `.sql.gz` en schoonmaken. Deze zijn mogelijk gemaakt met behulp van de &#39;ece-tools&#39; tijdens de back-up of bij het handmatig maken van databasedumps met behulp van de `mysqldump` gebruiken.

### Aanbevolen procedures

Om problemen te voorkomen met `/tmp` de volgende aanbevelingen zijn volledig :

* Gebruik MySQL niet voor zoekopdrachten. Elasticsearch voor onderzoek elimineert gewoonlijk de behoefte aan de meeste zware tijdlijstverwezenlijking. Zie [Adobe Commerce configureren voor gebruik van Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html) in onze ontwikkelaarsdocumentatie.
* Vermijd het uitvoeren van `SELECT` de vraag op kolommen zonder indexen aangezien dit omhoog een grote hoeveelheid tijdelijke schijfruimte gebruikt. U kunt ook de indexen toevoegen.
* Een uitsnede maken om op te schonen `/tmp` door het volgende bevel in CLI in werking te stellen:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Gerelateerde lezing

[MySQL-schijfruimte is te klein voor Adobe Commerce op cloudinfrastructuur](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) in onze kennisbasis voor ondersteuning.
