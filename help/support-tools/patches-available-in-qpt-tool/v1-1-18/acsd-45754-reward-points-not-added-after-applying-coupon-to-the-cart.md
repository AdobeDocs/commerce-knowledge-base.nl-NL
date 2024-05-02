---
title: "ACSD-45754: Achterwaartse punten niet toegevoegd na het toepassen van coupon op winkelwagentje"
description: De ACSD-45754-patch lost de kwestie op waarbij geen bonuspunten worden toegevoegd nadat een coupon op de wagen is aangebracht. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45754. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754: Achterwaartse punten niet toegevoegd na het toepassen van coupon op winkelwagentje

De ACSD-45754-patch lost de kwestie op waarbij geen bonuspunten worden toegevoegd nadat een coupon op de wagen is aangebracht. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45754. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Retourpunten worden niet toegevoegd na het toepassen van een coupon op de winkelwagentje.

<u>Vereisten</u>:

PayPal-betalingsmethode is geconfigureerd.

<u>Stappen om te reproduceren</u>:

1. Wisselkoersen voor bonuspunten maken door naar **Winkel** > **Overige instellingen** > **Reward Exchange Rates**.
1. Maak een prijsregel voor winkelwagentjes met een couponcode om 100 bonuspunten toe te passen voor aangemelde klanten.
1. Bekijk een product als aangemelde klant met PayPal en de waardeboncode.
1. Controleer de bonusgeschiedenis onder de klantenrekening in admin.

<u>Verwachte resultaten</u>:

De punten van beloningen worden toegevoegd aan de klant volgens de prijsregel.

<u>Werkelijke resultaten</u>:

Er worden geen bonuspunten aan de klant toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
