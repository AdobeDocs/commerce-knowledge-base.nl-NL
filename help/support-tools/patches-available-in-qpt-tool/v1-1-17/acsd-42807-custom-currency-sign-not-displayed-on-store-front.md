---
title: 'ACSD-42807: Aangepast valutasymbool niet weergegeven op de winkel'
description: De ACSD-42807-patch verhelpt het probleem waarbij het aangepaste valutasymbool niet op de winkel wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-42807. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: Aangepast valutateken niet weergegeven op de winkel

De ACSD-42807-patch verhelpt het probleem waarbij het aangepaste valutasymbool niet op de winkel wordt weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 is geïnstalleerd. De patch-id is ACSD-42807. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het aangepaste valutateken wordt niet weergegeven in de winkelruimte.

<u>Stappen om te reproduceren</u>:

1. Ga naar **Winkel** > **Instellingen** > **Configuraties** > **Algemeen** > **Valuta-instelling** en selecteer een aangepaste valuta. bijv. **Mexicaanse peso**.
1. Ga naar **Winkel** > **Instellingen** > **Configuraties** > **Algemeen** > **Landinstellingen** en selecteert u **Spaans (Mexico)**.
1. Ga naar **Winkel** > **Valutasymbolen** en configureer het valutasymbool om **MX$**.
1. Controleer het valutasymbool op de voorzijde.

<u>Verwachte resultaten</u>:

Het standaardvalutasymbool is &quot;MX$&quot; met de valuta ingesteld op &quot;Mexicaanse Peso&quot; en de landinstelling ingesteld op &quot;Spaans (Mexico)&quot;.

<u>Werkelijke resultaten</u>:

Het standaardvalutasymbool geeft &quot;$&quot; aan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
