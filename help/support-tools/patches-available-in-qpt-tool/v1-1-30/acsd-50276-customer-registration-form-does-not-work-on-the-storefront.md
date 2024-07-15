---
title: "ACSD-50276: registratieformulier voor klanten werkt niet bij opslag als een kenmerk voor meerdere klanten wordt gemaakt."
description: Pas de ACSD-50276-patch toe om het Adobe Commerce-probleem op te lossen waarbij het registratieformulier van de klant niet werkt op de winkel als een kenmerk van een klant met meerdere selecties wordt gemaakt.
exl-id: 542eb93a-3719-4e2d-bb1b-87817f0812b4
feature: Attributes, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-50276: registratieformulier voor klanten werkt niet bij opslag als een kenmerk voor meerdere klanten is gemaakt

De ACSD-50276-patch verhelpt het probleem waarbij het registratieformulier van de klant niet in de winkel werkt als een kenmerk van een klant met meerdere selecties wordt gemaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-50276. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het registratieformulier voor klanten werkt niet in de winkel als een kenmerk voor meerdere klanten wordt gemaakt.

<u> Stappen om </u> te reproduceren:

1. Creeer een nieuw multi-select klantenattribuut met de volgende montages:

   * *[!UICONTROL Required = Yes]*
   * *[!UICONTROL Show on storefront = Yes]* selecteert u *[!UICONTROL Customer registration form]* .

1. Open het registratieformulier voor klanten in de winkel.

<u> Verwachte resultaten </u>:

Het klantregistratieformulier wordt geladen.

<u> Ware resultaten </u>:

* Het registratieformulier voor klanten wordt niet geladen.
* De volgende fout wordt geregistreerd:

  ```PHP
  report. CRITICAL: Exception: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in vendor/magento/module-custom-attribute-management/Block/Form/Renderer/Multiselect.php
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
