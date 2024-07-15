---
title: 'ACSD-49065: Offertepunten zijn niet zichtbaar in admin'
description: Pas de ACSD-49065-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als ze alleen zijn toegewezen aan de aangepaste voorraad.
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065: Offertepunten zijn niet zichtbaar in admin

De ACSD-49065-patch verhelpt het probleem waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49065. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aanhalingstekens zijn niet zichtbaar in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad.

Vereisten:

**[!UICONTROL B2B]** en **[!UICONTROL Inventory]** modules moeten zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Company]** en **[!UICONTROL B2B Quote]** onder **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** in.
1. Maak een secundair **[!UICONTROL Inventory Source]** en wijs het toe aan een secundair **[!UICONTROL Inventory Stock]** .
1. Maak een nieuw product door alleen het secundaire (niet-standaard) **[!UICONTROL Inventory Source]** toe te wijzen.
1. Ga naar de winkel en maak een nieuw bedrijfsaccount. Meld u aan als de **[!UICONTROL Company Admin]** en voeg het gemaakte product toe aan de winkelwagentje.
1. Navigeer naar het winkelwagentje en *[!UICONTROL Request a Quote]* .
1. Ga naar de beheerder en bekijk de gevraagde prijsopgave op **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** .

<u> Verwachte resultaten </u>:

De punten zijn zichtbaar in het nieuwe citaat dat met nieuwe producten wordt gecreeerd zonder de producten opnieuw te bewaren.

<u> Ware resultaten </u>:

De sectie *[!UICONTROL Items Quoted]* is leeg. Als u het nieuwe product opnieuw opslaat, worden de items weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
