---
title: MySQL-schijfruimte is te klein voor Adobe Commerce op cloudinfrastructuur
description: Dit artikel biedt oplossingen voor problemen met erg weinig of geen ruimte voor MySQL op Adobe Commerce op cloudinfrastructuur. Symptomen kunnen plaatsstroomonderbrekingen omvatten, klanten kunnen geen producten aan de kar toevoegen, die niet met het gegevensbestand kunnen verbinden, tot het gegevensbestand ver toegang hebben, die niet SSH in knoop kunnen. Symptomen zijn onder andere Galera, Omgevingssync, PHP, Database en Implementatiefouten, zoals hieronder vermeld. Klik [Oplossing] (https://support.magento.com/hc/en-us/articles/360058472572#solution) om rechtstreeks aan de oplossingssectie te springen.
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# MySQL-schijfruimte is te klein voor Adobe Commerce op cloudinfrastructuur

Dit artikel biedt oplossingen voor problemen met erg weinig of geen ruimte voor MySQL op Adobe Commerce op cloudinfrastructuur. Symptomen kunnen plaatsstroomonderbrekingen omvatten, klanten kunnen geen producten aan de kar toevoegen, die niet met het gegevensbestand kunnen verbinden, tot het gegevensbestand ver toegang hebben, die niet SSH in knoop kunnen. Symptomen zijn onder andere Galera, Omgevingssync, PHP, Database en Implementatiefouten, zoals hieronder vermeld. Klikken [Oplossing](https://support.magento.com/hc/en-us/articles/360058472572#solution) rechtstreeks naar de oplossingssectie te gaan.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Probleem

De database wordt te groot. De symptomen kunnen onder andere het verlies van de databaseverbinding, de uploadfout voor de database en diverse andere problemen zijn.

Fouten die u kunt tegenkomen:

Galera:

* *SQLSTATE\[08S01\]: De mislukking van de communicatie verbinding: 1047 WSREP heeft nog geen knoop voor toepassingsgebruik voorbereid*   *Fouten bij importeren:*
* *SQLSTATE\[HY000\]: Algemene fout: 1180 Er is een fout van 5 &quot;Invoer/uitvoerfout&quot; opgetreden.*
* *SQLSTATE\[08S01\]: De mislukking van de communicatie verbinding: 1047 WSREP heeft nog geen knoop voor toepassingsgebruik voorbereid*

Synchronisatiefouten omgeving:

* *SQLSTATE: Algemene fout: 1180 Er is fout 5 &quot;Input/output error&quot; opgetreden tijdens COMMIT*

PHP-fouten:

* *php: BOB::\_\_construct(): MySQL-server is verdwenen.*
* *php-fouten: BOB::\_\_construct(): fout bij het lezen van wenspakket. PID=NNNN.*
* *FOUT 2013 (HY000): Verbinding met MySQL-server bij het lezen van het eerste communicatiepakket is verbroken, systeemfout: 0 &quot;Interne fout/controle (Geen systeemfout)&quot;.*

Database-fouten:

* *Fout\_code: 1114*
* *InnoDB: fout (onvoldoende schijfruimte) bij het schrijven van een woordknooppunt naar de aanvullende indextabel van FTS.*
* *SQLSTATE\[HY000\]: Algemene fout: MySQL-server van 2006 is verdwenen*
* *\[ERROR\] Slave SQL: Fout &#39;The table `<table\_name>` is volledig&#39; op vraag.*
* *De ingevoerde status van de eenheid mysql.service is mislukt.*
* *fout: &#39;Kan geen verbinding maken met lokale MySQL-server via socket &#39;/var/run/mysqld/mysqld.sock&#39; (111 &quot;Verbinding geweigerd&quot;)*
* *1205 Time-out vergrendelen overschreden; probeer transactie opnieuw te starten, query was: INSERT INTO \&quot;cron\_planning\&quot; (\&quot;job\_code\&quot;, \&quot;status\&quot;, \&quot;created\_at\&quot;, \&quot;scheduled\_at\&quot;) VALUES (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Implementatiefouten:

* *E: Command &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_Implementation.sh&#39;\]&#39; heeft een status geretourneerd die niet gelijk is aan nul 255*
* *E: Opdracht &#39;\[&#39;ssh&#39;, u`<node IP address>`, &#39;sudo /usr/bin/sv -w 30 site opnieuw starten-`<environment name>`g-nginx&#39;\]&#39; retourneert niet-nul*
* *Schema bijwerken.. SQLSTATE\[HY000\]: Algemene fout: 1114 De tabel `<table\_name>` is vol*
* *SQLSTATE\[HY000\]: Algemene fout: 3 Fout bij schrijven van bestand./`<environment name>`/\#*
* *B: `<filename>` (foutcode: 28 &quot;Geen ruimte meer over op apparaat&quot;)*  *Indexeringsfouten (samen met zwevende tijdelijke .ibd-bestanden in /tmp):*
* *Er wordt een uitzondering gegenereerd in de indexfunctie Catalogusregel. De tijdelijke lijsten worden niet schoongemaakt in de nasleep en dan vult de schijf op de huidige MySQL hoofdknoop*

<u>Stappen om te reproduceren</u>:

Een van de manieren waarop u kunt controleren of de `/data/mysql` (of waar MySQL de gegevensopslag wordt gevormd) is volledig door het volgende bevel in CLI in werking te stellen:

```bash
df -h
```

Minder dan 10% van het vrije geheugen op de schijf MySQL is een primaire indicator van een stroomstoring.

## Oorzaak

De `/data/mysql` mount kan vol worden vanwege een reeks problemen, zoals onvoldoende inodes, beschikbare opslagruimte en slechte query&#39;s die tijdelijke tabellen genereren.

## Oplossing

Er is een onmiddellijke stap die u zou kunnen nemen om MySQL terug op het spoor te brengen (of het te verhinderen vastgelopen te worden): maak wat ruimte vrij door grote lijsten te spoelen.

Maar een oplossing op lange termijn zou meer ruimte toewijzen en volgen [Best practices voor databases](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html), met inbegrip van het mogelijk maken van [Archief voor bestelling/factuur/verzending](https://docs.magento.com/user-guide/sales/order-archive.html) functionaliteit.

Hieronder vindt u details over zowel snelle als langetermijnoplossingen.

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

Controleer of Gebruik % &lt;70% is. De knooppunten zijn gecorreleerd met bestanden. Als u bestanden uit de partitie verwijdert, worden de inodes vrijgemaakt.

### Opslagruimte controleren en vrijmaken

Beschikbare opslagruimte controleren. Hiervoor voert u uit:

```bash
df -k
```

De uitvoer zou er ongeveer als volgt uitzien:

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

Als Gebruik % >70% is, moet u actie ondernemen om ruimte vrij te maken/toe te voegen.

### Controleren op groot `ibtmp1` bestanden

Controleren op groot `ibtmp1` bestand op `/data/mysql` van elk knooppunt: dit bestand is de tabelruimte voor tijdelijke tabellen. Als er slechte vragen zijn die tijdelijke lijsten produceren, zijn zij bevat in `ibtmp1` bestand. Dit bestand wordt alleen verwijderd wanneer de database opnieuw wordt gestart. Als het alle beschikbare ruimte in beslag neemt, moet de database opnieuw worden gestart. Als er slechte vragen zijn, zal het opnieuw worden ontspannen.

### Grote tabellen uitvouwen

>[!WARNING]
>
>We raden u ten zeerste aan een back-up van een database te maken voordat u wijzigingen aanbrengt en deze te vermijden tijdens perioden met veel laadtijd. Zie [Database dumpen](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) in onze ontwikkelaarsdocumentatie.

Controleer of er grote tabellen zijn en of een van deze tabellen kan worden verwijderd. Doe dit op het primaire (bron) knooppunt.

Tabellen met rapporten kunnen bijvoorbeeld meestal worden verwijderd. Voor meer informatie over het zoeken naar grote tabellen raadpleegt u de [Grote MySQL-tabellen zoeken](/help/how-to/general/find-large-mysql-tables.md) artikel.

Als er geen grote rapporttabellen zijn, kunt u flushing overwegen `_index` tabellen, alleen om de Adobe Commerce-toepassing weer op schema te krijgen. `index_price` tabellen zouden de beste kandidaten zijn . Bijvoorbeeld: `catalog_category_product_index_storeX` tabellen, waarbij X waarden kan hebben van &quot;1&quot; tot het maximale aantal winkels. Onthoud dat u opnieuw moet indexeren om gegevens in deze tabellen te herstellen. In het geval van grote catalogi kan het veel tijd kosten om de gegevens opnieuw te indexeren.

Wacht tot de software volledig is gesynchroniseerd nadat u deze hebt verwijderd. U kunt nu back-ups maken en belangrijke stappen nemen om meer ruimte toe te voegen, zoals meer ruimte toewijzen/kopen en [Archief voor bestelling/factuur/verzending](https://docs.magento.com/user-guide/sales/order-archive.html) functionaliteit.

### Instellingen voor binaire logboekregistratie controleren

Controleer de binaire logboekinstellingen van uw MySQL-server: `log_bin` en `log_bin_index`. Als de instellingen zijn ingeschakeld, kunnen de logbestanden enorm worden. [Een ondersteuningsticket maken](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) aanvragen om grote binaire logbestanden te wissen. Ook, verzoek om te controleren dat het binaire registreren correct wordt gevormd zodat de logboeken periodiek worden gezuiverd en niet teveel ruimte nemen.

Als u geen toegang tot MySQL servermontages hebt, verzoek steun om het te controleren.

### Meer ruimte toewijzen/kopen

Wijs meer schijfruimte toe voor MySQL als u wat ongebruikt hebt. Zie de [Limiet schijfruimte controleren](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) artikel voor informatie over het controleren of er vrije schijfruimte is.

* Voor het plan van de Aanzet, alle milieu&#39;s, en de milieu&#39;s van de Integratie van het Pro plan, kunt u de schijfruimte toewijzen als u wat ongebruikt hebt. Zie voor meer informatie de [Meer ruimte toewijzen voor MySQL](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md).
* Voor Pro-omgevingen voor staging en productie, [contactondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om meer schijfruimte toe te wijzen als u wat ongebruikt hebt.

Als u uw ruimtelimiet hebt bereikt en nog steeds weinig ruimte hebt, kunt u overwegen meer schijfruimte te kopen. Neem contact op met het accountteam van de Adobe voor meer informatie.
