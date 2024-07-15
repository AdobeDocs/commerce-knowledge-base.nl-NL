---
title: "[!DNL Fastly] veelgestelde vragen over het camoufleren van oorsprong"
description: Dit FAQ bespreekt gemeenschappelijke vragen over  [!DNL Fastly]  oorsprong het camoufleren enablement in Adobe Commerce (die volledig is uitgevoerd sinds 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly] veelgestelde vragen over het camoufleren van oorsprong

In deze veelgestelde vragen worden veelvoorkomende vragen over [!DNL Fastly] mogelijkheden voor het camoufleren van oorsprong in Adobe Commerce besproken (die vanaf 2021 volledig zijn geïmplementeerd).

## Wat is [!DNL Fastly] oorsprong camoufleren?

Oorspronkelijke camouflage is een beveiligingsfunctie waarmee Adobe Commerce op de cloudinfrastructuur elk [!DNL non-Fastly] -verkeer kan blokkeren (om aanvallen met DDoS te voorkomen, waarbij naar de cloudinfrastructuur (oorsprong) wordt gegaan.

## Wat zijn de voordelen van het camoufleren van de oorsprong?

Oorsprong het camoufleren wordt ontworpen om verkeer te verhinderen [!DNL Fastly Web Application Firewall] (WAF) te mijden en het te verpletteren door de strikt bepaalde stroom van **[!DNL Fastly]** > **de Balancer van de Lading** > **Instanties**. Met deze implementatie is gegarandeerd dat al het verkeer door de [!DNL Fastly] WAF gaat en de interne WAF die in het taakverdelingsmechanisme is ingebouwd.

## Waarom gebeurt deze &#39;oorsprong&#39;-ontmoediging?

Deze functie is oorspronkelijk gemaakt ten behoeve van Adobe Commerce op cloudinfrastructuur.

## Moet ik een verzoek indienen om mijn project te camoufleren van de oorsprong?

Nee. Deze functie had al moeten worden geïmplementeerd voor alle cloudprojecten en voor alle projecten die sinds 2021 zijn ingericht, zou dit standaard zijn ingeschakeld.

## Verandert de oorsprong het uitgaande IP adres camoufleren?

Nee, dat is het niet.

## Beïnvloedt het camoufleren van de oorsprong de REST API?

[!DNL Fastly] plaatst geen API-aanroepen in het cachegeheugen, dus de client moet wel naar behoren met de wijziging werken. Aanwezigheid camoufleren leidt alleen tot aanvragen die recht naar de oorsprong gaan, zoals:

* Productie

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Staging

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

In dit voorbeeld kan de client de API nog steeds raken als ze de URL wijzigen in ``mywebsite.com`` :

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Zal deze verandering plaatsing en onderbreking beïnvloeden?

Nr, zal deze verandering **NIET** plaatsing en onderbreking beïnvloeden.

## Als het project meerdere staging-omgevingen heeft, wordt de oorspronkelijke camouflage toegepast op alle staging-omgevingen?

Ja, als het project meerdere testomgevingen heeft, wordt de wijziging toegepast op alle testomgevingen.
