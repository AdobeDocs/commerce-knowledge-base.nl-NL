---
title: Het bovenste navigatievenster wordt niet geladen in de winkel
description: Dit artikel biedt configuratieoplossingen voor de ESI-problemen (Varnish Edge Side Includes), waarbij de inhoud van bepaalde pagina's, meestal het bovenste navigatievenster, niet in de winkel wordt weergegeven als Varnish wordt gebruikt voor het in cache plaatsen.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Het bovenste navigatievenster wordt niet geladen in de winkel

Dit artikel biedt configuratieoplossingen voor de ESI-problemen (Varnish Edge Side Includes), waarbij de inhoud van bepaalde pagina&#39;s, meestal het bovenste navigatievenster, niet in de winkel wordt weergegeven als Varnish wordt gebruikt voor het in cache plaatsen.

## Betrokken producten en versies

* Adobe Commerce 2.X.X
* Alle versies in Varnish

## Probleem

<u> Eerste vereisten </u>:

Installeer en configureer Varnish voor uw Adobe Commerce Store.

<u> Stappen om </u> te reproduceren:

1. Ga naar de winkel.
1. Blader door de winkelpagina&#39;s.

<u> Verwachte resultaten </u>:

Alle inhoud en alle paginablokken zijn geladen.

<u> Ware resultaten </u>:

Houd er rekening mee dat bepaalde inhoudsblokken, zoals het bovenste navigatievenster met categorieën, niet worden geladen. Er wordt lege ruimte weergegeven.

## Oorzaak

De mogelijke redenen voor deze kwestie zijn:

* In ESI worden tags voor include-bestanden gegenereerd met het HTTPS-toegangsprotocol, terwijl Varnish alleen werkt met HTTP.
* Varnish verwerkt geen ESI in JSON.
* De antwoordheaders zijn te groot voor Varnish, maar kunnen ze niet verwerken.

## Oplossing

Om de kwesties op te lossen, moet u een extra configuratie van Varnish uitvoeren en Varnish opnieuw beginnen.

1. Als gebruiker met `root` voorrechten, open uw Vanish configuratiedossier in een tekstredacteur. Zie [ wijzigen wijzigt de het systeemconfiguratie van Varnish ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) in onze ontwikkelaarsdocumentatie voor info over waar dit dossier voor verschillende werkende systemen zou kunnen worden gevestigd.
1. Voeg in de lus `DAEMON_OPTS variable` `-p feature=+esi_ignore_https` , `-p  feature=+esi_ignore_other_elements` , `-p  feature=+esi_disable_xml_check` toe. Dit ziet er als volgt uit:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.
1. Verhoog in het VCL-configuratiebestand de responsheaders door de waarden van de volgende parameters te verhogen: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend` . Zorg ervoor dat de laatste twee van deze waarden vergelijkbare waarden hebben.
1. Wanneer u dit wijzigt, moet u `service varnish restart` uitvoeren om de wijzigingen van kracht te laten worden.

## Gerelateerde lezing

* [ vorm Varnish en uw Webserver ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) in onze ontwikkelaarsdocumentatie.
* [ de documentatie van Varnish ](https://varnish-cache.org/docs/5.1/reference/index.html)
