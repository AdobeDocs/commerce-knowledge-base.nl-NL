---
title: 'MDVA-43605: De gegevens van de orde keren negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API'
description: De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605: De gegevens van de orde keren negatieve waarden voor rijtotalen terug wanneer het gebruiken van Rest API

De patch MDVA-43605 verhelpt het probleem waarbij de ordergegevens negatieve waarden voor rijtotalen retourneren bij gebruik van de Rest API. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ordegegevens geven negatieve waarden voor rijtotalen weer bij gebruik van de Rest API.

<u> Stappen om </u> te reproduceren:

1. Gratis verzending inschakelen.
1. Navigeer aan **Configuratie** > **Catalogus** > **Prijs** > en plaats het Reikwijdte van de Prijs van de Catalogus = Website.
1. Navigeer aan **Configuratie** > **Verkoop** > **Belasting** en update:
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

<u> Verwachte resultaten </u>:

De waarden van `base_row_total` en `base_row_total_incl_tax` in de reactie zijn nul.

<u> Ware resultaten </u>:

De velden `base_row_total` en `base_row_total_incl_tax` in het antwoord hebben negatieve waarden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
