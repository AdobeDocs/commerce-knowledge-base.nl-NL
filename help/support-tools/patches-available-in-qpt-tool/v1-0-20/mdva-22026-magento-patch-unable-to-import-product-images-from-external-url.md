---
title: "MDVA-22026: Kan geen productafbeeldingen van externe URL importeren"
description: Met de MDVA-22026-patch kunt u geen productafbeeldingen importeren van een externe URL.
exl-id: 29043c6c-daf2-4925-85bf-49eeeee3742c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# MDVA-22026: Kan geen productafbeeldingen importeren van externe URL

Met de MDVA-22026-patch kunt u geen productafbeeldingen importeren van een externe URL.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 is geïnstalleerd. De patch-id is MDVA-22026. Het probleem is opgelost in Adobe Commerce versie 2.3.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op cloudinfrastructuur 2.3.2-p2

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.2-2.3.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u>Stappen om te reproduceren</u>:

1. Ga in Beheer naar **Systeem** > **Importeren**.
1. Set **Type entiteit** = *Producten*.
1. Set **Gedrag importeren** = *Toevoegen/bijwerken*.
1. Set **Aantal toegestane fouten** = *10000*.
1. Selecteer het bestand dat u wilt importeren.
1. Klik op de knop **Gegevens controleren** (die het bestand moet valideren).
1. Klik op de knop **Importeren** knop.

<u>Verwachte resultaten</u>:

Producten uit CSV-bestanden, waaronder afbeeldingen van externe URL&#39;s, zijn naar behoren geïmporteerd.

<u>Werkelijke resultaten</u>:

Producten uit CSV-bestanden, waaronder afbeeldingen van externe URL&#39;s, zijn niet geïmporteerd en er is een vergelijkbare fout opgetreden:

```php
1. Imported resource (image) could not be downloaded from external resource due to timeout or access permissions in row(s): 4, 5, 8, 9, 16, 18, 20, 21, 22, 23, 26, 27, 28, 52, 53, 55, 58, 63, 70, 71, 77, 78, 83, 84, 91
```

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen afhankelijk van uw implementatiemethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html).
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Patch controleren voor Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
