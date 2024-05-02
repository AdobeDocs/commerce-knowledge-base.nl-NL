---
title: Omleiden naar een bovenliggende omgeving bij toegang tot nieuwe integratieomgeving
description: Dit artikel bevat instructies voor het oplossen van problemen voor de Adobe Commerce met betrekking tot cloudinfrastructuur, waarbij het proberen om toegang te krijgen tot de nieuwe integratieomgeving in plaats daarvan naar de bovenliggende omgeving leidt.
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Omleiden naar een bovenliggende omgeving bij toegang tot nieuwe integratieomgeving

Dit artikel bevat instructies voor het oplossen van problemen voor de Adobe Commerce met betrekking tot cloudinfrastructuur, waarbij het proberen om toegang te krijgen tot de nieuwe integratieomgeving in plaats daarvan naar de bovenliggende omgeving leidt.

Als u dit wilt corrigeren, moet u de waarde van de basis\_url in de database corrigeren en ervoor zorgen dat `UPDATE_URLS` variable value is ingesteld op `true`. Meer informatie vindt u in de onderstaande secties.

Betrokken versies en edities:

* Adobe Commerce op cloudinfrastructuur 2.X.X

## Probleem

<u>Stappen om te reproduceren</u>:

1. Kloon de bestaande tak van de Integratie.
1. Klik op de URL voor toegang tot de nieuwe omgeving.

<u>Verwacht resultaat</u>:

U gaat naar de nieuwe omgeving.

<u>Werkelijk resultaat</u>:

U wordt omgeleid aan het milieu op de oudertak.

## Oplossing

Als u het probleem wilt verhelpen, moet u het `base_url` waarden (veilig en onveilig) in het gegevensbestand van het douanemilieu en reeks `UPDATE_URL` in de `.magento.env.yaml` bestand.

### Basis\_url-waarden in database corrigeren

De veranderingen in het gegevensbestand kunnen of manueel of gebruikend Adobe Commerce CLI worden gedaan, als u versie 2.2.0 en later bent.

#### Corrigeer de waarden in de database handmatig

1. Maak verbinding met de database.
1. Voer de volgende opdrachten uit:

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### Corrigeer de database met Adobe Commerce CLI (beschikbaar voor versies 2.2.X)

1. Meld u aan als, of schakel over naar, de [Adobe Commerce-eigenaar bestandssysteem](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html).
1. Voer de volgende opdrachten uit:

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### Stel de `UPDATE_URLS` variabel

In uw lokale codebase, in `.magento.env.yaml` bestandenset:

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### Configuratiecache wissen

Voor de uit te voeren veranderingen, schoon het configuratiecache door het volgende bevel in werking te stellen:

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## Verwante artikelen in onze documentatie voor ontwikkelaars:

[Variabelen implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
