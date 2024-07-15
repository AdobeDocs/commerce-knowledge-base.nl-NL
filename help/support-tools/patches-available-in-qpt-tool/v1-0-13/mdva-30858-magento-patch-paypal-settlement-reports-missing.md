---
title: 'MDVA-30858: PayPal Settlement Reports missing'
description: "De MDVA-30858-patch verhelpt ontbrekende PayPal-afwikkelingsrapporten wanneer er meerdere PayPal-accounts zijn. De rapporten moeten beschikbaar zijn onder Admin sidebar&gt; **Reports** &gt; Verkoop&gt; **PayPal Settlement**. In plaats daarvan, het bericht: *We konden geen verslagen vinden.* wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: PayPal-afwikkelingsrapporten ontbreken

De MDVA-30858-patch verhelpt ontbrekende PayPal-afwikkelingsrapporten wanneer er meerdere PayPal-accounts zijn. De rapporten zouden onder Admin sidebar > **Rapporten** > Verkoop > **PayPal-regeling** beschikbaar moeten zijn. In plaats daarvan, het bericht: *wij konden geen verslagen vinden.* wordt weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Oplossingen de kwestie waar geen verslagen in **Rapporten** > Verkoop > **PayPal Afwikkeling** werden gevonden wanneer het hebben van veelvoudige rekeningen PayPal.

<u> Stappen om </u> te reproduceren:

1. Configureer PayPal-afwikkelingsrapporten.
1. Ga naar Admin, aan **Rapporten** > Verkoop > **PayPal Afwikkeling**.
1. Voor de meest recente updates, klik **Updates van de Vangst** in de hoger-juiste hoek.

<u> Verwachte resultaten </u>:

Er moeten rapporten worden weergegeven.

<u> Ware resultaten </u>:

Er verschijnt niets in het raster, hoewel er rapporten beschikbaar zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
