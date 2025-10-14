---
title: Offload niet- [!DNL regex] opnieuw richt aan  [!DNL Fastly]  in plaats van  [!DNL Nginx]  (routes)
description: Dit onderwerp stelt een oplossing aan een typisch redirects prestatieskwestie voor u zou kunnen hebben wanneer u niet [!DNL regex] herleidt aan  [!DNL Fastly]  in plaats van  [!DNL Nginx]  in Adobe Commerce op wolkeninfrastructuur.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Offload niet-[!DNL regex] omleidingen naar [!DNL Fastly] in plaats van [!DNL Nginx] (routes)

In dit onderwerp wordt een oplossing voorgesteld voor een typisch probleem met de omleiding van de prestaties dat u zou kunnen hebben wanneer u niet- [!DNL regex] omleidingen naar [!DNL Fastly] in plaats van [!DNL Nginx] in Adobe Commerce op cloudinfrastructuur verplaatst.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies) `Master/Production/Staging` -omgevingen die gebruikmaken van [!DNL Fastly]

## Probleem

In Adobe Commerce op cloudinfrastructuur kunnen grote aantallen niet- [!DNL regex] omleidingen/herschrijvingen niet worden uitgevoerd op de [!DNL Nginx] -laag, waardoor prestatieproblemen kunnen ontstaan.

## Oorzaak

Het bestand `routes.yaml` in de map `.magento/routes.yaml` definieert routes voor uw Adobe Commerce op cloudinfrastructuur.

Als de grootte van uw `routes.yaml` dossier 32KB of groter is, zou u uw niet [!DNL regex] redirects/rewrites aan [!DNL Fastly] moeten offloaden.

Deze [!DNL Nginx] laag kan een groot aantal niet - [!DNL regex] omleidingen/herschrijft behandelen, anders zullen de prestatieskwesties resulteren.

## Oplossing

De oplossing is om die niet- [!DNL regex] in plaats daarvan om te leiden naar [!DNL Fastly]. Maak een algemeen foutpad om naar [!DNL Fastly] om te leiden.

In de volgende stappen wordt beschreven hoe u omleidingen kunt plaatsen op [!DNL Fastly] in plaats van [!DNL Nginx] .

1. Maak een Edge-woordenboek.

   Eerst, kunt u [[!DNL VCL]  fragmenten in Adobe Commerce &#x200B;](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) gebruiken om een randwoordenboek te bepalen. Dit bevat de omleidingen.

   Enkele kanttekeningen:

   * [!DNL Fastly] kan [!DNL regex] niet toepassen op woordenboekitems. Het is maar een exacte overeenkomst. Zie de documenten van [[!DNL Fastly] over de beperkingen van het randwoordenboek &#x200B;](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations) voor meer informatie over deze beperkingen.
   * [!DNL Fastly] heeft een limiet van 1000 items in één woordenboek. [!DNL Fastly] kan deze limiet uitbreiden, maar dat leidt tot het derde voorbehoud.
   * Telkens wanneer u de items bijwerkt en dat bijgewerkte [!DNL VCL] naar alle knooppunten implementeert, is er een geometrische toename van de laadtijd met uitbreidende woordenboeken. Dit betekent dat een 2000-ingangswoordenboek 3x-4x langzamer wordt geladen dan een 1000-ingangswoordenboek. Maar dat is alleen van belang wanneer u [!DNL VCL] implementeert (het woordenboek bijwerkt of de functiecode [!DNL VCL] wijzigt).

     Het heeft geen invloed op de tijd die nodig is om een aanvraag te verwerken in [!DNL Fastly] . Het is alleen van invloed op de tijd die nodig is om een nieuwe configuratie uit te duwen in [!DNL Fastly] .

     Over het algemeen nemen configuratiewijzigingen gemiddeld enkele seconden in beslag, meestal niet meer dan 5-10 seconden. Zo neemt een 2x verhoging van woordenboekpunten omhoog van 30 seconden om uw config uit te krijgen. Een stijging van 4 x neemt dichter bij 2 minuten in beslag. Dit leidt tot het vierde voorbehoud.

   * Er is een vrij harde grens van 10.000 ingangen in een randwoordenboek.

   We raden u ten zeerste aan uw lijst met omleidingen te consolideren. U kunt meerdere woordenboeken gebruiken, maar houd er rekening mee dat elke update die u uitvoert naar uw [!DNL VCL] enkele minuten duurt voordat deze daadwerkelijk wordt gevuld in [!DNL Fastly] .

1. Vergelijk de [!DNL URL] met de woordenboeken.

   Wanneer de [!DNL URL] -zoekopdracht wordt uitgevoerd, wordt de vergelijking gemaakt om de aangepaste foutcode toe te passen als er een overeenkomst wordt gevonden.

   Gebruik een ander [!DNL VCL] -fragment om iets als het volgende toe te voegen aan `vcl_recv` :

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Hier controleren we of de code [!DNL URL] bestaat in de tabelvermelding. Als dit het geval is, wordt een interne [!DNL Fastly] fout aangeroepen en wordt de omleiding [!DNL URL] vanuit de tabel doorgegeven aan die fout.

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
>Als u al deze stappen wilt uitproberen, wordt u ten zeerste aangeraden een Adobe Commerce-testomgeving in te stellen. Op die manier kunt u tests uitvoeren met de service [!DNL Fastly] om ervoor te zorgen dat alles zich gedraagt zoals u zou verwachten.

Als u geen Adobe Commerce-testomgeving wilt gebruiken, maar wilt zien hoe deze omleidingen eruit zouden zien, kunt u rechtstreeks een werkgebiedaccount instellen op [!DNL Fastly] .

## Gerelateerde lezing

* [[!DNL Fastly VCL]  verwijzing &#x200B;](https://docs.fastly.com/vcl/)
* [&#x200B; vorm routes &#x200B;](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) in onze ontwikkelaarsdocumentatie
* [&#x200B; Opstelling  [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze ontwikkelingsdocumentatie
* [[!DNL VCL]  regelmatige uitdrukkingsbedriegblad &#x200B;](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) in onze ontwikkelaarsdocumentatie
* [&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
