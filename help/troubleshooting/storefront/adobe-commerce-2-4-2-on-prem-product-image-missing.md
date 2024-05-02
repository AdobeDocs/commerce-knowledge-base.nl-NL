---
title: "Adobe Commerce on-premisse 2.4.2: product image missing"
description: In dit artikel wordt een bekende Adobe Commerce-uitgave (2.4.2) beschreven waarbij de productafbeelding niet naar de productpagina wordt geüpload. Dit probleem zal in een toekomstige versie na versie 2.4.3 worden opgelost. Er is momenteel geen oplossing beschikbaar, maar als tijdelijke oplossing kunt u Nginx uitschakelen om de grootte van afbeeldingen te wijzigen.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce op locatie 2.4.2: afbeelding van product ontbreekt

In dit artikel wordt een bekende Adobe Commerce-uitgave (2.4.2) beschreven waarbij de productafbeelding niet naar de productpagina wordt geüpload. Dit probleem zal in een toekomstige versie na versie 2.4.3 worden opgelost. Er is momenteel geen oplossing beschikbaar, maar als tijdelijke oplossing kunt u Nginx uitschakelen om de grootte van afbeeldingen te wijzigen.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.2

## Probleem

De productafbeelding wordt opgeslagen in het dialoogvenster `s3` emmertje, maar wordt niet gesynchroniseerd naar de `pub/media` directory. Dit probleem treedt alleen op wanneer u beide gebruikt:

* Nginx voor site ingeschakeld om de grootte van afbeeldingen te wijzigen
* AWS `s3` als media-opslag

<u>Vereisten</u>:

Adobe Commerce geïnstalleerd met Nginx.

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce configureren voor gebruik van AWS `s3` als media-opslag.
1. Nginx configureren met de `nginx.conf.sample` configuratiebestand in de installatiemap van Adobe Commerce en een virtuele Nginx-host. Zie [Nginx configureren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) in onze ontwikkelaarsdocumentatie.
1. Maak een eenvoudig product met één productafbeelding.
1. Nginx heeft een configuratie zonder opmerkingen voor het vergroten of verkleinen van afbeeldingen in `nginx.conf.sample` vergelijkbaar met deze :

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Verwachte resultaten</u>:

De productafbeelding wordt geüpload naar de productpagina.

<u>Werkelijke resultaten</u>:

De productafbeelding wordt niet geüpload naar de productpagina.

## Workaround

Schakel Nginx uit om het formaat van afbeeldingen te wijzigen.
