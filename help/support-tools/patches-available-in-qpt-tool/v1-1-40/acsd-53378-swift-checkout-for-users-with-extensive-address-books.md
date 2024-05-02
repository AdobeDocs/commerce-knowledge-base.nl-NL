---
title: 'ACSD-53378: Verbeterde uitcheckervaring voor klanten met uitgebreide adresboeken'
description: Pas de ACSD-53378-patch toe om het Adobe Commerce-probleem op te lossen waar zich prestatieproblemen voordoen die worden veroorzaakt door adresvolumes van grote klanten.
feature: Customers, Checkout
role: Admin
exl-id: 561462fd-844b-40e0-9ccd-25f7aa9be161
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-53378: Verbeterde uitcheckervaring voor klanten met uitgebreide adresboeken

De ACSD-53378-patch verhelpt het probleem waar prestatieproblemen optreden die worden veroorzaakt door adresvolumes van grote klanten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40 is geïnstalleerd. De patch-id is ACSD-53378. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van Adobe Commerce worden zeer traag als een klant een groot aantal adressen heeft.

Als de configuratieoptie *[!UICONTROL Enable search address]* krachtens **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** wordt geactiveerd, wordt het volledige klantenadresboek niet meer volledig verwerkt. Het aantal verwerkte klantenadressen wordt bepaald door het plaatsen *[!UICONTROL Customer Addresses Limit]* krachtens  **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product van Admin.
1. Creeer een klant met een uitgebreid adresboek dat 1000 adressen bevat.
1. Navigeer naar de voorkant en voeg het product toe aan de winkelwagentje.
1. Open de winkelwagenpagina.

<u>Verwachte resultaten</u>:

Het aantal adressen van de klant heeft geen invloed op de reactietijd.

<u>Werkelijke resultaten</u>:

Het laden van de winkelwagenpagina kost veel tijd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
