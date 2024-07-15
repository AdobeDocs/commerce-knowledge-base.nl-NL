---
title: 'MDVA-30102: Redis cache getting full'
description: De MDVA-30102-patch lost het probleem op dat de Redis-cache vol raakt en fouten genereert die problemen veroorzaken met de pagina's met productlijsten (PLP) en de pagina's met productdetails (PDP), zoals ontbrekende producten. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 is geïnstalleerd.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: Redis cache wordt vol

De MDVA-30102-patch lost het probleem op dat de Redis-cache vol raakt en fouten genereert die problemen veroorzaken met de pagina&#39;s met productlijsten (PLP) en de pagina&#39;s met productdetails (PDP), zoals ontbrekende producten. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 geïnstalleerd is.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De cache van Redis wordt vol en de toegewezen `maxmemory` lijkt onvoldoende. De lay-outcache bevatte geen TTL en werd niet verwijderd, waardoor de cache toenam en andere toetsen in Redis werden verwijderd. Hierdoor is al het Redis-geheugen toegewezen aan de lay-outcache.

<u> Eerste vereisten </u>:

* De gebruiker moet Adobe Commerce 2.4 gebruiken en 100.000 eenvoudige producten (het producttype is niet van belang) en 50 categorieën hebben.
* Het geheime voorgeheugen van Redis moet volgens stappen worden gevormd die in [ de Gids van de Configuratie van Adobe Commerce > Redis van het Gebruik voor de pagina van Adobe Commerce en standaardgeheime voorgeheugen ](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) in onze ontwikkelaarsdocumentatie worden gegeven.

<u> Stappen om </u> te reproduceren:

1. Blader door alle PDP&#39;s en PLP&#39;s. U kunt [ ZEEP VAN HET ASPIS gebruiken ](https://www.zaproxy.org/) om de plaats te kruipen.
1. Neem het geheugengebruik van Redis waar.
1. Controleer ook de huidige configuratie en het gebruikte geheugen. Voer het volgende bevel in CLI in werking. Het controleert op gebruikt geheugen, maxmemory, geëlimineerde sleutels, en Redis omhoog tijd in dagen:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u> Verwachte resultaten </u>:

Redis cache mag niet snel groeien.

<u> Ware resultaten </u>:

De cache van Redis groeit tot ~5GB. Er geldt een maximale limiet van 8 GB Redis-geheugen. Als u 1M-producten hebt, is er dus heel snel onvoldoende geheugen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
