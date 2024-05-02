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

De MDVA-30102-patch lost het probleem op dat de Redis-cache vol raakt en fouten genereert die problemen veroorzaken met de pagina&#39;s met productlijsten (PLP) en de pagina&#39;s met productdetails (PDP), zoals ontbrekende producten. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op cloudinfrastructuur 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De cache van Redis wordt vol en de toegewezen `maxmemory` lijkt ontoereikend. De lay-outcache bevatte geen TTL en werd niet verwijderd, waardoor de cache toenam en andere toetsen in Redis werden verwijderd. Hierdoor is al het Redis-geheugen toegewezen aan de lay-outcache.

<u>Vereisten</u>:

* De gebruiker moet Adobe Commerce 2.4 gebruiken en 100.000 eenvoudige producten (het producttype is niet van belang) en 50 categorieën hebben.
* De cache van Redis moet worden geconfigureerd volgens de stappen die zijn opgegeven in [Adobe Commerce Configuration Guide > Use Redis for the Adobe Commerce page and default cache](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) in onze ontwikkelaarsdocumentatie.

<u>Stappen om te reproduceren</u>:

1. Blader door alle PDP&#39;s en PLP&#39;s. U kunt [EIGEN ZAP](https://www.zaproxy.org/) om door de site te kruipen.
1. Neem het geheugengebruik van Redis waar.
1. Controleer ook de huidige configuratie en het gebruikte geheugen. Voer het volgende bevel in CLI in werking. Het controleert op gebruikt geheugen, maxmemory, geëlimineerde sleutels, en Redis omhoog tijd in dagen:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Verwachte resultaten</u>:

Redis cache mag niet snel groeien.

<u>Werkelijke resultaten</u>:

De cache van Redis groeit tot ~5GB. Er geldt een maximale limiet van 8 GB Redis-geheugen. Als u 1M-producten hebt, is er dus heel snel onvoldoende geheugen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
