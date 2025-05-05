---
title: 'ACSD-46865: [!UICONTROL shipment] en [!UICONTROL credit memo] niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld'
description: Pas de ACSD-46865-patch toe om het Adobe Commerce-probleem op te lossen waarbij [!UICONTROL shipment] - en [!UICONTROL credit memo] -rasters niet worden gevuld wanneer [!UICONTROL asynchronous indexing] wordt ingeschakeld.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] en [!UICONTROL credit memo] niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld

De ACSD-46865-patch verhelpt het probleem waarbij [!UICONTROL shipment] - en [!UICONTROL credit memo] -rasters niet worden gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46865. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Shipment] en [!UICONTROL credit memo] rasters worden niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. In [!DNL Commerce] Admin, ga **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA*.
2. Ga nogmaals naar **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]* .
3. Clean config-cache.
4. Plaats een nieuwe gastbestelling voor een eenvoudig product.
5. Uitsnijden uitvoeren.
6. Open de order in de [!UICONTROL Commerce] Admin door naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** te gaan en een factuur en een creditnota te genereren.
7. Verplaats de volgorde naar [!UICONTROL Archive] .
8. Maak een andere volgorde voor een eenvoudig product.
9. Uitsnijden uitvoeren.
10. Ga naar de nieuwe bestelling en genereer een nieuwe verzending, factuur en creditnota.
11. Uitsnijden uitvoeren.
12. Controleer de rasters [!UICONTROL shipments] , [!UICONTROL invoices] en [!UICONTROL credit memo] in de beheerder.

<u> Verwachte resultaten </u>:

Nieuwe [!UICONTROL shipment] , [!UICONTROL invoice] en [!UICONTROL credit memo] worden weergegeven.

<u> Ware resultaten </u>:

Nieuw [!UICONTROL shipment] , [!UICONTROL invoice] en [!UICONTROL credit memo] worden niet weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
