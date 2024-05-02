---
title: "MDVA-33632 patch: out of stock product reorder exception"
description: Met de MDVA-33632-patch wordt het probleem opgelost waarbij een uitzondering optreedt bij het opnieuw ordenen van een product uit de voorraad.
exl-id: 4a970db4-a64c-49b5-8c5f-8b9c5cdd946f
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-33632 patch: out of stock product reorder exception

Met de MDVA-33632-patch wordt het probleem opgelost waarbij een uitzondering optreedt bij het opnieuw ordenen van een product uit de voorraad.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce over wolkeninfrastructuur 2.3.6

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.0 - 2.3.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Een configureerbaar product met één optie maken (voorbeeld: **kleur** = *rood*) en instellen **kwik** = *1*.
1. Maak een klant en plaats een bestelling met dit product, dat op dat moment **kwik** = *0*.
1. Ga naar Beheer en probeer de vorige volgorde opnieuw in te stellen.

<u>Verwachte resultaten</u>:

De klant krijgt &quot;*Dit product is uit voorraad.*&quot; bericht voor een product uit de voorraad, zoals verwacht.

<u>Werkelijke resultaten</u>:

De klant krijgt &quot;*Dit product is uit voorraad.*&quot;bericht, en `var/log/exception.log` bevat een vergelijkbare uitzondering:

```php
[2020-12-09 00:17:36] report.CRITICAL: This product is out of stock. {"exception":"[object] (Magento\\Framework\\Exception\\LocalizedException(code: 0): This product is out of stock. at /vendor/magento/module-quote/Model/Quote.php:1711)"} []
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
