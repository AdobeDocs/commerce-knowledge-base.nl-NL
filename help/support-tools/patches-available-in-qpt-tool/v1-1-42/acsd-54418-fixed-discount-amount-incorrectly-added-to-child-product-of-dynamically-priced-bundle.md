---
title: "ACSD-54418: Vast kortingsbedrag onjuist toegevoegd aan een onderliggend product van dynamisch geprijsde bundel"
description: Pas de ACSD-54418-patch toe om het Adobe Commerce-probleem op te lossen waarbij het vaste kortingsbedrag onjuist wordt toegepast op elk onderliggend product van de dynamisch geprijsde bundel.
feature: Shopping Cart
role: Admin, Developer
exl-id: f9a00a4b-0a57-4a61-8b7c-6385e0751991
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-54418: Vast kortingsbedrag onjuist toegevoegd aan het onderliggende product van dynamisch geprijsde bundel.

De ACSD-54418-patch verhelpt het probleem waarbij de vaste korting onjuist wordt toegepast op elk onderliggend product van de dynamisch geprijsde bundel. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.42 is geïnstalleerd. De patch-id is ACSD-54418. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De vaste korting wordt onjuist toegepast op elk onderliggend product van de dynamisch geprijsde bundel.

<u>Stappen om te reproduceren</u>:

1. Een **[!UICONTROL bundle product]** met dynamische prijzen en *2* bundelopties.
1. Een **[!UICONTROL cart price rule]** met een specifieke couponcode die alleen van toepassing is op het gebundelde product **[!UICONTROL SKU]** en heeft een vaste korting.
1. Voeg het gebundelde product aan de kar toe.
1. Pas de **[!UICONTROL coupon code]**.
1. Controleer de korting op het winkelwagentje.

<u>Verwachte resultaten</u>:

De korting wordt slechts eenmaal toegepast op het hele gebundelde product.

<u>Werkelijke resultaten</u>:

De korting wordt toegepast op elk bundelonderliggend product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
