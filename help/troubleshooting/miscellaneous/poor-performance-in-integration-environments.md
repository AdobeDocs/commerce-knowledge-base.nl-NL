---
title: Slechte prestaties in integratieomgevingen
description: Dit artikel biedt een oplossing voor het probleem waarbij de Pro-integratieomgevingen en de Starter-staging-omgevingen slecht presteren.
feature: Integration, Staging
role: Developer
source-git-commit: c0e2a8fdd2e4d231e56a3121544dbd8a25a8d60c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Slechte prestaties in integratieomgevingen

Dit artikel biedt een oplossing voor het probleem waarbij de Pro-integratieomgevingen en de Starter-staging-omgevingen slecht presteren.

## Betrokken producten en versies:

* Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

Uw Pro-integratieomgeving of Starter-staging-omgeving presteert slecht.

## Oorzaak

Afhankelijk van de grootte van uw catalogus/gegevens of de vereisten van uw externe integraties/aanpassingen, zijn de bronnen die beschikbaar zijn in de integratieomgevingen mogelijk overschreden.

## Oplossing

Om prestatieskwesties te behandelen, zorg ervoor dat u de beste praktijken voor beste prestaties in het integratiemilieu volgt. Mogelijk moet u ook een upgrade van de omgevingen aanvragen om de integratie te verbeteren.

Eerst, bepaal als uw milieu op de [ Verbeterde configuratie van de Integratie ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter) is.

* [ ProArchitectuur ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [ Architectuur van de Aanzet ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Controleer het plaatsingslogboek gebruikend één van deze methodes.

### Methode 1:

Voer de volgende opdracht uit met de Cloud CLI:

`magento-cloud activity:log -e <branch name>`

### Methode 2:

Controleer het meest recente plaatsingslogboek voor dat milieu in de [ Console van de Wolk ](https://console.adobecommerce.com).

Aan het eind van het plaatsingslogboek, als u iets als dit-eerste lijn ziet toont size=XL, en de resterende lijnen tonen size=L-dan betekent dat u op de Verbeterde configuratie van de Integratie bent.

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

Als u niet op de Verbeterde configuratie van de Integratie bent, kunt u [ om de verbetering/verbetering ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter) verzoeken.
Als u reeds op de Verbeterde configuratie van de Integratie bent of u nog prestatieskwesties na de verbetering ontmoet, zorg ervoor om de beste praktijken voor optimale prestaties in het integratiemilieu te volgen:

* [ ProArchitectuur ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [ Architectuur van de Aanzet ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

Als u de bovengenoemde aanbevelingen hebt voldaan, [ voorlegt een steunverzoek ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) voor extra hulp.
 
