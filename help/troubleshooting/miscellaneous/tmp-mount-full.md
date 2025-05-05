---
title: 'Problemen met /tmp-montage oplossen: vol voor Adobe Commerce'
description: Dit artikel biedt een oplossing voor het geval de &grave;-/tmp'-montage vol is, de site mogelijk is ingedrukt en u geen SSH in een knooppunt kunt plaatsen.
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Problemen met /tmp-montage oplossen: vol voor Adobe Commerce

Dit artikel biedt een oplossing voor het geval dat de `/tmp` -montage vol is, de site mogelijk is ingedrukt en u geen SSH in een knooppunt kunt plaatsen.

## Betrokken producten en versies

* Adobe Commerce 2.3.0 - 2.3.6-p1, 2.4.0 - 2.4.2

## Probleem

Als de `/tmp` -hoeveelheid vol is, kan dit leiden tot een reeks mogelijke symptomen, waaronder de volgende fouten:

* *SQLSTATE [ HY000 ]: Algemene fout: 3 Fout die dossier* schrijft
* *code van de Fout: 28*
* *Geen ruimte verlaten op apparaat (28)*
* *fout session_start (): ontbroken: Geen ruimte verlaten op apparaat*
* *FOUT 1 (HY000): Kan niet tot stand brengen/schrijven aan dossier &#39;/tmp/*
* *SQL Fout: 3, SQLState: HY000*
* *Algemene fout: 1021 volledige Schijf (/tmp)*
* *Onbekwaam om tot knoop via SSH toegang te hebben:*
  *bash: kan geen tijdelijk dossier voor hier-document creëren: Geen ruimte verlaten op apparaat*
* *fout: 28 &quot;Geen ruimte verlaten op apparaat&quot;*
* *mysqld: De schijf is volledig schrijvend &#39;/tmp&#39;*
* *[FOUT ] mysqld: Volledige schijf (/tmp)*
* *SQLSTATE [ HY000 ]: Algemene fout: 1 kan niet tot stand brengen/schrijven aan dossier &quot;/tmp/&quot;*
* *SQLSTATE [ HY000 ]: Algemene fout: 23 uit middelen wanneer het openen van dossier &#39;/tmp/&#39;*
* *Erkenning: 24 &quot;Te veel open dossiers&quot;*
* *Kreeg fout: 23: Uit middelen wanneer het openen van dossier*


<u> Stappen om te reproduceren:</u>

Als u wilt controleren hoe vol de `/tmp` -hoeveelheid is, schakelt u in de CLI over naar `/tmp` en voert u de volgende opdracht uit:

```bash
 df -h
```

<u> Verwacht resultaat </u>:

Minder dan 80%.

<u> Werkelijk resultaat </u>:

Ongeveer 100%.

## Oorzaak

Het `/tmp` -aantal heeft te veel bestanden, die kunnen worden veroorzaakt door:

* Onjuiste SQL-query&#39;s die grote en/of te veel tijdelijke tabellen genereren.
* Services die naar de map `/tmp` schrijven.
* Back-ups/dumps van databases blijven beschikbaar in de map `/tmp` .

## Oplossing

Er zijn dingen die u kunt doen om enige ruimte één keer vrij te maken, en er zijn beste praktijken die `\tmp` zouden verhinderen volledig te worden.

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

Er zijn verschillende services die bestanden kunnen opslaan in `/tmp` .

#### MySQL-ruimte inchecken en vrijmaken

Volg de instructies in [ MySQL schijfruimte is laag op Adobe Commerce op de infrastructuur van de wolk > Controle en bevrijd opslagruimte ](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free) in onze basis van de steunkennis.

#### Hapdumpen van Elasticsearch controleren

>[!WARNING]
>
>Heapdumps bevatten logboekinformatie die nuttig zou kunnen zijn voor het onderzoeken van kwesties. U kunt overwegen ze ten minste 10 dagen op een aparte locatie op te slaan.

Verwijder heapdumps (`*.hprof`) met behulp van systeemshell:

```bash
find /tmp/*.hprof -type f -delete
```

Als u geen toestemmingen hebt om dossiers te schrappen die door een andere gebruiker (in dit geval, Elasticsearch) worden gecreeerd, maar u ziet dat de dossiers groot zijn, te creëren gelieve [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om hen te behandelen.

#### Database-dumps/back-ups controleren

>[!WARNING]
>
>De steunen van het gegevensbestand worden gewoonlijk gecreeerd voor een doel. Als u niet zeker weet of het bestand nog steeds nodig is, kunt u het naar een andere locatie verplaatsen in plaats van het te verwijderen.

Controleer `/tmp` op `.sql` - of `.sql.gz` -bestanden en pas deze op. Deze zijn mogelijk gemaakt met behulp van de versnellingsprogramma&#39;s tijdens een back-up of tijdens het handmatig maken van databasedumps met het gereedschap `mysqldump` .

### Aanbevolen procedures

Volg de onderstaande aanbevelingen om problemen met `/tmp` als vol te voorkomen:

* Gebruik MySQL niet voor zoekopdrachten. Elasticsearch voor onderzoek elimineert gewoonlijk de behoefte aan de meeste zware tijdlijstverwezenlijking. Zie [ Adobe Commerce vormen om Elasticsearch ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/search/configure-search-engine) in onze ontwikkelaarsdocumentatie te gebruiken.
* Vermijd het uitvoeren van de query `SELECT` op kolommen zonder indexen aangezien dit een grote hoeveelheid tijdelijke schijfruimte gebruikt. U kunt ook de indexen toevoegen.
* Maak een uitsnede om op te schonen `/tmp` door de volgende opdracht in de CLI uit te voeren:

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## Gerelateerde lezing

[ MySQL schijfruimte is laag op Adobe Commerce op wolkeninfrastructuur ](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md) in onze basis van steunkennis.
