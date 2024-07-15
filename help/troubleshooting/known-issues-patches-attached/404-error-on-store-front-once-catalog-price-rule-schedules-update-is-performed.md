---
title: 404 Fout op winkelfront zodra de update van de catalogusprijsregelschema's is uitgevoerd
description: Dit artikel bevat een patch en de vereiste stappen voor het verhelpen van het bekende Adobe Commerce 2.2.1-probleem met betrekking tot het ophalen van een fout van 404 op alle voorpagina's van de winkel, nadat een update van de catalogusprijsregel is gemaakt en de begintijd later is bewerkt. U moet de patch toepassen om het probleem op te lossen.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Fout op winkelfront zodra de update van de catalogusprijsregelschema&#39;s is uitgevoerd

Dit artikel bevat een patch en de vereiste stappen voor het verhelpen van het bekende Adobe Commerce 2.2.1-probleem met betrekking tot het ophalen van een fout van 404 op alle voorpagina&#39;s van de winkel, nadat een update van de catalogusprijsregel is gemaakt en de begintijd later is bewerkt. U moet de patch toepassen om het probleem op te lossen.

## Probleem

Storefront-pagina&#39;s zijn niet meer beschikbaar, er is een fout van 404 geretourneerd. De uitgave wordt weergegeven nadat de actieve update van de catalogusprijsregel moet worden uitgevoerd, op voorwaarde dat de begindatum van deze update is bewerkt na de eerste aanmaak.

<u> Stappen om </u> te reproduceren:

1. In Commerce Admin, creeer een nieuwe Regel van de Prijs van de Catalogus onder **Marketing** > **Bevorderingen** > **Regel van de Prijs van de Catalogus**.
1. In het **net van de Regel van de Prijs van de Catalogus**, klik **uitgeven,** programma een nieuwe Update en plaats **Status** aan *Actief.*
1. Navigeer aan **Inhoud** > **Inhoud die** opneemt > **Dashboard.**
1. Selecteer de onlangs gemaakte update en wijzig de begintijd.
1. Sla de wijzigingen op.

<u> Verwacht resultaat </u>:

Wanneer de begindatum van de update van kracht wordt, wordt de regel voor catalogusprijzen met succes toegepast.

<u> Werkelijk resultaat </u>:

Wanneer de begindatum van de update van kracht wordt, worden alle catalogus en producten in de winkel niet meer beschikbaar en wordt de fout 404 geretourneerd.

## Oplossing

Als u cataloguspagina&#39;s wilt herstellen en de functionaliteit voor updates van catalogusprijsregels volledig wilt kunnen gebruiken, moet u de patch installeren, de regel zowel handmatig als in de beheerder verwijderen en de ongeldige koppelingen in de database herstellen. U moet ook de regel voor catalogusprijzen opnieuw maken.

Hieronder volgt een gedetailleerde beschrijving van de vereiste stappen:

1. [ pas het flard ](#patch) toe.
1. Verwijder in Commerce Admin de regel voor catalogusprijzen met betrekking tot de uitgave (waar de begintijd is bijgewerkt). Om dit te doen, open de regelpagina onder **Marketing** > **Bevorderingen** > **Regel van de Prijs van de Catalogus**, en klik **Regel van de Schrapping**.
1. Als u de database opent, verwijdert u de verwante record handmatig uit de tabel `catalogrule` .
1. Corrigeer de ongeldige koppelingen in de database. Zie de [ verwante paragraaf ](#fix_links) voor details.
1. In Commerce Admin onder **Marketing**, ga **Bevorderingen** > **Regel van de Prijs van de Catalogus**, en creeer de nieuwe regel met de vereiste configuratie.
1. Wis het browser geheime voorgeheugen onder **Systeem** > **het Beheer van het Geheime voorgeheugen**.
1. Zorg ervoor dat de uitsnijdtaken correct zijn geconfigureerd en met succes kunnen worden uitgevoerd.

## Reparatie {#patch}

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch downloaden](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce 2.2.1

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over cloudinfrastructuur 2.2.0 - 2.2.4
* Adobe Commerce op locatie 2.2.0 en 2.2.2 - 2.2.4

## Hoe de pleister aanbrengen

Voor instructie, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Ongeldige koppelingen naar testbestanden in database herstellen {#fix_links}

>[!WARNING]
>
>Wij adviseren sterk om een gegevensbestandsteun tot stand te brengen alvorens om het even welke gegevensbestandmanipulaties. Wij adviseren eerst het testen van vragen over ontwikkelomgeving.

Voer de volgende stappen uit om de rijen te corrigeren met ongeldige koppelingen naar de tabel `staging_update` .

1. Controleer of de ongeldige koppelingen naar de tabel `staging_update` voorkomen in de tabel `flag` . Dit zijn records waarin `flag_code=staging` voorkomt.
1. Identificeer de ongeldige versie van de `flag` lijst gebruikend de volgende vraag:

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. Selecteer in de tabel `staging_update` de bestaande versie die lager is dan de huidige (ongeldige) versie en stel de versiewaarde van twee getallen in. U neemt het, niet de vorige versie, om de situatie te vermijden dat de vorige versie de maximumversie in de tabel `staging_update` is die kan worden toegepast en dat we deze nog steeds opnieuw moeten toepassen.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   De versie die u als reactie krijgt, is uw geldige versie `id` .

1. Voor de rijen met ongeldige koppelingen in de `flag` -tabel stelt u de `flag_data` -waarden in op gegevens die een geldige versie-id bevatten. Dit helpt de prestaties te besparen bij het opnieuw indexeren en maakt het mogelijk opnieuw indexeren van alle entiteiten te voorkomen.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u> Voorbeeld:</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Bijgevoegde bestanden
