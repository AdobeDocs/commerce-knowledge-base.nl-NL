---
title: "MDVA-41350: Uitzondering wanneer de beheerder producten toevoegt buiten zijn toegang"
description: De flard MDVA-41350 lost de kwestie op waar een uitzonderingsfout in plaats van een beperkt toegangsbericht wordt geworpen wanneer een admin gebruiker een product in de orde door SKU toevoegt die buiten hun toegang is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-41350. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350: Uitzondering wanneer admin producten buiten hun toegang toevoegt

De flard MDVA-41350 lost de kwestie op waar een uitzonderingsfout in plaats van een beperkt toegangsbericht wordt geworpen wanneer een admin gebruiker een product in de orde door SKU toevoegt die buiten hun toegang is. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11 is geïnstalleerd. De patch-id is MDVA-41350. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een admin gebruiker met beperkte toegang een product door SKU buiten hun toegang in de orde toevoegt, komt een uitzondering in plaats van een bericht voor dat de gebruiker op de hoogte brengt van hun beperkte toegang.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder als een gebruiker met alleen toegang tot een specifieke website.
1. Ga naar **Verkoop** > **Orders** en klik op **Nieuwe volgorde maken**.
1. Selecteer een klant en een winkelweergave.
1. Klikken op **Producten toevoegen door SKU**.
1. Zoeken naar een SKU die niet is toegewezen aan een website of niet is toegewezen aan de website waartoe u toegang hebt.
1. Klikken **Toevoegen aan bestelling**.

<u>Verwachte resultaten</u>:

Er wordt een geschikt foutbericht weergegeven.

<u>Werkelijke resultaten</u>:

Er treedt een uitzondering op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
