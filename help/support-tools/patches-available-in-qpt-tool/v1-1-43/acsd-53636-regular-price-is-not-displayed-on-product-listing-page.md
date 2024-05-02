---
title: 'ACSD-53636: de normale prijs wordt niet weergegeven op [!UICONTROL Product Listing] page'
description: Pas de ACSD-53636-patch toe om het Adobe Commerce-probleem op te lossen waarbij de normale prijs niet wordt weergegeven op *[!UICONTROL Product Listing]* pagina's voor configureerbare producten die kindproducten met speciale prijzen hebben.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: de normale prijs wordt niet weergegeven op *[!UICONTROL Product Listing]* page

De ACSD-53636-patch verhelpt het probleem waarbij de normale prijs niet wordt weergegeven op *[!UICONTROL Product Listing]* pagina&#39;s voor configureerbare producten die kindproducten met speciale prijzen hebben. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-53636. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De normale prijs wordt niet weergegeven op *[!UICONTROL Product Listing]* pagina&#39;s voor configureerbare producten die kindproducten met speciale prijzen hebben.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de beheerder en ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** en maak of open een configureerbaar product.
2. Open het onderliggende product en voeg een speciale prijs toe aan alle of een van de onderliggende producten en sla het product op.
3. Ga naar voorkant en open de **[!UICONTROL Product Detail]** pagina van het configureerbare product; in de stalen van het onderliggende product met een speciale prijs ziet u de *[!UICONTROL Regular price]* doorgehaald (verwacht).
4. Ga naar voorkant en open de **[!UICONTROL Product Listing]** pagina voor het configureerbare product met speciale prijs; zie dat de configureerbare veranderingen van het productmonster niet de regelmatige prijs in tegenstelling tot *[!UICONTROL Product Detail Page]* en andere eenvoudige producten.

<u>Verwachte resultaten</u>:

Op de *[!UICONTROL Product Listing]* op de pagina toont het configureerbare product de normale prijs voor het onderliggende product.

<u>Werkelijke resultaten</u>:

Op de *[!UICONTROL Product Listing]* pagina, toont het configureerbare product niet de regelmatige prijs voor zijn kindproduct.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
