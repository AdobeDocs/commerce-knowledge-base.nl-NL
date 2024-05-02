---
title: "MDVA-31763: Catalogusprijsregels worden teruggedraaid totdat ze handmatig opnieuw worden berekend"
description: De patch MDVA-31763 lost het probleem op waarbij de prijsregels voor catalogi worden teruggedraaid tot de redex handmatig wordt uitgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-31763. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763: Catalogusprijsregels worden teruggedraaid totdat ze handmatig opnieuw worden berekend

De patch MDVA-31763 lost het probleem op waarbij de prijsregels voor catalogi worden teruggedraaid tot de redex handmatig wordt uitgevoerd. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-31763. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer `catalogrule_product` gedeeltelijke indexeerfunctie wordt uitgevoerd op configureerbare producten, de catalogusregels verdwijnen.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder-back-end.
1. Ga naar **Winkels** > **Attributen** > **Product** en zoek naar het kenmerk &quot;manufacturer&quot;.
   * Voeg een paar opties toe en stel &quot;Gebruik voor de Voorwaarden van de Regel van de Bevordering&quot;aan *Ja*.
1. Ga naar **Winkels** > **Attributen** > **Kenmerksets**.
   * Selecteer de standaardkenmerkset en voeg het kenmerk &quot;manufacturer&quot; eraan toe.
1. Maak een configureerbaar product met een paar variaties.
1. Stel de waarde van het kenmerk &quot;manufacturer&quot; in voor eerder gemaakt configureerbaar product.
1. Catalogusregels maken:
   * Actief = Ja
   * Websites = hoofdwebsite
   * Klantengroepen = NIET AANGEMELD
   * Voorwaarden: fabrikant = \&lt;selected value=&quot;&quot; for=&quot;&quot; configurable=&quot;&quot; product=&quot;&quot;>
   * Handelingen: elke korting
1. Voer een volledige index uit.
1. Controleer de productprijs op PDP en controleer of de prijs correct is.
1. Werk het &quot;gewicht&quot;attribuut van het gecreeerde configureerbare product bij.
1. Controleer de productprijs op PDP.

<u>Verwachte resultaten</u>:

De catalogusprijsregels die zijn ingesteld voor configureerbare producten worden niet verwijderd tijdens een gedeeltelijke herindex.

<u>Werkelijke resultaten</u>:

De catalogusprijsregels die zijn ingesteld voor configureerbare producten, zijn verdwenen tijdens een gedeeltelijke herindexering.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
