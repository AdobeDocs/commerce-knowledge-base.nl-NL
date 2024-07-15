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

Dit artikel biedt oplossingen voor problemen met erg weinig of geen ruimte voor MySQL op Adobe Commerce op cloudinfrastructuur. Symptomen kunnen plaatsstroomonderbrekingen omvatten, klanten kunnen geen producten aan de kar toevoegen, die niet met het gegevensbestand kunnen verbinden, tot het gegevensbestand ver toegang hebben, die niet SSH in knoop kunnen. Symptomen zijn onder andere Galera, Omgevingssync, PHP, Database en Implementatiefouten, zoals hieronder vermeld. Klik [ Oplossing ](https://support.magento.com/hc/en-us/articles/360058472572#solution) om rechtstreeks aan de oplossingssectie te springen.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur 2.3.0-2.3.6-p1, 2.4.0-2.4.2

## Probleem

De database wordt te groot. De symptomen kunnen onder andere het verlies van de databaseverbinding, de uploadfout voor de database en diverse andere problemen zijn.

Fouten die u kunt tegenkomen:

Galera:

* *SQLSTATE \[08S01 \]: Communicatie verbindingsmislukking: 1047 WSREP heeft nog geen knoop voor toepassingsgebruik voorbereid*   *de fouten van de Invoer:*
* *SQLSTATE \[HY000 \]: Algemene fout: 1180 kreeg fout 5 &quot;Input/output fout&quot;*
* *SQLSTATE \[08S01 \]: Communicatie verbindingsmislukking: 1047 WSREP heeft nog geen knoop voor toepassingsgebruik voorbereid*

Synchronisatiefouten omgeving:

* *SQLSTATE: Algemene fout: 1180 kreeg fout 5 &quot;Input/output fout&quot;tijdens BEVEL*

PHP-fouten:

* *php: BOB::\_\_construct (): MySQL server is weggegaan.*
* *php fouten: BOB::\_\_construct (): Fout terwijl het lezen van groet pakket. PID=NNNN.*
* *FOUT 2013 (HY000): Verloren verbinding aan server MySQL bij het &quot;lezen van eerste communicatie pakket&quot;, systeemfout: 0 &quot;Interne fout/controle (niet systeemfout)&quot;.*

Database-fouten:

* *Fout \_code: 1114*
* *InnoDB: Fout (uit schijfruimte) die woordknoop aan FTS hulpindexlijst schrijft.*
* *SQLSTATE \[HY000 \]: Algemene fout: De server van 2006 MySQL is weggegaan*
* *\[ERROR\] Slave SQL: Fout &quot;De lijst `<table\_name>` is volledig&quot;op vraag.*
* *eenheid mysql.service ingegaan ontbroken staat.*
* *fout: &quot;Kan niet met lokale server verbinden MySQL door contactdoos &quot;/var/run/mysqld/mysqld.sock&quot;(111 &quot;Verbinding geweigerd&quot;)*
* *1205 De wachttijd van het Slot overschrijdt; probeer opnieuw beginnend transactie, de vraag was: TUSSENVOEGSEL IN \&quot;cron\_planning\ ` (\&quot;baan\_code\ `, \ &quot;status\\\ `, \&quot;gepland\_at\ `) WAARDEN (?, ?, `YYYY-02-07 HH:MM:SS`, `YYYY-MM-DD HH:MM:SS`)*

Implementatiefouten:

