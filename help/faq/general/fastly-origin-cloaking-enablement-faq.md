---
title: "[!DNL Fastly] Veelgestelde vragen over het camouflage van oorsprong"
description: In deze veelgestelde vragen worden veelvoorkomende vragen over [!DNL Fastly] de mogelijkheid om de oorsprong te camoufleren in Adobe Commerce (die sinds 2021 volledig is geïmplementeerd).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly] veelgestelde vragen over het camoufleren van oorsprong

In deze veelgestelde vragen worden veelvoorkomende vragen over [!DNL Fastly] de mogelijkheid om de oorsprong te camoufleren in Adobe Commerce (die sinds 2021 volledig is geïmplementeerd).

## Wat is [!DNL Fastly] camoufleren van oorsprong?

Oorspronkelijke camouflage is een beveiligingsfunctie waarmee Adobe Commerce in de cloud-infrastructuur alle [!DNL non-Fastly] verkeer (om aanvallen van DDoS te verhinderen, die naar de wolkeninfrastructuur (oorsprong) gaan.

## Wat zijn de voordelen van het camoufleren van de oorsprong?

Oorsprongscamouflage is ontworpen om te voorkomen dat het verkeer de [!DNL Fastly Web Application Firewall] (WAF) en het verpletteren van het door de strikt bepaalde stroom van **[!DNL Fastly]** > **Balans laden** > **Instanties**. Met deze implementatie wordt gegarandeerd dat al het verkeer door de [!DNL Fastly] zowel WAF als de interne WAF die in het taakverdelingsmechanisme is ingebouwd.

## Waarom gebeurt deze &#39;oorsprong&#39;-ontmoediging?

Deze functie is oorspronkelijk gemaakt ten behoeve van Adobe Commerce op cloudinfrastructuur.

## Moet ik een verzoek indienen om mijn project te camoufleren van de oorsprong?

Nee. Deze functie had al moeten worden geïmplementeerd voor alle cloudprojecten en voor alle projecten die sinds 2021 zijn ingericht, zou dit standaard zijn ingeschakeld.

## Verandert de oorsprong het uitgaande IP adres camoufleren?

Nee, dat is het niet.

## Beïnvloedt het camoufleren van de oorsprong de REST API?

[!DNL Fastly] plaatst geen API vraag in het voorgeheugen, zodat zou de cliënt met de verandering fijn moeten zijn. Aanwezigheid camoufleren leidt alleen tot aanvragen die recht naar de oorsprong gaan, zoals:

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

In dit voorbeeld kan de client de API nog steeds raken als deze de URL wijzigt in ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Zal deze verandering plaatsing en onderbreking beïnvloeden?

Nee, deze wijziging zal **NOT** impact implementatie en downtime.

## Als het project meerdere staging-omgevingen heeft, wordt de oorspronkelijke camouflage toegepast op alle staging-omgevingen?

Ja, als het project meerdere testomgevingen heeft, wordt de wijziging toegepast op alle testomgevingen.
