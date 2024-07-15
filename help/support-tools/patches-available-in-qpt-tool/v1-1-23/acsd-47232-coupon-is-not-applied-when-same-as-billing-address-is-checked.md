---
title: 'ACSD-47232: coupon wordt niet toegepast wanneer [!UICONTROL Same as Billing Address] wordt gecontroleerd'
description: Pas de ACSD-47232-patch toe om het Adobe Commerce-probleem op te lossen waarbij geen coupon wordt gebruikt wanneer [!UICONTROL Same as Billing Address] wordt gecontroleerd.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: coupon wordt niet toegepast bij controle van [!UICONTROL Same as Billing Address]

De ACSD-47232-patch corrigeert de kwestie waar de coupon niet wordt gebruikt wanneer **[!UICONTROL Same as Billing Address]** wordt gecontroleerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23 wordt geïnstalleerd. De patch-id is ACSD-47232. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Coupon wordt niet toegepast wanneer **[!UICONTROL Same as Billing Address]** wordt gecontroleerd.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren.
1. Creeer een eenvoudig product met gewicht = *8*.
1. Maak een nieuwe klant met standaardfacturering en standaardverzendadres.
1. Maak een regel voor de winkelprijs met een coupon.
   * In **[!UICONTROL Conditions]** secties, voeg *Totale Gewicht gelijk of groter dan 5* toe
1. Maak een nieuwe volgorde in [!UICONTROL Commerce] Admin.
   * Gebruik de klant die u zojuist hebt gemaakt
   * Een product toevoegen
   * Probeer de coupon toe te passen

<u> Verwachte resultaten </u>:

Coupon wordt toegepast.

<u> Ware resultaten </u>:

U krijgt een fout gelijkend op het volgende: *de 123 couponcode is ongeldig. Verifieer de code en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
