---
title: Snel caching werkt niet op Adobe Commerce op cloudinfrastructuur
description: Dit artikel bevat een oplossing voor het snel in cache plaatsen van bestanden die niet op uw site werken. De snelst is een CDN en het in het voorgeheugen onderbrengen dienst inbegrepen met Adobe Commerce op de plannen en de implementaties van de wolkeninfrastructuur. Als u wilt controleren of de extensie Fastly werkt of als u fouten wilt opsporen in de extensie Fastly, kunt u de opdracht Krullen gebruiken om bepaalde antwoordheaders weer te geven. De waarden van deze antwoordheaders geven aan of Fastly is ingeschakeld en of het goed werkt. U kunt kwesties verder onderzoeken die op de waarden van kopballen en caching gedrag worden gebaseerd.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Snel caching werkt niet op Adobe Commerce op cloudinfrastructuur

Dit artikel bevat een oplossing voor het snel in cache plaatsen van bestanden die niet op uw site werken. De snelst is een CDN en het in het voorgeheugen onderbrengen dienst inbegrepen met Adobe Commerce op de plannen en de implementaties van de wolkeninfrastructuur. Als u wilt controleren of de extensie Fastly werkt of als u fouten wilt opsporen in de extensie Fastly, kunt u de opdracht Krullen gebruiken om bepaalde antwoordheaders weer te geven. De waarden van deze antwoordheaders geven aan of Fastly is ingeschakeld en of het goed werkt. U kunt kwesties verder onderzoeken die op de waarden van kopballen en caching gedrag worden gebaseerd.

Met deze informatie kunt u snel headers voor uw livesite en oorspronkelijke servers controleren en testen.

## Betrokken versies

* Adobe Commerce over cloudinfrastructuur
* Snelst 1.2.27 en hoger

## Probleem

Caching werkt mogelijk niet voor uw livesite-, productie- of staging-omgevingen.

## Oorzaak

Configuraties, onjuiste gegevens of niet-ondersteunde Adobe Commerce-extensies kunnen vaak worden gebruikt omdat caching niet snel werkt. Als u de instelling Fastly onjuist instelt of een niet-ondersteunde extensie gebruikt die de koppen doorsnijdt, werkt het snel in cache plaatsen niet.

## Testen met opdrachten en reactiekoppen controleren

### Testen met graven, opdracht

Eerst, controleer kopballen met een gradibevel aan URL. In een eindtoepassing, ga graving `<url>` in om de Snelle vertoning van de diensten in de kopballen te verifiëren. Voor extra grafietests, zie het Snelle Testen van [ alvorens DNS ](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains) te veranderen.

Bijvoorbeeld:

* Live site: `dig http[s]://<your domain>`
* Staging: `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Productie: `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Testen met krullen, opdracht

Vervolgens gebruikt u een krullingsopdracht om te controleren of er X-Magento-tags bestaan en aanvullende koptekstgegevens. Het bevelformaat verschilt voor het Opvoeren en de Productie.

Voor meer informatie over deze opdrachten gaat u snel over wanneer u `-H "host:URL"` injecteert, vervangt u deze door de oorsprong naar de verbindingslocatie (CNAME-informatie uit uw OneDrive-werkblad), negeert `-k` SSL en `-v` biedt uitgebreide reacties. Als de kopballen correct tonen, controleer de levende plaats en verifieer opnieuw kopballen.

* Als er headerproblemen optreden wanneer de oorspronkelijke servers rechtstreeks worden overgeslagen zonder dat dit ten koste gaat van Snelheid, kunnen er problemen optreden in uw code, met extensies of met de infrastructuur.
* Als er geen fouten optreden die direct van invloed zijn op de oorspronkelijke servers, maar de headers het live domein niet snel raken, kunnen er snel fouten optreden.

Eerst, controleer uw **levende plaats** om de antwoordkopballen te verifiëren. De opdracht doorloopt de extensie Snelst om reacties te ontvangen. Als u niet de correcte kopballen ontvangt, dan zou u de oorsprongservers direct moeten testen. Deze opdracht retourneert de waarden van de koppen `Fastly-Magento-VCL-Uploaded` en `X-Cache` .

1. Voer in een terminal de volgende opdracht in om de URL van uw livesite te testen:

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Gebruik `--resolve` slechts als uw levende URL niet opstelling met DNS is en u geen statische routeset hebt. Bijvoorbeeld:

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Controleer de antwoordheaders om te controleren of Fastly werkt. De output voor dit bevel is gelijkaardig aan het krullen Staging en Productie. Bijvoorbeeld, zou u de teruggekeerde unieke kopballen door dit bevel moeten zien:

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Om **het Staging** te testen:

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Om **het taakverdelingsmechanisme van de Productie** te testen:

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Om **knoop van de Oorsprong van de Productie te testen**:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Een knooppunt van directe oorsprong:

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Als u bijvoorbeeld een openbare URL hebt www.mymagento.biz, voert u een opdracht in die vergelijkbaar is met de volgende opdracht om de productiesite te testen:

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Reactiekoppen controleren

* Controleer de geretourneerde antwoordheaders en -waarden:
* Fastly-Magento-VCL-Geüpload zou aanwezig moeten zijn
* X-Magento-tags moeten worden geretourneerd
* Fastly-Module-Toegelaten zou of ja of het Fastly aantal van de uitbreidingsversie moeten zijn
* X-cache moet HIT of HIT zijn
* x-cache-hits moeten 1,1 zijn
* Cachebeheer: maximumleeftijd moet groter zijn dan 0
* Pragma moet cache zijn

