---
title: 'ACSD-46618: widget productlijst toont onjuiste caching prijzen voor het programma geopende klant'
description: Pas een patch toe om het Adobe Commerce-probleem op te lossen, waarbij in de productlijst van de widget onjuiste cacheprijzen worden weergegeven voor een aangemelde klant.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618: De widget productlijst toont onjuiste caching prijzen voor een aangemelde klant

De ACSD-46618-patch lost het probleem op waarbij de widget voor de productlijst onjuiste prijzen in de cache weergeeft voor een aangemelde klant. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 wordt geïnstalleerd. De patch-id is ACSD-46618. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ACSD-46618-patch lost het probleem op waarbij de widget voor de productlijst onjuiste prijzen in de cache weergeeft voor een aangemelde klant.

<u> Stappen om </u> te reproduceren:

1. Selecteer in Adobe Commerce Admin **[!UICONTROL Stores]**, vervolgens **[!UICONTROL Configuration]** , vouw **[!UICONTROL Sales]** en selecteer **[!UICONTROL Tax]** . Werk de belastinginstellingen bij om de prijzen inclusief en exclusief belastingen weer te geven.
1. Plaats **[!UICONTROL Enable Cross Border Trade]** = _ja_.
1. Maak een belastingregel die alleen van toepassing is op de VS.
1. Voeg een widget aan de homepage toe met inbegrip van meer dan één product.
1. Creeer twee klanten met een adres van de V.S. en een niet adres van de V.S.
1. Meld u aan met de Amerikaanse klant van de winkel. Zorg ervoor dat de pagina in de cache is opgeslagen.
1. Neem de prijs waar die in de widget homepage wordt getoond.
1. Log uit en meld u aan met de niet-VS klant.

<u> Verwachte resultaten </u>:

De prijs die in de widget homepage wordt weergegeven, komt overeen met het adres van de klant.

<u> Ware resultaten </u>:

De widget homepage toont de prijzen aan de hand van de belasting voor niet-Amerikaanse klanten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
