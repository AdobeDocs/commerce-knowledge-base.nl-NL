---
title: 'MDVA-30858: PayPal Settlement Reports missing'
description: "De MDVA-30858-patch verhelpt ontbrekende PayPal-afwikkelingsrapporten wanneer er meerdere PayPal-accounts zijn. De rapporten moeten beschikbaar zijn onder Admin sidebar &gt; **Reports** gt; Verkoop &gt; **PayPal Settlement**. In plaats daarvan, het bericht: *We konden geen verslagen vinden.* wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: PayPal-afwikkelingsrapporten ontbreken

De MDVA-30858-patch verhelpt ontbrekende PayPal-afwikkelingsrapporten wanneer er meerdere PayPal-accounts zijn. De rapporten moeten beschikbaar zijn onder Admin sidebar > **Rapporten** > Verkoop > **PayPal-afwikkeling**. In plaats daarvan wordt het bericht: *We konden geen records vinden.* worden weergegeven. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over wolkeninfrastructuur 2.3.4

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij geen records zijn gevonden in **Rapporten** > Verkoop > **PayPal-afwikkeling** als er meerdere PayPal-accounts zijn.

<u>Stappen om te reproduceren</u>:

1. Configureer PayPal-afwikkelingsrapporten.
1. Ga naar Beheer, naar **Rapporten** > Verkoop > **PayPal-afwikkeling**.
1. Voor de meest recente updates klikt u op **Updates ophalen** in de rechterbovenhoek.

<u>Verwachte resultaten</u>:

Er moeten rapporten worden weergegeven.

<u>Werkelijke resultaten</u>:

Er verschijnt niets in het raster, hoewel er rapporten beschikbaar zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
