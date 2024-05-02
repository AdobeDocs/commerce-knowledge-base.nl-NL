---
title: Meer ruimte toewijzen voor MySQL in Adobe Commerce in de cloud
description: Dit artikel bevat instructies voor het toewijzen van meer ruimte voor MySQL in Adobe Commerce op cloudinfrastructuur.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Meer ruimte toewijzen voor MySQL in Adobe Commerce in de cloud


## Ruimte toewijzen aan Starter-plan en Pro Plan-integratie

Voor alle Starter-planningsomgevingen en Pro-plan [Integratieomgeving](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), kunt u meer ruimte toewijzen voor MySQL in de `.magento/services.yaml` bestand, door de `mysql: disk:` parameter. Bijvoorbeeld:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Zie de [MySQL-service instellen](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) artikel ter referentie.

Wanneer u de `.magento/services.yaml` moet u de wijzigingen vastleggen en doorvoeren, zodat deze worden toegepast. De duw zal het plaatsingsproces teweegbrengen.

>[!WARNING]
>
>Een Starter-planpartitie mag nooit kleiner worden gemaakt (bijvoorbeeld van 30 GB naar 20 GB), omdat dit waarschijnlijk tot catastrofale gegevensbeschadiging zal leiden.

## Ruimte toewijzen aan Pro Plan Staging of Productie

Als u deze wijzigingen wilt aanbrengen in de omgeving Staging of Productie van het Pro-plan, moet u een [ondersteuningsticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Wanneer het voorleggen van een steunkaartje om opslag te verhogen, zal de steun moeten weten hoeveel en aan welke verdeling de opslag zou moeten worden toegepast (`/mysql` of `/exports`). Een verzoek om opslagverhoging vereist goedkeuring van uw Team van de Rekening van de Adobe, die uw recht van opslag (zoals in het ordeformulier) zal herzien alvorens goed te keuren.

## Toegewezen ruimte verkleinen is niet beschikbaar (Pro- en Starterabonnement)

Adobe Commerce Support kan een partitie uitbreiden (`/mysql` of `/exports`), maar kan een partitie niet verkleinen. Er bestaat een risico op gegevensbeschadiging als u dit doet. Daarom is het verlagen van de opslagcapaciteit voor een partitie niet beschikbaar.
Dit geldt ook voor het Starter-plan, waar u de toegewezen ruimte zelf kunt vergroten: verkleinen wordt ten zeerste afgeraden en kan leiden tot beschadiging van gegevens.
