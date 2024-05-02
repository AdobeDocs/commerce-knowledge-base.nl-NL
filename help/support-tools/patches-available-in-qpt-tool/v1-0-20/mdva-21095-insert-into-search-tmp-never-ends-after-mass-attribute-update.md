---
title: 'MDVA-21095: INSERT INTO "search_tmp..." never end after mass attribute update'
description: De patch MDVA-21095 verhelpt het probleem wanneer een query "INSERT INTO" "search\_tmp.." nooit eindigt na een update van het massakenmerk. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-21095. Er is momenteel geen plan om dit probleem in toekomstige versies op te lossen.
exl-id: fd599473-b49a-4f9c-a13f-612d05e43f09
feature: Attributes, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-21095: INSERT INTO &quot;search_tmp...&quot; never end after mass attribute update

De patch MDVA-21095 lost het probleem op wanneer een query wordt uitgevoerd `INSERT INTO` &quot;search\_tmp...&quot; eindigt nooit na een update van het kenmerk massa. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-21095. Er is momenteel geen plan om dit probleem in toekomstige versies op te lossen.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`INSERT INTO` &quot;search\_tmp...&quot; eindigt nooit na een update van het kenmerk massa.

<u>Stap om te reproduceren</u>:

Voer een update uit voor de waarden van massaferekenmerken met ~30.000 items.

<u>Verwachte resultaten</u>:

Het herindexeringsproces wordt normaal voltooid, zoals verwacht.

<u>Werkelijke resultaten</u>:

Het herindexeringsproces is voltooid, maar er zijn veel vragen `INSERT INTO` &quot;search\_tmp...&quot; begint totdat de server de `pm.max_children` De parameterwaarde en PHP-fpm gaan dood, en deze komen constant opnieuw voor zelfs na het opnieuw beginnen MySQL en proces doden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
