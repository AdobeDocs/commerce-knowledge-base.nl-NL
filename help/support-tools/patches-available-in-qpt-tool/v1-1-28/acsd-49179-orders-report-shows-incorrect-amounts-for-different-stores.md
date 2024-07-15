---
title: 'ACSD-49179: het orderrapport toont onjuiste hoeveelheden voor verschillende winkels.'
description: Pas de ACSD-49179-patch toe om het Adobe Commerce-probleem op te lossen, waarbij in het orderrapport onjuiste bedragen worden weergegeven in het geval van verschillende valuta's voor verschillende winkels.
exl-id: 01e4cd2d-6c33-4cf5-bf31-bbc34eaaed1a
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-49179: het orderrapport toont onjuiste hoeveelheden voor verschillende winkels

De ACSD-49179-patch corrigeert de kwestie waar in het orderrapport onjuiste bedragen worden weergegeven in het geval van verschillende valuta&#39;s voor verschillende winkels. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49179. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het orderrapport geeft onjuiste bedragen weer in het geval van verschillende valuta&#39;s voor verschillende winkels.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** en stel [!UICONTROL Catalog Price Scope] = [!UICONTROL Website] in.
1. Maak een aanvullende website-, opslag- en winkelweergave.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** en stel de volgende opties in:
   * Standaardconfiguratie:
      * Basisvaluta: USD
      * Standaardweergavevaluta: USD
      * Toegestane valuta: EUR, USD en THB (Thai Baht)
   * Hoofdwebsite:
      * Basisvaluta: EUR
      * Standaardweergavevaluta: EUR
      * Toegestane valuta&#39;s: EUR
   * Aanvullende nieuwe website:
      * Basisvaluta: THB (Thai Baht)
      * Standaardweergavevaluta: THB (Thai Baht)
      * Toegestane valuta&#39;s: THB (Thai Baht)
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** en stel de lege conversietarieven voor THB in (stel de tarieven in op 1,0000).
1. Maak een product, wijs het toe aan beide websites en plaats een bestelling met dit product in de extra website die u eerder hebt gemaakt.
1. Zorg ervoor dat de orde in *de status van de Verwerking* (factuur het) is.
1. Ga op de achtergrond naar **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
1. Klik op de waarschuwing **[!UICONTROL Yellow]** om de statistieken te vernieuwen.
1. Stel het bereik van het rapport op de eerder gemaakte aanvullende website in en stel het filter als volgt in:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: De dag waarop de testvolgorde werd geplaatst
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u> Verwachte resultaten </u>:

Het verkooptotaal geeft het juiste bedrag weer dat is omgezet in de valuta van de website.

<u> Ware resultaten </u>:

Het totaal is nul.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
