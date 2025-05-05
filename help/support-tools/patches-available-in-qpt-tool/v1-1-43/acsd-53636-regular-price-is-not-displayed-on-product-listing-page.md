---
title: 'ACSD-53636: De normale prijs wordt niet weergegeven op de pagina [!UICONTROL Product Listing]'
description: Pas ACSD-53636 flard toe om de kwestie van Adobe Commerce te bevestigen waar de regelmatige prijs niet op * [!UICONTROL Product Listing] * pagina's voor configureerbare producten wordt getoond die kindproducten met speciale prijzen hebben.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636: De normale prijs wordt niet weergegeven op de pagina *[!UICONTROL Product Listing]*

De ACSD-53636-patch verhelpt het probleem dat de normale prijs niet wordt weergegeven op pagina&#39;s van *[!UICONTROL Product Listing]* voor configureerbare producten die onderliggende producten met speciale prijzen hebben. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-53636. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De normale prijs wordt niet weergegeven op pagina&#39;s van *[!UICONTROL Product Listing]* voor configureerbare producten die onderliggende producten met speciale prijzen hebben.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder en ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** en maak of open een configureerbaar product.
2. Open het onderliggende product en voeg een speciale prijs toe aan alle of een van de onderliggende producten en sla het product op.
3. Ga naar voren en open de **[!UICONTROL Product Detail]** -pagina van het configureerbare product. In de stalen van het onderliggende product met een speciale prijs ziet u het bestand *[!UICONTROL Regular price]* striked out (expected).
4. Ga naar voren en open de pagina **[!UICONTROL Product Listing]** voor het configureerbare product met een speciale prijs; zie dat de configureerbare veranderingen van het productmonster niet de regelmatige prijs in tegenstelling tot *[!UICONTROL Product Detail Page]* en andere eenvoudige producten tonen.

<u> Verwachte resultaten </u>:

Op de pagina *[!UICONTROL Product Listing]* geeft het configureerbare product de normale prijs voor het onderliggende product weer.

<u> Ware resultaten </u>:

Op de pagina *[!UICONTROL Product Listing]* ziet het configureerbare product niet de normale prijs voor het onderliggende product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
