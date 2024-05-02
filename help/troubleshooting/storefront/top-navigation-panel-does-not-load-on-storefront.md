---
title: Het bovenste navigatievenster wordt niet geladen in de winkel
description: Dit artikel biedt configuratieoplossingen voor de ESI-problemen (Varnish Edge Includes), waarbij de inhoud van bepaalde pagina's, meestal het bovenste navigatievenster, niet in de winkel wordt weergegeven als Varnish wordt gebruikt voor het in cache plaatsen.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Het bovenste navigatievenster wordt niet geladen in de winkel

Dit artikel biedt configuratieoplossingen voor de ESI-problemen (Varnish Edge Includes), waarbij de inhoud van bepaalde pagina&#39;s, meestal het bovenste navigatievenster, niet in de winkel wordt weergegeven als Varnish wordt gebruikt voor het in cache plaatsen.

## Betrokken producten en versies

* Adobe Commerce 2.X.X
* Alle versies in Varnish

## Probleem

<u>Vereisten</u>:

Installeer en configureer Varnish voor uw Adobe Commerce Store.

<u>Stappen om te reproduceren</u>:

1. Ga naar de winkel.
1. Blader door de winkelpagina&#39;s.

<u>Verwachte resultaten</u>:

Alle inhoud en alle paginablokken zijn geladen.

<u>Werkelijke resultaten</u>:

Houd er rekening mee dat bepaalde inhoudsblokken, zoals het bovenste navigatievenster met categorieën, niet worden geladen. Er wordt lege ruimte weergegeven.

## Oorzaak

De mogelijke redenen voor deze kwestie zijn:

* In ESI worden tags voor include-bestanden gegenereerd met het HTTPS-toegangsprotocol, terwijl Varnish alleen werkt met HTTP.
* Varnish verwerkt geen ESI in JSON.
* De antwoordheaders zijn te groot voor Varnish, maar kunnen ze niet verwerken.

## Oplossing

Om de kwesties op te lossen, moet u een extra configuratie van Varnish uitvoeren en Varnish opnieuw beginnen.

1. Als gebruiker met `root` toegangsrechten, opent u het Vanish-configuratiebestand in een teksteditor. Zie de [De configuratie van het vernis-systeem wijzigen](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) in onze ontwikkelaarsdocumentatie voor informatie over waar dit dossier voor verschillende werkende systemen zou kunnen worden gevestigd.
1. In de `DAEMON_OPTS variable`, toevoegen `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Dit ziet er als volgt uit:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.
1. Verhoog in het VCL-configuratiebestand de responsheaders door de waarden van deze parameters te verhogen: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Zorg ervoor dat de laatste twee van deze waarden vergelijkbare waarden hebben.
1. Wanneer u dit wijzigt, moet u `service varnish restart` de wijzigingen van kracht worden.

## Gerelateerde lezing

* [Varnish en uw webserver configureren](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) in onze ontwikkelaarsdocumentatie.
* [Varnish-documentatie](https://varnish-cache.org/docs/5.1/reference/index.html)
