---
title: "ACSD-54680: B2B-offerte voor een product met Meerdere toegewezen bronnen kan worden verwerkt"
description: Pas de ACSD-54680-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het B2B-citaat voor een product met Meerdere toegewezen bronnen niet kan worden verwerkt.
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680: B2B Citaat voor een product met Veelvoudige Toegewezen Bronnen kan niet worden verwerkt.

De ACSD-54680-patch verhelpt het probleem waarbij het B2B-citaat voor een product met Meerdere toegewezen bronnen niet kan worden verwerkt. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.40 is geïnstalleerd. De patch-id is ACSD-54680. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

B2B Citaat voor een product met Veelvoudige Toegewezen Bronnen kan niet worden verwerkt.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** en maak twee nieuwe bronnen: **Bron 1** en **Bron 2**.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** en een nieuwe voorraad aanmaken: **Voorraad A**, en wijst u deze toe aan de hoofdwebsite **Bron 1** en **Bron 2** aan de Commissie.
1. Een eenvoudig product maken, toewijzen **Bron 1** en **Bron 2** en stelt Qty = in *2* voor elke bron. (de verkoopbare hoeveelheid van het product moet *4* als gevolg daarvan).
1. Maak een bedrijfsaccount.
1. Ga naar de **[!UICONTROL Storefront]** en meld u aan bij de bedrijfsaccount.
1. Voeg het eenvoudige product toe aan het winkelwagentje met hoeveelheid = *4*.
1. Open de *[!UICONTROL Shopping cart]* en klik op **[!UICONTROL Request a quote]** knop.
1. Voeg een opmerking en een aanhalingsteken toe en klik op **[!UICONTROL Send a Request]** knop.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Onlangs verzonden offerte openen.

<u>Verwachte resultaten</u>:

De vermelde items bevatten het geordende product.

<u>Werkelijke resultaten</u>:

De pagina-sectie met items waarnaar wordt verwezen, is leeg en het is niet mogelijk om het aanhalingsteken te verwerken.
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
