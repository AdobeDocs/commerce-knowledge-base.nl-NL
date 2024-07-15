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

De ACSD-42807-patch verhelpt het probleem waarbij het aangepaste valutasymbool niet op de winkel wordt weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 geïnstalleerd is. De patch-id is ACSD-42807. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het aangepaste valutateken wordt niet weergegeven in de winkelruimte.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Montages** > **Configuraties** > **Algemeen** > **Opstelling van de Valuta** en selecteer om het even welke douanemunt. Bijvoorbeeld, **Mexicaanse Peso**.
1. Ga naar **Opslag** > **Montages** > **Configuraties** > **Algemeen** > **Opties van de Plaats** en selecteer **Spaans (Mexico)**.
1. Ga naar **Opslag** > **Symbolen van de Valuta** en vorm het muntsymbool aan **MX$**.
1. Controleer het valutasymbool op de voorzijde.

<u> Verwachte resultaten </u>:

Het standaardvalutasymbool is &quot;MX$&quot; met de valuta ingesteld op &quot;Mexicaanse Peso&quot; en de landinstelling ingesteld op &quot;Spaans (Mexico)&quot;.

<u> Ware resultaten </u>:

Het standaardvalutasymbool geeft &quot;$&quot; aan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