In het volgende voorbeeld worden de juiste waarden getoond voor Pragma, X-Magento-Tags en Fastly-Module-Enabled.

De uitvoer voor curlopdrachten kan lang zijn. Hieronder volgt alleen een overzicht:

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Oplossen

### Fast Module-Enabled is niet aanwezig

Als u geen &quot;ja&quot;voor Fastly-Module-Toegelaten in reactiekopballen ontvangt, moet u verifiëren de module van de Snelheid wordt geïnstalleerd en geselecteerd.

Als u wilt controleren of Fastly is ingeschakeld in Staging en Productie, controleert u de configuratie in Commerce Admin voor elke omgeving:

1. Meld u met /admin (of de gewijzigde beheerURL) aan bij de beheerconsole voor Staging en Productie.
1. Navigeer naar Opslag > Configuratie > Geavanceerd > Systeem. Blader en klik op Volledige paginacache.
1. Controleer of de CDN snel is geselecteerd.
1. Klik op Snelconfiguratie. Controleer of de snelste service-id en het snelste API-token zijn ingevoerd (uw snelste referenties). Verifieer u de correcte geloofsbrieven hebt ingegaan voor de het Opvoeren en milieu van de Productie. Klik op Referenties testen voor hulp.
1. Bewerk het bestand composer.json en zorg ervoor dat de module Snelheid wordt opgenomen in de versie. Dit bestand bevat alle modules die bij versies worden vermeld.

   * In de sectie &quot;require&quot; moet u &quot;faals/magento2&quot; hebben: `<version number>`
   * In de sectie &quot;repositories&quot; moet u beschikken over:

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Als u het Beheer van de Configuratie gebruikt, zou u een configuratiedossier moeten hebben. Bewerk het bestand app/etc/config.app.php (2.0, 2.1) of app/etc/config.php (2.2) en controleer of de instelling `'Fastly_Cdn' => 1` juist is. De instelling mag niet `'Fastly_Cdn' => 0` (uitgeschakeld) zijn. Als u Fastly hebt ingeschakeld, verwijdert u het configuratiebestand en voert u de opdracht bin/magento magento-cloud:scd-dump uit om bij te werken. Voor een looppas-door van dit dossier, zie [ Voorbeeld van het beheren van systeem-specifieke montages ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) in de Gids van de Configuratie.

Als de module niet geïnstalleerd is, moet u in een [ milieu van de Integratie ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) tak installeren en aan het Staging en Productie worden opgesteld. Zie [ Opstelling snel ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) voor instructies in Commerce op de Gids van de Infrastructuur van de Wolk.

### Fastly-Magento-VCL-Uploaded is niet aanwezig

Tijdens installatie en configuratie, zou u Fastly VCL moeten uploaden. Dit zijn de basisVCL fragmenten die door de Fastly module worden verstrekt, niet de fragmenten van douaneVCL u creeert. Voor instructies, zie [ snel VCL fragmenten ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) in Commerce op de Gids van de Infrastructuur van de Wolk uploaden.

### X-cache bevat MISS

Als X-Geheime voorgeheugen of HIT, MISS of MISS is, MISS, ga het zelfde krullbevel opnieuw in om ervoor te zorgen de pagina niet onlangs van het geheime voorgeheugen werd weggejaagd.

Als u hetzelfde resultaat krijgt, gebruikt u de krullopdrachten en controleert u de antwoordheaders:

* Pragma is cache
* Er zijn X-Magento-tags
* Cache-control: max-age is groter dan 0

Als het probleem zich blijft voordoen, worden deze headers waarschijnlijk opnieuw ingesteld door een andere extensie. Herhaal de volgende procedure in Staging om extensies uit te schakelen om te zoeken welke procedure de kwestie veroorzaakt. Nadat u de extensie(s) hebt gevonden die het probleem veroorzaakt, moet u de extensie(s) in Production uitschakelen.

1. Om de uitbreidingen onbruikbaar te maken, volg de stappen die in [ worden gegeven leiden de sectie van Uitbreidingen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) van Commerce op de gids van de Infrastructuur van de Wolk.
1. Nadat u de extensies hebt uitgeschakeld, gaat u naar **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]** .
1. Klik op **[!UICONTROL Flush Magento Cache]**.
1. Schakel nu één extensie tegelijk in en sla de configuratie op en spoel de cache op.
1. Probeer de krullopdrachten en controleer de antwoordheaders.
1. Herhaal stap 4 en 5 om de krullopdrachten in te schakelen en te testen. Wanneer de snelkopteksten niet meer worden weergegeven, hebt u de extensie gevonden die problemen met Snelheid veroorzaakt.

Wanneer u de extensie isoleert die de sneltoetsen opnieuw instelt, neemt u contact op met de ontwikkelaar van de extensie voor extra hulp. We kunnen geen oplossingen of updates bieden voor extensieontwikkelaars van andere leveranciers die werken met Fastly caching.

## Meer informatie in onze ontwikkelaarsdocumentatie:

* [ Ongeveer snel ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [ Opstelling snel ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [ de fragmenten van VCL van de Douane de Fastly ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