* *E: Het bevel &#39;\[&#39;sudo&#39;, &#39;-u&#39;, `<environment name>`, &#39;bash&#39;, &#39;-c&#39;, &#39;/etc/platform/`<environment name>`/post\_Implementatie.sh&#39;\]&#39; keerde niet-nul uitgangsstatus 255*
* *E: Bevel &quot;\[&#39;ssh&#39;, u `<node IP address>`, &quot;sudo /usr/bin/sv - w 30 herstart plaats- `<environment name>` g-nginx \]&quot;teruggekeerde niet-nul*
* *Bevorderend schema.. SQLSTATE\[HY000\]: Algemene fout: 1114 De tabel `<table\_name>` is vol*
* *SQLSTATE\[HY000\]: Algemene fout: 3 Fout bij het schrijven van bestand./`<environment name>`/\#*
* *W: `<filename>` (ErrCode: 28 &quot;Geen ruimte verlaten op apparaat&quot;)* *Indexerende fouten (samen met orphaned tijdelijke.ibd- dossiers in /tmp):*
* *de indexeerder van de Regel van de Catalogus werpt een uitzondering. De tijdelijke lijsten worden niet schoongemaakt in de nasleep en dan de schijf op de huidige MySQL hoofdknoop* vullen

<u> Stappen om </u> te reproduceren:

Één van de manieren u kunt controleren als `/data/mysql` (of waar MySQL gegevensopslag wordt gevormd) volledig is door het volgende bevel in CLI in werking te stellen:

```bash
df -h
```

Minder dan 10% van het vrije geheugen op de schijf MySQL is een primaire indicator van een stroomstoring.

## Oorzaak

De hoeveelheid `/data/mysql` kan vol worden als gevolg van een aantal problemen, zoals onvoldoende codes, beschikbare opslagruimte en onjuiste query&#39;s die tijdelijke tabellen genereren.

## Oplossing

Er is een onmiddellijke stap die u zou kunnen nemen om MySQL terug op het spoor te brengen (of het te verhinderen vastgelopen te worden): maak wat ruimte vrij door grote lijsten te spoelen.

Maar een oplossing op lange termijn zou meer ruimte en na [ beste praktijken van het Gegevensbestand ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) toewijzen, met inbegrip van het toelaten van de [ Orde/Factuur/het archieffunctionaliteit van het Verzending ](https://docs.magento.com/user-guide/sales/order-archive.html).

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

### Controleren op grote `ibtmp1` bestanden

Controleren op groot `ibtmp1` bestand op `/data/mysql` van elk knooppunt: dit bestand vormt de tabelruimte voor tijdelijke tabellen. Als er ongeldige query&#39;s zijn die tijdelijke tabellen genereren, staan deze in het `ibtmp1` -bestand. Dit bestand wordt alleen verwijderd wanneer de database opnieuw wordt gestart. Als het alle beschikbare ruimte in beslag neemt, moet de database opnieuw worden gestart. Als er slechte vragen zijn, zal het opnieuw worden ontspannen.

### Grote tabellen uitvouwen

>[!WARNING]
>
>We raden u ten zeerste aan een back-up van een database te maken voordat u wijzigingen aanbrengt en deze te vermijden tijdens perioden met veel laadtijd. Zie [ Dump uw gegevensbestand ](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump) in onze ontwikkelaardocumentatie.

Controleer of er grote tabellen zijn en of een van deze tabellen kan worden verwijderd. Doe dit op het primaire (bron) knooppunt.

Tabellen met rapporten kunnen bijvoorbeeld meestal worden verwijderd. Voor details op hoe te om grote lijsten te vinden, zie [ Groot MySQL- lijsten ](/help/how-to/general/find-large-mysql-tables.md) artikel vinden.

Als er geen grote rapporttabellen zijn, kunt u `_index` -tabellen leegmaken, gewoon om de Adobe Commerce-toepassing weer op schema te krijgen. `index_price` -tabellen zijn de beste kandidaten. Bijvoorbeeld `catalog_category_product_index_storeX` tabellen, waarin X waarden kan hebben van &quot;1&quot; tot het maximale aantal winkels. Onthoud dat u opnieuw moet indexeren om gegevens in deze tabellen te herstellen. In het geval van grote catalogi kan het veel tijd kosten om de gegevens opnieuw te indexeren.

Wacht tot de software volledig is gesynchroniseerd nadat u deze hebt verwijderd. U kunt steunen nu tot stand brengen en belangrijkere stappen nemen om meer ruimte toe te voegen, als het toewijzen van/het kopen van meer ruimte en het toelaten van ](https://docs.magento.com/user-guide/sales/order-archive.html) functionaliteit van het archiefarchief 0} van de Orde/van de Rekening/van de Verzending.[

### Instellingen voor binaire logboekregistratie controleren

Controleer de binaire logboekinstellingen voor MySQL-servers: `log_bin` en `log_bin_index` . Als de instellingen zijn ingeschakeld, kunnen de logbestanden enorm worden. [ creeer een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoekend om grote binaire logboekdossiers te zuiveren. Ook, verzoek om te controleren dat het binaire registreren correct wordt gevormd zodat de logboeken periodiek worden gezuiverd en niet teveel ruimte nemen.

Als u geen toegang tot MySQL servermontages hebt, verzoek steun om het te controleren.

### Meer ruimte toewijzen/kopen

Wijs meer schijfruimte toe voor MySQL als u wat ongebruikt hebt. Zie het [ de grens van de schijfruimte van de Controle ](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md) artikel leren hoe te om te controleren als u vrije schijfruimte hebt.

* Voor het plan van de Aanzet, alle milieu&#39;s, en de milieu&#39;s van de Integratie van het Pro plan, kunt u de schijfruimte toewijzen als u wat ongebruikt hebt. Voor details, zie [ meer ruimte voor MySQL ](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md) toewijzen.
* Voor Pro plan het Opvoeren en de milieu&#39;s van de Productie, [ contactsteun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om meer schijfruimte toe te wijzen als u wat ongebruikt hebt.

Als u uw ruimtelimiet hebt bereikt en nog steeds weinig ruimte hebt, kunt u overwegen meer schijfruimte te kopen. Neem contact op met het accountteam van de Adobe voor meer informatie.
