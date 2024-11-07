---
title: Meer ruimte toewijzen voor MySQL in Adobe Commerce in de cloud
description: Dit artikel bevat instructies voor het toewijzen van meer ruimte voor MySQL in Adobe Commerce op cloudinfrastructuur.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Meer ruimte toewijzen voor MySQL in Adobe Commerce in de cloud


## Ruimte toewijzen aan Starter-plan en Pro Plan-integratie

Voor alle milieu&#39;s van het Plan van de Starter en het Pro milieu van de Plan [ Integratie ](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), kunt u meer ruimte voor MySQL in het `.magento/services.yaml` dossier toewijzen, door de `mysql: disk:` parameter te verhogen. Bijvoorbeeld:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Zie de [ dienst MySQL van de Opstelling ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql) artikel voor verwijzing.

Nadat u het `.magento/services.yaml` -bestand hebt gewijzigd, moet u de wijzigingen doorvoeren en doorvoeren, zodat deze kunnen worden toegepast. De duw zal het plaatsingsproces teweegbrengen.

>[!WARNING]
>
>Een Starter-planpartitie mag nooit kleiner worden gemaakt (bijvoorbeeld van 30 GB naar 20 GB), omdat dit waarschijnlijk tot catastrofale gegevensbeschadiging zal leiden.

## Ruimte toewijzen aan Pro Plan Staging of Productie

Om deze veranderingen voor het Opvoeren of het milieu van de Productie van het Pro plan aan te brengen, moet u a [ steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed) tot stand brengen. Wanneer het voorleggen van een steunkaartje om opslag te verhogen, zal de steun moeten weten hoeveel en aan welke verdeling de opslag zou moeten worden toegepast (`/mysql` of `/exports`). Een verzoek om opslagverhoging vereist goedkeuring van uw Team van de Rekening van de Adobe, die uw recht van opslag (zoals in het ordeformulier) zal herzien alvorens goed te keuren.

## Toegewezen ruimte verkleinen is niet beschikbaar (Pro- en Starterabonnement)

De Steun van Adobe Commerce kan een verdeling (`/mysql` of `/exports`) groeien, maar kan geen verdeling krimpen. Er bestaat een risico op gegevensbeschadiging als u dit doet. Daarom is het verlagen van de opslagcapaciteit voor een partitie niet beschikbaar.
Dit geldt ook voor het Starter-plan, waar u de toegewezen ruimte zelf kunt vergroten: verkleinen wordt ten zeerste afgeraden en kan leiden tot beschadiging van gegevens.
