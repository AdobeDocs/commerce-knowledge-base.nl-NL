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

Voor het hulpprogramma Beveiligingsscan moet u aantonen dat u de site in eigendom hebt voordat het domein aan het hulpprogramma Beveiligingsscan kan worden toegevoegd. U kunt dit uitvoeren door een bevestigingscode aan uw site toe te voegen met een HTML-opmerking of de `<meta>` -tag. De opmerking HTML moet in het dialoogvenster `<body>` -tag, bijvoorbeeld in de voettekstsectie. De `<meta>` -tag moet binnen de pagina worden geplaatst `<head>` sectie.

Handelaren hebben vaak te maken met het probleem dat de beveiligingsscan-functie de eigendom van de site van de handelaar niet kan bevestigen.

Als er een fout optreedt en u uw site niet kunt verzenden voor de scan, raadpleegt u de [Foutbericht bij het toevoegen van sites aan Beveiligingsscan](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) het oplossen van problemenartikel in onze steun kennisbasis.

## Probleem: lege rapporten die zijn gegenereerd door het gereedschap Beveiligingsscan

U krijgt lege scanrapporten van het hulpprogramma Security Scan of u krijgt rapporten met slechts één fout, zoals *Beveiligingsgereedschap kon de basis-URL niet bereiken* of *Installatie van Magento is niet gevonden op de opgegeven URL*.

### Oplossing

1. Controleer of IP&#39;s van 52.87.98.44, 34.196.167.176 en 3.218.25.102 niet worden geblokkeerd bij 80 en 443 poorten.
1. Controleer de verzonden URL op omleidingen (bijvoorbeeld `https://mystore.com` omleiding naar `https://www.mystore.com` of vice versa of omleiding naar andere domeinnamen).
1. Onderzoek WAF/de logboeken van de Webservertoegang voor verworpen/onvervulde verzoeken. HTTP 403 `Forbidden` en HTTP 500 `Internal server error` zijn de gemeenschappelijke serverreacties die lege rapportgeneratie veroorzaken. Hier is een voorbeeld van de bevestigingscode die verzoeken door gebruikersagenten blokkeert:

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

U kunt ook [Het rapport Beveiligingsscan Tool is leeg](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) artikel in onze kennisbasis voor ondersteuning voor meer informatie .

## Probleem: beveiligingsprobleem opgelost, maar nog steeds kwetsbaar in scan

U hebt een beveiligingsprobleem opgelost en u verwacht dat de beveiligingsscan aangeeft dat u niet langer kwetsbaar bent voor het nieuwe probleem. In plaats daarvan, vindt u dat het rapport dat door het Scannen van de Veiligheid wordt geproduceerd u nog meldt kwetsbaar aan de veiligheidskwestie.

### Oorzaak

Metagegevens van cloudinstellingen worden alleen verzameld voor `active` en `live` Cloudoprojecten en is GEEN real-time proces.

Het script voor het verzamelen van statistische gegevens wordt één keer per dag uitgevoerd en vervolgens moet het hulpprogramma voor beveiligingsscan de nieuwe gegevens later ophalen.

De verwachte vertraging van de synchronisatiecyclus bedraagt maximaal een week en neemt minimaal 24 uur in beslag.

De volgende statussen kunnen bij controles worden weergegeven:

1. **Voldoende**: Met het gereedschap Beveiligingsscan hebt u de bijgewerkte gegevens gescand en de wijzigingen goedgekeurd.
1. **Onbekend**: Het gereedschap Beveiligingsscan bevat nog geen gegevens over uw domein. Wacht op de volgende synchronisatiecyclus.
1. **Mislukt**: Als de status aangeeft dat deze is mislukt, moet u het probleem verhelpen (2FA inschakelen, URL van beheerder wijzigen, enz.) en wacht op de volgende synchronisatiecyclus.

Als er 24 uur zijn verstreken sinds de wijzigingen zijn aangebracht in de instantie en deze niet worden weergegeven in het rapport Beveiligingsscan, kunt u [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Geef de URL van de winkel op wanneer u het ticket verzendt.

## BotNet vermoedelijke fout

U ontvangt een melding met betrekking tot de fout &quot;BotNet Suspect&quot;.

### Oorzaak

1. De naam van het opslagdomein kwam terug in een &quot;Potential BotNet Deelnemerslijst&quot;in 2019, en het had het Admin paneel, de downloader, of functionaliteit RSS openbaar, en/of zijn URL is vermeld in de CC skimming forums.
1. De waarschuwing kan worden veroorzaakt door de signalen van compromis en/of malware van de opslagplaats, zoals JavaScript die op de pagina wordt gevonden.
1. Het is niet noodzakelijkerwijs een kwestie die nog steeds speelt. Als de winkel al eerder in gevaar is gebracht, kan de hostnaam nog steeds als &#39;slachtoffer&#39; rond het donkere web zweven.
1. Het kan ook niet door Adobe Commerce worden veroorzaakt, maar door een systeemcompromis (op OS niveau).

### Oplossing

1. Controleren op de nieuwe SSH-accounts, wijzigingen in het bestandssysteem, enzovoort.
1. Voer een beveiligingscontrole uit.
1. Controleer de Adobe Commerce-versie en upgrade, vooral als Magento 1 nog wordt uitgevoerd en dit niet meer wordt ondersteund.
1. Als het probleem zich blijft voordoen, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en geef de URL van de winkel op.

## Probleem: fout bij het toedienen van het compromis

Er is een fout opgetreden met betrekking tot een fout met betrekking tot een &quot;Compromise-injectie&quot;.

### Oplossing

1. Bekijk de scripts die worden vermeld in het rapport van het gereedschap Beveiligingsscan.
1. De brontekst van de homepage van het overzicht voor inlinescripts injecties.
1. Wijzigingen in systeemconfiguratie doorvoeren, vooral aangepast `HTML head` en `Miscellaneous HTML` in `footer` sectiewaarden.
1. Voer code en gegevensbestandoverzicht voor onbekende veranderingen en tekenen van geïnjecteerde malware uit.

Als geen van de bovenstaande voordelen helpt, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) en geef de URL van de winkel en het foutbericht van het rapport op.

## Veelgestelde vragen

### Zal de beveiligingsscan invloed hebben op de prestaties van mijn website?

Nee. Met de beveiligingsscan worden alle aanvragen één voor één ingediend, net als bij één gebruiker. Daarom moet de beveiligingsscan de prestaties van de website niet beïnvloeden.

### Hoe lang bewaart Adobe Commerce Beveiligingsscan rapporten?

U kunt de vorige 10 rapporten van uw eind produceren. Neem contact op met de ondersteuning van Adobe Commerce als er oudere rapporten vereist zijn. Er kunnen maximaal een jaar voorafgaande beveiligingsscanrapporten worden verkregen.

### Welke informatie is nodig wanneer het voorleggen van een steunkaartje?

Geef de domeinnaam op.
