---
title: '"ACSD-47137: de laadsnelheid van de afbeeldingsgalerie ` pub/media` folder big'' verbeteren'
description: Pas de ACSD-47137-patch toe om de laadsnelheid van de afbeeldingsgalerie te verbeteren wanneer de map 'pub/media' erg groot is.
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137: verbeter de snelheid waarmee afbeeldingsgalerie wordt geladen wanneer de map `pub/media` groot is

De ACSD-47137-patch verbetert de laadsnelheid van de afbeeldingsgalerie wanneer de map `pub/media` erg groot is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47137. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De laadsnelheid van de afbeeldingsgalerie neemt af wanneer de map `pub/media` erg groot is.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** aan _Nr_.
1. Reinig het configuratiecache.
1. Meld u af en meld u opnieuw aan als beheerder.
1. Ga in het zijpaneel Beheer naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en selecteer de hoofdcategorie.
1. Vouw de sectie **[!UICONTROL Content]** uit en klik op **[!UICONTROL Select from Gallery]** .

Bij het laden van de pagina verzendt Adobe Commerce de aanvraag `media_gallery/directories/gettree` om de mediamappenstructuur te laden.

<u> Verwachte resultaten </u>:

De aanvraag `media_gallery/directories/gettree` moet alleen inhoud laden uit de benodigde mappen, anders dan de padlijst in zijn geheel vanuit de map `pub/media/` .

<u> Ware resultaten </u>:

Het laden van de aanvraag `media_gallery/directories/gettree` duurt lang wanneer de map `pub/media/` veel inhoud bevat.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
