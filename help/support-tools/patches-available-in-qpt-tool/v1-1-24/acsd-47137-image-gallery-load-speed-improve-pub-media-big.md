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

# ACSD-47137: de snelheid van het laden van afbeeldingsgalerieën verhogen wanneer `pub/media` map groot

De ACSD-47137-patch verbetert de laadsnelheid van de afbeeldingsgalerie wanneer de `pub/media` map is erg groot. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47137. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De laadsnelheid van de afbeeldingsgalerie is traag wanneer de `pub/media` map is erg groot.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** tot _Nee_.
1. Reinig het configuratiecache.
1. Meld u af en meld u opnieuw aan als beheerder.
1. Ga op de zijbalk Beheerder naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en selecteert u de hoofdcategorie.
1. Breid uit **[!UICONTROL Content]** en klik op **[!UICONTROL Select from Gallery]**.

Bij het laden van de pagina verzendt Adobe Commerce `media_gallery/directories/gettree` verzoek om de mediamappenstructuur te laden.

<u>Verwachte resultaten</u>:

De `media_gallery/directories/gettree` De aanvraag moet alleen inhoud laden uit de benodigde mappen, anders dan de volledige padlijst vanuit de `pub/media/` map.

<u>Werkelijke resultaten</u>:

De `media_gallery/directories/gettree` Het laden van een aanvraag duurt lang als de `pub/media/` map bevat veel inhoud.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
