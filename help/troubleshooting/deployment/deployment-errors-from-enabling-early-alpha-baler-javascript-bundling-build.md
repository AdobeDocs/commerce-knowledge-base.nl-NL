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

<u> Stappen om </u> te reproduceren:

1. De handelaar probeert om **SCD\_USE\_BALER** variabele in te voegen in het bouwstijlstadium van het `.magento.env.yaml` dossier, dat het bundelpakket van JavaScript van de Baler toelaat.
1. De handelaar voegt ook de composer-afhankelijkheid Baler toe: `"magento/module-baler": "1.0.0-alpha"` aan `require` sectie van `composer.json` .

<u> Verwacht resultaat </u>:

Succesvolle implementatie.

<u> Werkelijk resultaat </u>:

De handelaar ziet de volgende foutenmelding in de plaatsingslogboeken op de wolk, die `<project home>/var/log/cloud.log` is, op het statische stadium van de inhoudsimplementatie:

```
[2020-08-19 12:06:12] WARNING: [1007] Baler JS bundling cannot be used because of the following issues:
        [2020-08-19 12:06:12] WARNING:  - Path to baler executable could not be found. The Node package may not be installed or may not be linked.
```

## Oorzaak

De Baler-module bevindt zich momenteel in de vroege fase van alfaontwikkeling en het installatieproces van de Baler-extensie is complex.

## Oplossing

U kunt bestaande documentatie van de Alpha van Baler bij [ bekijken Github/Magento/Baler/Begonnen het worden met alpha ](https://github.com/magento/baler/blob/master/docs/ALPHA.md). Het is echter niet klaar voor gebruik in de productie en het wordt op eigen risico gebruikt. U wordt aangeraden in plaats daarvan Javascript-bestanden (JS) samen te voegen of te bundelen met ingebouwde bundeling (basisbundeling) van Adobe Commerce voor optimalisatie van bestanden.

* U kunt het samenvoegen of het bundelen in Admin (het samenvoegen en het bundelen kunnen niet tezelfdertijd worden toegelaten) aanzetten: **Slaat** > **Montages** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **de Montages van JavaScript**.
* U kunt ingebouwde Adobe Commerce-bundeling (basisbundeling) ook inschakelen via de opdrachtregel: `php -f bin/magento config:set dev/js/enable_js_bundling 1`

Meer leren, verwijs naar [ CSS en Javascript dossieroptimalisering op Adobe Commerce op wolkeninfrastructuur en Adobe Commerce op-gebouw ](https://support.magento.com/hc/en-us/articles/360044482152).
