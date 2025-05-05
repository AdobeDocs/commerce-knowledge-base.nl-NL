---
title: 'ACSD-54989: Bedrijfsbeheer kan geen bestelling uitvoeren als [!UICONTROL Enable Purchase Orders] is ingesteld op Ja en [!UICONTROL Purchase Order] is ingesteld op Nee'
description: Pas de ACSD-54989-patch toe om het Adobe Commerce-probleem op te lossen, waarbij bedrijfsbeheerders geen orders kunnen plaatsen als [!UICONTROL Enable Purchase Orders] op Ja is ingesteld en [!UICONTROL Purchase Order] op Nee is ingesteld.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989: Beheer van het bedrijf kan niet opdracht geven tot wanneer *[!UICONTROL Enable Purchase Orders]* aan *ja* wordt geplaatst en *[!UICONTROL Purchase Order]* aan *Nr*

ACSD-54989 flardmoeilijke situatie de kwestie waar de orden niet kunnen worden geplaatst als **[!UICONTROL Enable Purchase Orders]** aan *ja* en **[!UICONTROL Purchase Order]** geplaatst aan *Nr* worden geplaatst. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54989. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrijf admins kan geen orden plaatsen wanneer **[!UICONTROL Enable Purchase Orders]** aan *ja* wordt geplaatst en **Inkooporder** geplaatst aan *Nr*.

<u> Eerste vereisten </u>:

Installeer [!DNL B2B] modules.

<u> Stappen om </u> te reproduceren:

1. Laat bedrijf toe en verlaat [!UICONTROL **Order Approval Configuration]** > **&#x200B; [!UICONTROL Purchase Order**] = *Nr*.
1. Maak een eenvoudig product met een prijs van 100.
1. Maak een nieuw bedrijf via de beheerder.
1. Plaats [!UICONTROL **laat de Orden van de Aankoop toe**] aan *ja*.
1. Meld u aan als bedrijfsbeheerder op de winkel.
1. Voeg het gemaakte eenvoudige product toe aan het winkelwagentje.
1. Ga naar de afhandelingspagina en klik op **[!UICONTROL Place Order]** om de aankoop te voltooien.

<u> Verwachte resultaten </u>:

U kunt een bestelling plaatsen.

<u> Ware resultaten </u>:

De pagina **[!UICONTROL My Account]** wordt geopend en de volgorde wordt niet geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
