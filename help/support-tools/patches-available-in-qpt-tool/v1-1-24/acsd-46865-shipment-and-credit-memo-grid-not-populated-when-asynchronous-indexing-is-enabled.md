---
title: '"ACSD-46865: [!UICONTROL shipment] en [!UICONTROL credit memo] niet gevuld wanneer [!UICONTROL asynchronous indexing] is enabled'''
description: Pas de ACSD-46865-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL shipment] en [!UICONTROL credit memo] rasters worden niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] en [!UICONTROL credit memo] niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld

De ACSD-46865-patch verhelpt het probleem waarbij: [!UICONTROL shipment] en [!UICONTROL credit memo] rasters worden niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46865. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Shipment] en [!UICONTROL credit memo] rasters worden niet gevuld wanneer [!UICONTROL asynchronous indexing] is ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. In de [!DNL Commerce] Beheerder, ga naar **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *JA*.
2. Opnieuw Ga naar **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Clean config-cache.
4. Plaats een nieuwe gastbestelling voor een eenvoudig product.
5. Uitsnijden uitvoeren.
6. Open de volgorde in het dialoogvenster [!UICONTROL Commerce] Beheerder door naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en een factuur en een creditnota genereren.
7. De volgorde verplaatsen naar [!UICONTROL Archive].
8. Maak een andere volgorde voor een eenvoudig product.
9. Uitsnijden uitvoeren.
10. Ga naar de nieuwe bestelling en genereer een nieuwe verzending, factuur en creditnota.
11. Uitsnijden uitvoeren.
12. Controleer de [!UICONTROL shipments], [!UICONTROL invoices], en [!UICONTROL credit memo] rasters in de beheerder.

<u>Verwachte resultaten</u>:

Nieuw [!UICONTROL shipment], [!UICONTROL invoice] en [!UICONTROL credit memo] worden weergegeven.

<u>Werkelijke resultaten</u>:

Nieuw [!UICONTROL shipment], [!UICONTROL invoice], en [!UICONTROL credit memo] niet worden weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
