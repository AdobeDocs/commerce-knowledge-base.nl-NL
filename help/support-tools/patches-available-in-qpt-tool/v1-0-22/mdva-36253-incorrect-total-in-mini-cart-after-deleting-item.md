---
title: 'MDVA-36253: Onjuist totaal in minikart na verwijderen van item'
description: De MDVA-36253-patch lost het probleem op waarbij de productprijs niet wordt bijgewerkt als u teruggaat naar de miniwinkelpagina nadat u een product hebt verwijderd bij het uitvoeren van de afhandelingsstap voor meerdere verzendingen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22 is geïnstalleerd. De patch-id is MDVA-36253. De kwestie is opgelost in Adobe Commerce 2.4.3.
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253: Onjuist totaal in minikart na verwijderen van item

De MDVA-36253-patch lost het probleem op waarbij de productprijs niet wordt bijgewerkt als u teruggaat naar de miniwinkelpagina nadat u een product hebt verwijderd bij het uitvoeren van de afhandelingsstap voor meerdere verzendingen. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.2 is geïnstalleerd. De patch-id is MDVA-36253. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuist totaal in minikaart na verwijderen van item.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als een klant met ten minste één adres.
1. Voeg vier producten toe aan winkelwagentje (prijs = 10 dollar voor elk).
1. Ga naar het winkelwagentje en klik op **Uitchecken met meerdere adressen**.
1. Eén item verwijderen.
1. Ga terug naar de startpagina.
1. Open het winkelwagentje en controleer de totale prijs.

<u>Verwachte resultaten</u>:

Het totaal is $30.

<u>Werkelijke resultaten</u>:

Het totaal is $40.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
