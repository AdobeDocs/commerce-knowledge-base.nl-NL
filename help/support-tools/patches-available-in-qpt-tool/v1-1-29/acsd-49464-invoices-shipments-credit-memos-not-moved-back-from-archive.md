---
title: 'ACSD-49464: facturen, overbrengingen en creditnota''s niet van archief worden verplaatst'
description: Pas de ACSD-49464-patch toe om het Adobe Commerce-probleem op te lossen, waarbij facturen, verzendingen en creditnota's niet uit het archief worden verplaatst wanneer de orderId anders is.
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464: facturen, overbrengingen en creditnota&#39;s niet van archief worden verplaatst

De ACSD-49464-patch verhelpt het probleem waarbij facturen, verzendingen en creditnota&#39;s niet uit archief worden verplaatst wanneer orderId anders is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49464. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Facturen, verzendingen en creditnota&#39;s worden niet uit het archief verplaatst wanneer orderId anders is.

<u> Stappen om </u> te reproduceren:

1. Opdrachten, facturen, verzendingen en archivering van creditnota&#39;s inschakelen.
1. Maak en voltooi een bestelling, inclusief verzending, factuur en creditnota.
1. Zorg ervoor dat de verzend-, factuur- en creditnota-id&#39;s niet hetzelfde zijn als het ordernummer.
1. De volgorde verplaatsen naar archief.
1. Herstel de gearchiveerde bestelling naar orderbeheer.
1. Controleer de gegevens over factuur, verzending en creditnota onder de respectieve rasterpagina&#39;s [!UICONTROL Invoice] , [!UICONTROL Shipping] en [!UICONTROL Credit Memo] .

<u> Verwachte resultaten </u>:

De oorspronkelijke verwante records worden hersteld wanneer de volgorde wordt verplaatst van de archieflijst naar het orderbeheer.

<u> Ware resultaten </u>:

* Geen administratie voor verzending, factuur en creditnota&#39;s als alle id&#39;s verschillend zijn.
* Als de orde en verwante verslagen zelfde identiteitskaart hebben, dan zijn de verslagen teruggekeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
