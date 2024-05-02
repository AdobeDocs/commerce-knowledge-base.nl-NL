---
title: "MDVA-38929: FPT heeft een onjuist totaal"
description: De patch MDVA-38929 lost het probleem op waarbij de factuur met FPT een onjuist totaal geeft wanneer de bestelling wordt betaald met winkelkrediet. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 1ed0e311-f4a5-4dc0-98fc-fc1cc9458516
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-38929: FPT toont onjuist totaal

De patch MDVA-38929 lost het probleem op waarbij de factuur met FPT een onjuist totaal geeft wanneer de bestelling wordt betaald met winkelkrediet. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De factuur met FPT geeft een onjuist totaal als de bestelling wordt betaald met winkelkrediet.

<u>Stappen om te reproduceren</u>:

1. Maak een klant en zorg ervoor dat de klant voldoende krediet heeft om de bestelling te dekken.
1. Schakel FPT in en voeg FPT toe aan een product.
1. Van het vooreind, login zoals de klant enkel creeerde.
1. Voeg het product met FPT toe aan de kar.
1. Afhandeling en betaling met winkelkrediet. Het moet een betalingsopdracht van nul zijn.
1. Ga naar Bestellingen en factureer de bestelling handmatig.
1. Controleer het totaal van de factuur.

<u>Verwachte resultaten</u>:

* Het totaal van de factuur is nul.
* Het totaalbedrag van de bestelling is nul.

<u>Werkelijke resultaten</u>:

* Het totaalbedrag op de factuur toont nog steeds het FPT-bedrag.
* Het betaalde totaalbedrag toont nog steeds het FPT-bedrag.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
