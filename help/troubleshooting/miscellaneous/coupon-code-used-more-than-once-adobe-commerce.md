---
title: Coupon voor eenmalig gebruik wordt meerdere keren gebruikt, Adobe Commerce
description: Dit artikel biedt een oplossing voor de kwestie wanneer de coupons van de regel van de winkelwagentje niet goed werken. Handelaren stellen een coupon in voor eenmalig gebruik en klanten kunnen deze meerdere keren gebruiken.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Coupon voor eenmalig gebruik wordt meerdere keren gebruikt, Adobe Commerce

Dit artikel biedt een oplossing voor de kwestie wanneer de coupons van de regel van de winkelwagentje niet goed werken. Handelaren stellen een coupon in voor eenmalig gebruik en klanten kunnen deze meerdere keren gebruiken.


## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.4.3 en hoger

## Probleem

Handelaren stellen een coupon in voor eenmalig gebruik en klanten kunnen deze meerdere keren gebruiken.

<u> Stappen om </u> te reproduceren:

1. Maak een coupon en configureer de coupon voor eenmalig gebruik.
1. Ga door met de kassa.
1. Gebruik de coupon die u zojuist hebt gemaakt.
1. Ga door met de afhandeling en gebruik dezelfde coupon.

<u> Verwacht resultaat </u>:

De coupon kan slechts eenmaal worden gebruikt. Een berichtvertoningen: *de couponcode &quot;COUPON_NAME&quot;is ongeldig*.

<u> Werkelijk resultaat </u>:

De coupon kan meerdere keren worden gebruikt.


## Oorzaak

Handelaars hebben geen `sales.rule.update.coupon.usage` consumenteninstelling en -uitvoering die tot onjuist gedrag leiden.

## Oplossing

Voeg de `sales.rule.update.coupon.usage` consumer aan het `app/etc/env.php` dossier toe.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Voor gedetailleerde stappen, verwijs naar [ beheer berichtrijen > Configuratie ](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html#configuration) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

[ het Overzicht van de Rijen van het Bericht ](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html) in onze ontwikkelaarsdocumentatie.
