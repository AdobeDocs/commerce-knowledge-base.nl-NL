---
title: 'ACSD-54418: Vast kortingsbedrag onjuist toegevoegd aan onderliggend product van dynamisch geprijsde bundel'
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

De ACSD-54418-patch verhelpt het probleem waarbij de vaste korting onjuist wordt toegepast op elk onderliggend product van de dynamisch geprijsde bundel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54418. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De vaste korting wordt onjuist toegepast op elk onderliggend product van de dynamisch geprijsde bundel.

<u> Stappen om </u> te reproduceren:

1. Creeer a **[!UICONTROL bundle product]** met dynamische tarifering en *2* bundelopties.
1. Maak een **[!UICONTROL cart price rule]** met een specifieke couponcode die alleen van toepassing is op het gebundelde product **[!UICONTROL SKU]** en een vaste korting heeft.
1. Voeg het gebundelde product aan de kar toe.
1. Pas **[!UICONTROL coupon code]** toe.
1. Controleer de korting op het winkelwagentje.

<u> Verwachte resultaten </u>:

De korting wordt slechts eenmaal toegepast op het hele gebundelde product.

<u> Ware resultaten </u>:

De korting wordt toegepast op elk bundelonderliggend product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
