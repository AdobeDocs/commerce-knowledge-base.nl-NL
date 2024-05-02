---
title: 'MDVA-40401: Veranderingen van de gebruikswaarde van coupon na mislukte orde'
description: De patch MDVA-40401 verhelpt de kwestie waar de waarde van het coupongebruik verandert, zelfs na een mislukte bestelling. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40401. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401: Veranderingen van de gebruikswaarde van coupon na mislukte orde

De patch MDVA-40401 verhelpt de kwestie waar de waarde van het coupongebruik verandert, zelfs na een mislukte bestelling. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40401. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen de coupon niet opnieuw toepassen als ze deze in een mislukte volgorde hebben gebruikt.

<u>Stappen om te reproduceren</u>:

1. Maak een winkelwagentregel met automatisch gegenereerde coupons.
1. Voeg een product toe aan de winkelwagentje en pas de coupon toe.
1. Ga naar **Afhandeling**.
1. Maak het toegevoegde product &quot;uit voorraad&quot; voordat u de bestelling plaatst.
1. U moet een *uit voorraad* fout.
1. Uitsnijden uitvoeren.
1. Ga naar de kar en verwijder dat product.
1. Voeg nog een product toe en pas de coupon toe.

<u>Verwachte resultaten</u>:

De couponcode moet correct worden toegepast omdat de vorige volgorde niet is geplaatst.

<u>Werkelijke resultaten</u>:

Je krijgt een *couponcode is ongeldig* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
