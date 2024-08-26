---
title: 'ACSD-56979: Productafbeeldingen die zijn verwijderd nadat de testupdate is verwijderd'
description: Pas de ACSD-56979-patch toe om het Adobe Commerce-probleem op te lossen waarbij productafbeeldingen worden verwijderd nadat een testupdate is verwijderd
feature: Products
role: Admin, Developer
source-git-commit: 8e916feab8be9d92d047fae8861a479070d448e8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-56979: Productafbeeldingen die zijn verwijderd na het stapelen van de update verwijderd

De ACSD-56979-patch verhelpt het probleem waarbij productafbeeldingen worden verwijderd nadat een testupdate is verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-56979. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce en de versies van de Magento Open Source:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Productafbeeldingen worden verwijderd nadat een testupdate is verwijderd.

<u> Stappen om </u> te reproduceren:

1. Ga op de zijbalk Commerce Admin naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en maak een product.
1. Upload een afbeelding onder **[!UICONTROL Images and Videos]** en sla het product op.
1. Selecteer **[!UICONTROL Schedule New Update]** in het vak **[!UICONTROL Scheduled Changes]** .
   1. Kies in de toekomst een begindatum van enkele minuten.
   1. Kies geen einddatum.
1. Selecteer in het vak **[!UICONTROL Scheduled Changes]** de koppeling **[!UICONTROL View/Edit]** .
1. Ga naar **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** en selecteer **[!UICONTROL Done]** .
1. Vernieuw de pagina.

<u> Verwachte resultaten </u>:

Aangezien de update voor de geplande begindatum wordt verwijderd, moet het product hetzelfde blijven.

<u> Ware resultaten </u>:

De afbeeldingsinhoud gaat verloren en er worden nul bytes weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
