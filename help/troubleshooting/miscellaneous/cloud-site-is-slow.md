---
title: Cloudsite is traag
description: Dit artikel bevat aanbevelingen voor het verbeteren van de prestaties van uw Adobe Commerce op de cloudinfrastructuur onder zware verkeersbelastingen en voor het verminderen van deze belasting.
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Cloudsite is traag

Dit artikel bevat aanbevelingen voor het verbeteren van de prestaties van uw Adobe Commerce op de cloudinfrastructuur onder zware verkeersbelastingen en voor het verminderen van deze belasting.

## Betrokken versies en edities

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u>Stappen om te reproduceren</u>

1. Ga naar je Adobe Commerce-winkel.
1. Blader door een rubriekpagina.
1. Voeg een product toe aan de kar.

<u>Verwacht resultaat</u>

De site reageert snel en het toevoegen van een product aan het winkelwagentje gaat snel.

<u>Werkelijk resultaat</u>

De site is traag of de categoriepagina&#39;s zijn snel, maar de winkelpagina is traag.

## Foutopsporingsstappen en oplossingen

Ga als volgt te werk om de oorzaak van de trage prestaties op te sporen en te corrigeren. U kunt de eerste en tweede stappen schakelen, maar ga aan het blokkeren van IPs slechts te werk als de geheim voorgeheugenmontages optimalisering niet helpt.

1. Controleer de aanraaksnelheid in het cachegeheugen voor de pagina&#39;s met veel verkeer en verminder de hoeveelheid gegevens die vaak worden bijgewerkt.
1. Controleer de algemene aanraaksnelheid voor het cachegeheugen van de site en controleer de algemene cachegeheugen-/snelconfiguratie.
1. Identificeer de Webcliënten die de hoge serverlading veroorzaken en blokkeer IP&#39;s die de hoge lading veroorzaken.

De volgende alinea&#39;s bevatten meer details voor elke stap.

### Stap 1: Controleer het tarief van de geheim voorgeheugenhit voor de pagina&#39;s met hoog verkeer

De eerste stap aan het bevestigen van een plaats die door zwaar verkeer wordt samengeperst is ervoor te zorgen de pagina&#39;s met het zwaarste verkeer, zoals de homepage van de winkel en de top-level categoriepagina&#39;s, behoorlijk in het voorgeheugen onder worden gebracht.

U kunt de snelheden van de cache voor deze pagina&#39;s achterhalen door het dialoogvenster `X-Cache` HTTP-headers die cURL gebruiken, zoals beschreven in [Cache controleren met cURL](https://docs.fastly.com/guides/debugging/checking-cache#using-curl) in de Fastly documentatie. Of controleer de zelfde kopballen gebruikend het netwerklusje in de ontwikkelaartoolbar van uw favoriete Webbrowser.

In het algemeen worden de antwoordheaders die afkomstig zijn van de toepassing, snel gerespecteerd. Als alle kopteksten echter zijn ingesteld op &quot;niet in cache plaatsen&quot; en voor de pagina &quot;in het verleden verlopen&quot;, kan de pagina snel niet in het cachegeheugen worden opgeslagen.

>[!WARNING]
>
>Let op: als u snel de antwoordheaders wijzigt, dus als u de hoofd-URL met cURL of de webbrowser controleert, wordt niet noodzakelijkerwijs weergegeven welke headers door de toepassing worden uitgegeven. Het is gebruikelijk voor Fastly zelf om aan Webbrowsers met &quot;geen geheim voorgeheugenkopballen&quot;te antwoorden, maar voor de Webtoepassing zelf toe te staan caching en voor Fastly om het punt behoorlijk in het voorgeheugen onder te brengen. De headerinformatie &#39;cache-control&#39; en &#39;pragma&#39; zijn in dit geval dus niet nuttig.

#### Problemen oplossen voor pagina&#39;s met veel verkeer

Als de indexpagina een lage aanraaksnelheid heeft, kunt u deze corrigeren door de hoeveelheid gegevens op die pagina die zwaar zijn bijgewerkt, te verminderen.

### Stap 2: Controleer de totale aanraaksnelheid van de sitecache

De algemene aanraaksnelheid in cache controleren:

1. [Snelle gebruikersgegevens ophalen](http://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#cloud-fastly-creds) voor uw Adobe Commerce in een cloud-infrastructuuromgeving.
1. Voer de volgende Linux/macOS-opdracht cURL uit om de snelheden voor uw site in de afgelopen 30 minuten te controleren, waarbij u de waarden voor uw snelste referenties vervangt:

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   U kunt ook de historische hit-snelheden van de laatste dag of maand controleren door de zoekoptie voor het tijdbereik te wijzigen vanuit `?by=minute` tot `?by=hour` of `?by=day`. Voor meer informatie over het krijgen van de Fastly geheim voorgeheugenstatistieken, zie [Zoekopties](https://docs.fastly.com/api/stats#Query) in de Fastly documentatie.

   De `| json_pp` optie drukt de JSON-responsuitvoer vrij af met de `json_pp` nut. Als er een fout van het type a_&#39;json\_pp niet wordt gevonden&#39;_, installeert u het dialoogvenster `json_pp` of gebruik een ander opdrachtregelprogramma voor JSON-vrij afdrukken. U kunt ook de `| json_pp` en voer de opdracht opnieuw uit. De uitvoer van de JSON-reactie is niet opgemaakt, maar u kunt deze uitvoeren via een JSON-verfijnen om de uitvoer op te schonen.

Een treffer boven 0,90 of 90% geeft aan dat de cache van de volledige pagina werkt.

Een aanraaksnelheid lager dan 0,85 of 85% geeft mogelijk een probleem met de siteconfiguratie aan, of u hebt een extensie van een andere fabrikant geïnstalleerd waardoor de inhoud niet in de cache kan worden opgeslagen.

#### Oplossen van problemen met de algemene aanraaksnelheid voor cache

1. Bepaal aan de hand van de statistieken van de aanraaksnelheid per uur en per dag wanneer de aanraaksnelheid begon te dalen. Als het raakpercentage plotseling is gedaald op het moment dat u een wijziging in uw site hebt geïmplementeerd, kunt u de wijziging desgewenst terugdraaien totdat de site is geladen.
1. Controleer de configuratie in de Commerce Admin, onder **Winkels** > **Configuratie** > Geavanceerd > **Systeem** > **Volledige paginacache**. Controleer of **TTL voor openbare inhoud** waarde is niet te laag ingesteld.
1. Zorg ervoor dat je [De VCL-fragmenten geüpload](https://devdocs.magento.com/guides/v2.3/cloud/cdn/configure-fastly.html#upload-vcl-snippets).
1. Als u de fragmenten van douaneVCL gebruikt, zuivert hen voor correct gebruik van de &quot;pas&quot;of &quot;pijp&quot;acties: zij zouden zorgvuldig moeten worden gebruikt en op het minst met een voorwaarde van één of andere soort worden gebruikt. Zie voor meer tips [Aangepaste, snel VCL-fragmenten](https://devdocs.magento.com/guides/v2.3/cloud/cdn/cloud-vcl-custom-snippets.html) in onze ontwikkelaarsdocumentatie.

### Stap 3: Identificeer de websites die de hoge serverlading veroorzaken

U kunt een van de volgende methoden gebruiken om informatie op te halen over de IP-adressen die toegang krijgen tot uw Adobe Commerce-winkel.

* Controleer de de toegangslogboeken van HTTP door een zitting van SSH.
* Neem contact op met de ondersteuning van Adobe Commerce om een lijst met IP-adressen op te vragen die de site zwaar belasten.

#### Controleer de HTTP-toegangslogboeken

Voer de volgende opdracht uit vanuit uw lokale ontwikkelomgeving om het toegangslogboek van uw site weer te geven:

```bash
magento-cloud log access
```

Meer regels weergeven met de opdracht

```bash
--lines
```

, bijvoorbeeld:

```bash
magento-cloud log access --lines=500
```

U kunt dit logboek bekijken en controleren om te zien of komt een groot deel van verzoeken uit een specifiek IP adres. Een andere manier is om te gebruiken `awk` , `sort` en `uniq` om de het vaakst voorkomen IP adressen in het logboek, als het volgende automatisch te tellen:

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

Als de

```bash
magento-cloud log
```

opdracht werkt niet, kunt u verbinding maken met de externe server met SSH en het logbestand controleren op `/var/log/access.log`

Nadat u de IP adressen identificeert die zware serverlading veroorzaken, kunt u hen blokkeren door een IP lijst van gewezen personen van in het paneel van Admin van Commerce te vormen, onder **Winkels** > **Configuratie** > GEAVANCEERD > **Systeem** > **Volledige paginacache** > **Snelle configuratie** > **Blokkeren**.

Als u vanwege de hoge belasting geen toegang hebt tot uw beheerder, kunt u de snelheids-API gebruiken om de blokkeringsregels in te stellen:

1. Creeer ACL zoals die in wordt beschreven [Werken met ACLs die API gebruiken](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly doc.
1. In de `recv` sectie, creeer een fragment VCL met de volgende inhoud, die ACL\_NAME\_GOES\_HERE met de naam van ACL vervangen die in de vorige stap werd gecreeerd:

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

Voor meer informatie bij het blokkeren van IP adressen, zie [Gids voor snelle Adobe Commerce-module](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) in GitHub.
