---
title: 'ACSD-49480: Verdere regels die niet werken negeren'
description: Pas de ACSD-49480-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals bedoeld.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals bedoeld

De ACSD-49480-patch verhelpt het probleem waarbij de [!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals bedoeld. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-49480. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] werkt niet zoals bedoeld.

<u>Stappen om te reproduceren</u>:

1. Een **[!UICONTROL Cart Price Rule]** met een couponcode (geef deze de naam *TEST*) die een korting van $10 geeft aan de *Product-id 1* in de **[!UICONTROL Actions]** tab met [!UICONTROL Discard Subsequent Rules] instellen op *[!UICONTROL Yes]* en [!UICONTROL Priority] instellen op *1*.
1. Een andere maken **[!UICONTROL Cart Price Rule]** zonder couponcode die een korting van € 5 geeft aan *Product ID 2* in de **[!UICONTROL Actions]** tab met [!UICONTROL Priority] instellen op *2*. We gaan ervan uit dat dit een wereldwijde verkoop is voor *Product ID 2*.
1. Ga naar de voorste site en voeg *Product-id 1* en *Product ID 2* in de kar.
1. Pas de *TEST* couponcode.

<u>Verwachte resultaten</u>

* *Korting 1* wordt toegepast op *Product-id 1*.
* *Korting 2* wordt toegepast op *Product ID 2*.

<u>Werkelijke resultaten</u>

* Alleen *Korting 1* wordt toegepast op *Product-id 1*.
* *Korting 2* is niet toegepast op *Product ID 2*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
