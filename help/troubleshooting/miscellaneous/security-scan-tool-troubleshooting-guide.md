---
title: Handleiding voor het oplossen van problemen met Adobe Commerce Security Scan
description: Leer hoe u de verschillende problemen kunt oplossen met het hulpprogramma Security Scan voor Adobe Commerce en Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Handleiding voor het oplossen van problemen met Adobe Commerce Security Scan

Leer hoe u de verschillende problemen kunt oplossen met het hulpprogramma Security Scan voor Adobe Commerce en Magento Open Source.

## Uitgave: kan de site niet verzenden

Voor het hulpprogramma Beveiligingsscan moet u aantonen dat u de site in eigendom hebt voordat het domein aan het hulpprogramma Beveiligingsscan kan worden toegevoegd. U kunt dit doen door een bevestigingscode aan uw site toe te voegen met een HTML-opmerking of de `<meta>` -tag. De opmerking HTML moet binnen de tag `<body>` worden geplaatst, bijvoorbeeld in de voettekstsectie. De tag `<meta>` moet in de `<head>` -sectie van de pagina worden geplaatst.

Handelaren hebben vaak te maken met het probleem dat de beveiligingsscan-functie de eigendom van de site van de handelaar niet kan bevestigen.

Als u een fout krijgt en uw plaats voor het aftasten niet kunt voorleggen, verwijs naar het [ bericht van de Fout wanneer het toevoegen van plaatsen in het het oplossen van problemenartikel van het Aftasten van de Veiligheid ](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) in onze steunkennisbasis.

## Probleem: lege rapporten die zijn gegenereerd door het gereedschap Beveiligingsscan

U krijgt lege aftastenrapporten van het hulpmiddel van het Scannen van de Veiligheid of krijgt rapporten die slechts één fout bevatten zoals *het hulpmiddel van de Veiligheid niet kon basis URL* bereiken of *de installatie van het Magento wordt niet gevonden op verstrekte URL*.

### Oplossing

1. Controleer of IP&#39;s van 52.87.98.44, 34.196.167.176 en 3.218.25.102 niet worden geblokkeerd bij 80 en 443 poorten.
1. Controleer de verzonden URL op omleidingen (bijvoorbeeld `https://mystore.com` wordt omgeleid naar `https://www.mystore.com` of andersom of wordt omgeleid naar andere domeinnamen).
1. Onderzoek WAF/de logboeken van de Webservertoegang voor verworpen/onvervulde verzoeken. HTTP 403 `Forbidden` en HTTP 500 `Internal server error` zijn de gemeenschappelijke serverreacties die lege rapportgeneratie veroorzaken. Hier is een voorbeeld van de bevestigingscode die verzoeken door gebruikersagenten blokkeert:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

U kunt [ het rapport van het Hulpmiddel van het Scannen van de Veiligheid ook zien ](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) leeg artikel in onze steunkennisbasis voor meer informatie.

## Probleem: beveiligingsprobleem opgelost, maar nog steeds kwetsbaar in scan

U hebt een beveiligingsprobleem opgelost en u verwacht dat de beveiligingsscan aangeeft dat u niet langer kwetsbaar bent voor het nieuwe probleem. In plaats daarvan, vindt u dat het rapport dat door het Scannen van de Veiligheid wordt geproduceerd u nog meldt kwetsbaar aan de veiligheidskwestie.

### Oorzaak

Metagegevens van cloudinstellingen worden alleen verzameld voor `active` - en `live` Cloud-projecten. Dit is GEEN real-time proces.

Het script voor het verzamelen van statistische gegevens wordt één keer per dag uitgevoerd en vervolgens moet het hulpprogramma voor beveiligingsscan de nieuwe gegevens later ophalen.

De verwachte vertraging van de synchronisatiecyclus bedraagt maximaal een week en neemt minimaal 24 uur in beslag.

De volgende statussen kunnen bij controles worden weergegeven:

1. **pas** over: Het hulpmiddel van het Scannen van de Veiligheid heeft uw bijgewerkte gegevens gescand en de veranderingen goedgekeurd.
1. **Onbekend**: Het hulpmiddel van het Scannen van de Veiligheid heeft nog geen gegevens over uw domein; wacht op de volgende synchronisatiecyclus.
1. **Gebrek**: Als de status toont ontbreken, zult u de kwestie moeten bevestigen (laat 2FA toe, verander admin URL, enz.) en wacht op de volgende synchronisatiecyclus.

Als 24 uren zijn overgegaan aangezien de veranderingen aan de instantie werden aangebracht en zij niet in het Scanrapport van de Veiligheid worden weerspiegeld, kunt u [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen. Geef de URL van de winkel op wanneer u het ticket verzendt.

## BotNet vermoedelijke fout

U ontvangt een melding met betrekking tot de fout &quot;BotNet Suspect&quot;.

### Oorzaak

1. De naam van het opslagdomein kwam terug in een &quot;Potential BotNet Deelnemerslijst&quot;in 2019, en het had het Admin paneel, de downloader, of functionaliteit RSS openbaar, en/of zijn URL is vermeld in de CC skimming forums.
1. De waarschuwing kan worden veroorzaakt door de signalen van een compromis met de winkel en/of malware, zoals JavaScript op de pagina.
1. Het is niet noodzakelijkerwijs een kwestie die nog steeds speelt. Als de winkel al eerder in gevaar is gebracht, kan de hostnaam nog steeds als &#39;slachtoffer&#39; rond het donkere web zweven.
1. Het kan ook niet door Adobe Commerce worden veroorzaakt, maar door een systeemcompromis (op OS niveau).

### Oplossing

1. Controleren op de nieuwe SSH-accounts, wijzigingen in het bestandssysteem, enzovoort.
1. Voer een beveiligingscontrole uit.
1. Controleer de Adobe Commerce-versie en upgrade, vooral als Magento 1 nog wordt uitgevoerd en dit niet meer wordt ondersteund.
1. Als de kwestie nog voortduurt, [ voorlegt een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en verstrekt de opslag URL.

## Probleem: fout bij het toedienen van het compromis

Er is een fout opgetreden met betrekking tot een fout met betrekking tot een &quot;Compromise-injectie&quot;.

### Oplossing

1. Bekijk de scripts die worden vermeld in het rapport van het gereedschap Beveiligingsscan.
1. De brontekst van de homepage van het overzicht voor inlinescripts injecties.
1. Wijzigingen in de systeemconfiguratie doorvoeren, met name aangepaste `HTML head` en `Miscellaneous HTML` in `footer` sectiewaarden.
1. Voer code en gegevensbestandoverzicht voor onbekende veranderingen en tekenen van geïnjecteerde malware uit.

Als niets van de bovengenoemde hulp, [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorlegt en de opslag URL en foutenmelding van het rapport verstrekt.

## Veelgestelde vragen

### Zal de beveiligingsscan invloed hebben op de prestaties van mijn website?

Nee. Met de beveiligingsscan worden alle aanvragen één voor één ingediend, net als bij één gebruiker. Daarom moet de beveiligingsscan de prestaties van de website niet beïnvloeden.

### Hoe lang bewaart Adobe Commerce Beveiligingsscan rapporten?

U kunt de vorige 10 rapporten van uw eind produceren. Neem contact op met de ondersteuning van Adobe Commerce als er oudere rapporten vereist zijn. Er kunnen maximaal een jaar voorafgaande beveiligingsscanrapporten worden verkregen.

### Welke informatie is nodig wanneer het voorleggen van een steunkaartje?

Geef de domeinnaam op.
