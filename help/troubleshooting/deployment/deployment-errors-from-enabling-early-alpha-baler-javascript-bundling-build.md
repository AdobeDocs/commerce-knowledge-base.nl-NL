---
title: Implementatiefouten die voortvloeien uit het inschakelen van de vroege alfakalermodule
description: De handelaar ervaart plaatsingsfouten wanneer het gebruiken van de module Baler op een productiemilieu, aangezien de eigenschap momenteel in de vroege alpha- ontwikkelingsfase is.
exl-id: 6cdac0a5-eaeb-467d-8369-9017aed6219e
feature: Build, Deploy, Extensions, SCD, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Implementatiefouten die voortvloeien uit het inschakelen van de vroege alfakalermodule

De handelaar ervaart plaatsingsfouten wanneer het gebruiken van de module Baler op een productiemilieu, aangezien de eigenschap momenteel in de vroege alpha- ontwikkelingsfase is.

>[!WARNING]
>
>Early-alpha Baler Javascript-bundeling is niet klaar voor productiegebruik en wordt op eigen risico gebruikt.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.3.x en 2.4.x.
* Adobe Commerce op locatie 2.3.x en 2.4.x.

## Probleem

We raden handelaren niet aan de Baler-module te gebruiken in een productieomgeving, aangezien deze zich momenteel in de vroege fase van alfaontwikkeling bevindt. Het gebruiken van het kan in plaatsingsfouten resulteren.

<u>Stappen om te reproduceren</u>:

1. De handelaar probeert het **SCD\_USE\_BALER** variabele in de bouwfase van `.magento.env.yaml` bestand, dat het bundelpakket Baler JavaScript inschakelt.
1. De handelaar voegt ook de composer van Baler toe gebiedsdeel: `"magento/module-baler": "1.0.0-alpha"` tot `require` deel van `composer.json`.

<u>Verwacht resultaat</u>:

Succesvolle implementatie.

<u>Werkelijk resultaat</u>:

De handelaar ziet de volgende foutenmelding in de plaatsingslogboeken op de wolk, die is `<project home>/var/log/cloud.log`, zodra de statische inhoud wordt geïmplementeerd:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Oorzaak

De Baler-module bevindt zich momenteel in de vroege fase van alfaontwikkeling en het installatieproces van de Baler-extensie is complex.

## Oplossing

U kunt de bestaande Baler Alpha documentatie bekijken op [Github/Magento/Baler/Aan de slag met de alfa](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Het is echter niet klaar voor gebruik in de productie en het wordt op eigen risico gebruikt. U wordt aangeraden in plaats daarvan Javascript-bestanden (JS) samen te voegen of te bundelen met ingebouwde bundeling (basisbundeling) van Adobe Commerce voor optimalisatie van bestanden.

* U kunt samenvoeging of bundeling inschakelen in Beheer (samenvoeging en bundeling kunnen niet tegelijkertijd worden ingeschakeld): **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **JavaScript-instellingen**.
* U kunt ingebouwde bundeling (basisbundeling) voor Adobe Commerce ook inschakelen via de opdrachtregel: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Raadpleeg voor meer informatie [CSS- en Javascript-bestandsoptimalisatie op Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie](https://support.magento.com/hc/en-us/articles/360044482152).
