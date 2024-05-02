---
title: Redis unserialize error ` setup:static-content:inzetten"
description: Dit artikel bevat een oplossing voor de ongedaan-maken-fout van Redis bij het uitvoeren van de setup van "magento":static-content:inzetten".
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Fout bij ongedaan maken van Redis `setup:static-content:deploy`

Dit artikel bevat een oplossing voor de Redis-fout voor ongedaan maken bij uitvoering `magento setup:static-content:deploy`.

Wordt uitgevoerd `magento setup:static-content:deploy` veroorzaakt de fout van Redis:

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

Het probleem wordt veroorzaakt door parallelle storende processen op de Redis-verbinding.

Uitvoeren om te herstellen `setup:static-content:deploy` in een single-thread-modus door de volgende omgevingsvariabele in te stellen:

```
STATIC_CONTENT_THREADS =1
```

of voert u de `setup:static-content:deploy` gevolgd door de `-j 1` (of `--jobs=1` ).

Merk op dat het onbruikbaar maken van multithreading het proces vertraagt om statische activa op te stellen.

## Betrokken versies

* Adobe Commerce op locatie: 2.1.2 en hoger
* Adobe Commerce over cloudinfrastructuur 2.1.2 en hoger
* Redis, elke versie

## Probleem

De `setup:static-content:deploy` veroorzaakt de Redis-fout:

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

Hier, een proces in `App/Config/Type/System.php` had een reactie verwacht voor `system_defaultweb`, maar heeft een reactie ontvangen voor `system_cache_exists` dat is gebeurd via een ander proces . Zie de gedetailleerde uitleg in [Jason Woods-bericht](https://github.com/magento/magento2/issues/9287#issuecomment-302362283).

## Oplossing

Parallelisme uitschakelen en uitvoeren `setup:static-content:deploy` in een single-thread-modus door de volgende omgevingsvariabele in te stellen:

```
STATIC_CONTENT_THREADS =1
```

U kunt ook de opdracht `setup:static-content:deploy` gevolgd door de `-j 1` (of `--jobs=1`).

>[!NOTE]
>
>Op de single-thread wijze, kan het statische proces van de inhoudsplaatsing vier keer langer duren.

## Meer informatie

In onze documentatie voor ontwikkelaars:

* [Redis configureren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html)
* [Opdrachtregelupgrade](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)
