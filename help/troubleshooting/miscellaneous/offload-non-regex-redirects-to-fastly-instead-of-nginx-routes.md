---
title: Offload niet-regex herleidt naar Fastly in plaats van Nginx (routes)
description: Dit onderwerp stelt een oplossing voor een typisch redirects prestatieskwestie voor u zou kunnen hebben wanneer u niet-regex herleidt aan Fastly in plaats van Nginx in Adobe Commerce op wolkeninfrastructuur.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Offload niet-regex herleidt naar Fastly in plaats van Nginx (routes)

Dit onderwerp stelt een oplossing voor een typisch redirects prestatieskwestie voor u zou kunnen hebben wanneer u niet-regex herleidt aan Fastly in plaats van Nginx in Adobe Commerce op wolkeninfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies) `Master/Production/Staging` -omgevingen die snel gebruikmaken van

## Probleem

In Adobe Commerce op cloudinfrastructuur kunnen grote aantallen niet-regex-omleidingen/herschrijvingen niet worden uitgevoerd op de Nginx-laag en kunnen hierdoor prestatieproblemen ontstaan.

## Oorzaak

Het bestand `routes.yaml` in de map `.magento/routes.yaml` definieert routes voor uw Adobe Commerce op cloudinfrastructuur.

Als de grootte van het `routes.yaml` -bestand 32 kB of groter is, moet u de omleiding/herschrijving van het bestand naar Fastly ongedaan maken.

Deze NGinx-laag kan geen groot aantal niet-regex omleidingen/herschrijvingen verwerken, anders zullen er prestatieproblemen optreden.

## Oplossing

De oplossing is om die niet-regex in plaats daarvan om te leiden naar Snelst. Maak een algemeen foutpad om snel om te leiden.

In de volgende stappen wordt beschreven hoe u omleidingen snel kunt plaatsen in plaats van op Nginx.

1. Maak een Edge-woordenboek.

   Eerst, kunt u [ VCL fragmenten in Adobe Commerce ](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) gebruiken om een randwoordenboek te bepalen. Dit bevat de omleidingen.

   Enkele kanttekeningen:

   * Kan snel geen regex uitvoeren op woordenboekitems. Het is maar een exacte overeenkomst. Voor meer op deze beperkingen, gelieve te zien {de documenten van 0} Fastly op de beperkingen van het randwoordenboek ](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).[
   * Er geldt een limiet van 1000 items in één woordenboek. Deze limiet kan snel worden vergroot, maar dat leidt tot het derde voorbehoud.
   * Telkens wanneer u de ingangen bijwerkt en dat bijgewerkte VCL aan alle knopen opstelt, is er een geometrische toename van de ladingstijd met het uitbreiden van woordenboeken - betekenend, zal een 2000 ingangswoordenboek 3x-4x langzamer dan een 1000 ingangswoordenboek eigenlijk laden. Maar dat is slechts een kwestie wanneer u VCL (het bijwerken van het woordenboek of het veranderen van de VCL functiecode) opstelt.

     Het heeft geen invloed op de tijd die nodig is om een aanvraag snel te verwerken; het is alleen van invloed op de tijd die nodig is om snel een nieuwe configuratie uit te duwen.

     Over het algemeen nemen configuratiewijzigingen gemiddeld enkele seconden in beslag, meestal niet meer dan 5-10 seconden. Zo neemt een 2x verhoging van woordenboekpunten omhoog van 30 seconden om uw config uit te krijgen. Een stijging van 4 x neemt dichter bij 2 minuten in beslag. Dit leidt tot het vierde voorbehoud.

   * Er is een vrij harde grens van 10.000 ingangen in een randwoordenboek.

   We raden u ten zeerste aan uw lijst met omleidingen te consolideren. U kunt meerdere woordenboeken gebruiken, maar houd er rekening mee dat elke update die u aanbrengt in uw VCL enkele minuten duurt om snel te vullen.

1. Vergelijk de URL met het woordenboek.

   Wanneer de URL-zoekopdracht wordt uitgevoerd, wordt de vergelijking gemaakt om de aangepaste foutcode toe te passen als er een overeenkomst wordt gevonden.

   Gebruik een ander VCL-fragment om iets als het volgende toe te voegen aan `vcl_recv` :

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Hier, controleren wij om te zien of bestaat URL in de lijstingang. Als dit het geval is, wordt een interne Fastly-fout aangeroepen en wordt de omleiding van de URL vanuit de tabel doorgegeven aan die fout.

1. De omleiding beheren.

   Wanneer een overeenkomst wordt gevonden, wordt de actie ondernomen die voor die `obj.status` wordt bepaald, in dit geval een 301 permanent bewegingsomleiding.

   Gebruik een laatste fragment in `vcl_error` om de 301 foutcodes terug te sturen naar de client:

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Met dit blok, controleren wij om te zien of zal de foutencode die van `vcl_recv` wordt overgegaan aanpast, en als zo, zullen wij de plaats aan het foutenbericht plaatsen dat binnen wordt overgegaan, dan de statuscode in 301 en het bericht &quot;permanent&quot;veranderen. Op dat punt, zou de reactie klaar moeten zijn om terug naar de cliënt te gaan.

### Stage-service

>[!WARNING]
>
>Als u al deze stappen wilt uitproberen, wordt u ten zeerste aangeraden een Adobe Commerce-testomgeving in te stellen. Op die manier kunt u tests uitvoeren tegen de Fastly-service om ervoor te zorgen dat alles zich gedraagt zoals u zou verwachten.

Als u geen Adobe Commerce het opvoeren milieu wilt in werking stellen, maar u zou willen zien hoe deze omleidingen zouden kijken, kunt u opstelling een werkgebiedrekening direct op Fastly.

## Gerelateerde lezing

* [ de Snelle verwijzing van VCL ](https://docs.fastly.com/vcl/)
* [ vorm routes ](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) in onze ontwikkelaarsdocumentatie.
* [ Opstelling snel ](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze ontwikkelaarsdocumentatie.
* [ VCL regelmatige uitdrukkingsbedriegblad ](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) in onze ontwikkelaardocumentatie.
