---
title: Duizenden resultaten behalen wanneer u op zoek bent naar een bepaald product
description: Dit artikel biedt een oplossing voor het probleem waarbij u duizenden zoekresultaten krijgt wanneer u naar een bepaald product zoekt.
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Duizenden resultaten behalen wanneer u op zoek bent naar een bepaald product

Dit artikel biedt een oplossing voor het probleem waarbij u duizenden zoekresultaten krijgt wanneer u op zoek bent naar een bepaald product.

## Betrokken producten en versies

* Adobe Commerce alle versies met [!DNL ElasticSearch] geïnstalleerd

## Problemen

U zoekt een bepaald product (bijvoorbeeld, *WSH12-32-Rood*) maar het onderzoek keert veel gelijkaardige producten terug.

## Oplossingen

De aard van een full-text zoekopdracht in [!DNL ElasticSearch] is gebaseerd op relevantie, niet op exacte overeenkomst. De meest relevante overeenkomsten (zoals exact overeenkomende SKU) worden dus eerst geordend.

Als u echter een zoekresultaat nodig hebt dat exact overeenkomt met uw zoekterm (exacte overeenkomst), moet u aanhalingstekens gebruiken voor uw zoekopdracht. Bijvoorbeeld, zal de vraag voor *WSH12-32-Rood* zonder citaten verscheidene resultaten met de nauwkeurige gelijke terugkeren (product met *SKU WSH12-32-Rood*) die eerst in het resultaat verschijnen. Maar geciteerde vraag *&quot;WSH12-32-rood&quot;* zal slechts één nauwkeurig gelijke resultaat terugkeren.
