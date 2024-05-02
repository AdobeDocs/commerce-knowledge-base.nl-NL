---
title: "MDVA-44533: Kortingen die onjuist zijn toegepast op gebundeld kinderproduct"
description: De patch MDVA-44533 verhelpt het probleem waarbij een korting onjuist wordt toegepast op een gebundeld onderliggend product. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44533. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533: Korting wordt onjuist toegepast op gebundeld onderliggend product

De patch MDVA-44533 verhelpt het probleem waarbij een korting onjuist wordt toegepast op een gebundeld onderliggend product. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 is geïnstalleerd. De patch-id is MDVA-44533. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Korting wordt onjuist toegepast op een gebundeld onderliggend product.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product met een prijs van 50$.
1. Maak een gebundeld product en wijs het eenvoudige product als enige optie voor het gebundelde product toe.
1. Een prijsregel voor winkelwagentjes maken met:

   * Voorwaarde: als de totale hoeveelheid groter is dan 130$
   * Actie: korting voor vaste bedragen van 10$ wordt toegepast

1. Ga naar de winkel en voeg het bundelproduct aan de kar met hoeveelheid = 1 toe.
1. Ga naar het winkelwagentje en controleer of de totale kosten van het bundelproduct 50$ bedragen en of de korting niet van toepassing is.
1. Wijzig de hoeveelheid in 2 en werk de winkelwagen bij. De totale kosten van het gebundelde product moeten nu 100$ bedragen.

<u>Verwachte resultaten</u>:

De korting wordt niet toegepast omdat het subtotaal 100\$ is, wat minder dan 130\$ in de regelvoorwaarde is.

<u>Werkelijke resultaten</u>:

De korting wordt toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
