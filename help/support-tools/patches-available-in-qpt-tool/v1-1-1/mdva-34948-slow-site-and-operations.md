---
title: "MDVA-34948: Verlichting van de website"
description: De MDVA-34948 Adobe Commerce patch verhelpt het probleem van de vertraging van de website. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 is geïnstalleerd. De patch-id is MDVA-34948. Het probleem is opgelost in Adobe Commerce versie 2.4.1.
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948: Verlichting website


## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce op onze cloudinfrastructuur 2.4.0-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce op locatie en Adobe Commerce op onze cloud-infrastructuur 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De website wordt langzaam, wat bewerkingen belemmert.

<u>Stappen om te reproduceren</u>:

1. Uitvoeren `show processlist` in MySQL.
1. Controleer of er meerdere query&#39;s zijn zoals:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Verwachte resultaten</u>:

`GET_LOCK` onmiddellijk uitgevoerd.

<u>Werkelijke resultaten</u>:

Meerdere `GET_LOCK` query&#39;s blijven maximaal 10 seconden vastzitten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
