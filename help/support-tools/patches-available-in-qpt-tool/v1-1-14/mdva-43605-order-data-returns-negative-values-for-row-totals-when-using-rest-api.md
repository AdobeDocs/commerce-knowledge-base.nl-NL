---
title: 'MDVA-43605: De gegevens van de orde keert negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API'
description: De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: De gegevens van de orde keren negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API

De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ordegegevens geven negatieve waarden voor rijtotalen weer bij gebruik van de Rest API.

<u>Stappen om te reproduceren</u>:

1. Gratis verzending inschakelen.
1. Navigeren naar **Configuratie** > **Catalogus** > **Prijs** > en stel Catalog Price Scope = Website in.
1. Navigeren naar **Configuratie** > **Verkoop** > **Belasting** en bijwerken:
   * Belastingklasse voor verzending = belastbare goederen
   * Berekeningsinstellingen:
      * Catalogusprijs = inclusief belasting
      * Verzendprijs = inclusief prijs
      * Korting op prijzen toepassen = inclusief belasting
   * Weergave-instellingen prijs: inclusief belasting (alle velden)
   * Weergave-instellingen voor winkelwagentje: inclusief BTW (alle velden)
   * Orders, facturen, creditnota&#39;s:
      * Verzendbedrag weergeven = inclusief btw
1. Maak een belastingtarief voor de VS (staat = &#39;*&#39;), tarief percentage = 24,00
1. Maak een belastingregel met bovenstaande BTW-tarief.
1. Maak een regel voor de winkelwagenprijs met een specifieke coupon en een korting = $50 van het vaste bedrag voor de hele winkelwagen.
1. Maak vier producten met de volgende prijzen: $ 8,90, $ 5,90, $ 6,90 en $ 5,95.
1. Maak een beheerdersvolgorde met vier van deze producten met behulp van de couponcode die in de vorige stap is gemaakt. Gebruik de gratis verzending.
1. Betaling is niet vereist omdat de couponcode het carttotaal dekt.
1. Haal de orde op die enkel via Rest API eindpunt werd gecreeerd:

   ```json
   GET rest/V1/orders/1
   ```

<u>Verwachte resultaten</u>:

De waarden van `base_row_total` en `base_row_total_incl_tax` in de reactie is nul.

<u>Werkelijke resultaten</u>:

De `base_row_total` en `base_row_total_incl_tax` velden in het antwoord hebben negatieve waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
