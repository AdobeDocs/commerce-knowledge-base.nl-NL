---
title: "MDVA-20376: geen dergelijke entiteit met customerId"
description: De patch MDVA-20376 lost de kwestie van een *No zulk een entiteit met customerId = 1* fout voor geregistreerde klanten na ordeplaatsing op. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.4.
exl-id: a12865d0-4ac2-444f-b8b6-22cae249f5d4
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-20376: geen dergelijke entiteit met customerId

De MDVA-20376-patch lost het probleem van een *Geen dergelijke entiteit met customerId = 1* fout voor aangemelde klanten na de plaatsing van de bestelling. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten met aanmelding ontvangen *Geen dergelijke entiteit met customerId = 1* fout na plaatsing van de order.

<u>Stappen om te reproduceren</u>:

1. Navigeer naar de storefront en meld u aan als geregistreerde gebruiker.
1. Plaats een bestelling.
1. Ga in de CLI naar `var/log` en u ziet de `exception.log` bestand.

<u>Verwachte resultaten</u>:

Er worden geen fouten weergegeven in de logboeken, zoals u had verwacht.

<u>Werkelijke resultaten</u>:

Het uitzonderingslogboek vult met fouten gelijkend op:

```php
report.CRITICAL: No such entity with customerId = 1 {"exception":"[object] (Magento\\Framework\\Exception\\NoSuchEntityException(code: 0): No such entity with customerId = 1 at /mnt/data/home/nyarlaga/dev/232/vendor/magento/framework/Exception/NoSuchEntityException.php:50)"} []
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
