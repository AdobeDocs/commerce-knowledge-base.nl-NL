---
title: 'ACSD-48262: producten die niet zichtbaar zijn op de winkel wanneer [!UICONTROL Allow All Products Per Page] is ingesteld [!UICONTROL Yes]'
description: Pas de ACSD-48262-patch toe om het Adobe Commerce-probleem op te lossen, waarbij producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op [!UICONTROL Yes] .
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262: producten die niet zichtbaar zijn op de winkel als [!UICONTROL Allow All Products Per Page] is ingesteld *[!UICONTROL Yes]*

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op *[!UICONTROL Yes]* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op *[!UICONTROL Yes]* .

<u> Stappen om </u> te reproduceren:

1. Maak een testcategorie.
1. Maak een testproduct in de testcategorie.
1. Blader naar de pagina met productcategorieën op de winkel en controleer of het product zichtbaar is.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** en stel de instelling [!UICONTROL Allow All Products Per Page] in op *[!UICONTROL Yes]* .
1. Cache wissen.
1. Categoriepagina controleren in de winkel.

<u> Verwachte resultaten </u>:

Het product is zichtbaar.

<u> Ware resultaten </u>:

Het product is niet zichtbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
