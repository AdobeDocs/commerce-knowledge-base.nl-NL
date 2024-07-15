---
title: 'Redis unserialize fout "opstelling :static-content: stelt"op'
description: 'Dit artikel verstrekt een moeilijke situatie voor Redis unserialize fout wanneer het runnen van ` magento opstelling :static-content: opstellen `.'
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis unserialize error `setup:static-content:deploy`

Dit artikel bevat een oplossing voor de Redis-fout bij het ongedaan maken van de serienummering wanneer `magento setup:static-content:deploy` wordt uitgevoerd.

Als `magento setup:static-content:deploy` wordt uitgevoerd, treedt de fout Redis op:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Het probleem wordt veroorzaakt door parallelle storende processen op de Redis-verbinding.

Als u wilt oplossen, voert u `setup:static-content:deploy` uit in een modus met één thread door de volgende omgevingsvariabele in te stellen:

```
STATIC_CONTENT_THREADS =1
```

of voert u de opdracht `setup:static-content:deploy` uit, gevolgd door het argument `-j 1` (of `--jobs=1` ).

Merk op dat het onbruikbaar maken van multithreading het proces vertraagt om statische activa op te stellen.

## Betrokken versies

* Adobe Commerce op locatie: 2.1.2 en hoger
* Adobe Commerce over cloudinfrastructuur 2.1.2 en hoger
* Redis, elke versie

## Probleem

Als u de opdracht `setup:static-content:deploy` uitvoert, treedt de fout Redis op:

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## Oorzaak

Het probleem wordt veroorzaakt door parallelle storende processen op de Redis-verbinding.

In dit geval verwachtte een proces in `App/Config/Type/System.php` een reactie voor `system_defaultweb` , maar ontving het een reactie voor `system_cache_exists` die door een ander proces werd gemaakt. Zie de gedetailleerde verklaring in [ Jason Woods&#39; post ](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Oplossing

U kunt parallellisme uitschakelen en `setup:static-content:deploy` uitvoeren in een modus met één thread door de volgende omgevingsvariabele in te stellen:

```
STATIC_CONTENT_THREADS =1
```

U kunt ook de opdracht `setup:static-content:deploy` uitvoeren, gevolgd door het argument `-j 1` (of `--jobs=1` ).

>[!NOTE]
>
>Op de single-thread wijze, kan het statische proces van de inhoudsplaatsing vier keer langer duren.

## Meer informatie

In onze documentatie voor ontwikkelaars:

* [ vormen Redis ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [ bevel-lijn verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
