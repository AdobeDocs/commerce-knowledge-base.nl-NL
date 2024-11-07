---
title: Het oplossen van problemen 503 fout die door noodzaak wordt veroorzaakt om standaardVersige montages te veranderen
description: Dit artikel biedt oplossingen voor het oplossen van problemen met 503 fouten die worden veroorzaakt door bepaalde standaardwaarden van Varnish Cache die niet voldoende zijn voor uw winkel.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Het oplossen van problemen 503 fout die door noodzaak wordt veroorzaakt om standaardVersige montages te veranderen

Dit artikel biedt oplossingen voor het oplossen van problemen met 503 fouten die worden veroorzaakt door bepaalde standaardwaarden van Varnish Cache die niet voldoende zijn voor uw winkel.

## Probleem

Als de lengte van geheim voorgeheugenmarkeringen door Adobe Commerce wordt gebruikt Varnish&#39;s gebrek van 8192 bytes overschrijdt, kunt u HTTP 503 (Achterste Ophalen Mislukt) fouten in browser zien. De fouten worden mogelijk als volgt weergegeven: *&quot;Fout 503 Ophalen achtergrondafbeelding is mislukt. Ophalen van back-end is mislukt&quot;*

## Oplossing

U lost dit probleem op door de standaardwaarde van de parameter `http_resp_hdr_len` in het Varnish-configuratiebestand te verhogen. De `http_resp_hdr_len` parameter specificeert de maximumkopballengte *binnen* de totale standaardreactiegrootte van 32768 bytes.

>[!NOTE]
>
>Als de waarde `http_resp_hdr_len` groter is dan 32 kB, moet u ook de standaardresponsgrootte verhogen met de parameter `http_resp_size` .

1. Als gebruiker met `root` bevoegdheden opent u het Vanish-configuratiebestand in een teksteditor:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Zoek naar de parameter `http_resp_hdr_len`.
1. Als de parameter niet bestaat, voegt u deze na `thread_pool_max` toe.
1. Stel `http_resp_hdr_len` in op een waarde die gelijk is aan het aantal producten in de grootste categorie vermenigvuldigd met 21. (Elke producttag is ongeveer 21 tekens lang.)    Stel de waarde bijvoorbeeld in op 65536 bytes als de grootste categorie 3000 producten bevat.    Bijvoorbeeld:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Stel de `http_resp_size` in op een waarde die geschikt is voor de verhoogde lengte van de responsheader.    Het gebruik van de som van de verhoogde headerlengte en de standaardresponsgrootte is bijvoorbeeld een goed beginpunt (bijvoorbeeld 65536 + 32768 = 98304): `-p http_resp_size=98304`. Een fragment volgt:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Tijdslimiet voor health check {#health-check-timeouts}

Als u het geheime voorgeheugen onbruikbaar maakt terwijl Varnish als caching toepassing wordt gevormd en terwijl Adobe Commerce op ontwikkelaarwijze is, zou het onmogelijk kunnen worden om aan login aan Admin.

Deze situatie kan zich voordoen omdat de standaardhealth check een `timeout` -waarde van 2 seconden heeft. Het kan meer dan 2 seconden duren voor de health check gegevens verzamelt en samenvoegt op elk verzoek om een health check. Als dit gebeurt in 6 van de 10 health checks, wordt de Adobe Commerce-server als ongezond beschouwd. Varnish bedient schale inhoud wanneer de server ongezond is.

Omdat Admin via Varnish wordt benaderd, kunt u zich niet aanmelden bij Admin om caching in te schakelen (tenzij Adobe Commerce weer gezond wordt). U kunt echter de volgende opdracht gebruiken om cache in te schakelen:

```bash
$ bin/magento cache:enable
```

Voor meer informatie over het gebruiken van de bevellijn, zie [ begonnen met bevel-lijn configuratie ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) worden.
