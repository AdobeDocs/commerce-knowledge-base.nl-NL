---
title: '''ACSD-47920: een gastgebruiker kan orders plaatsen via REST API, zelfs als [!UICONTROL Allow Guest Checkout] is uit'
description: Pas de ACSD-47920-patch toe om het Adobe Commerce-probleem op te lossen, waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als de [!UICONTROL Allow Guest Checkout] is uitgeschakeld.
exl-id: 8726eac4-ab19-4232-8e15-270d09bdc0a5
feature: REST, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-47920: een gastgebruiker kan opdrachten plaatsen via REST API, zelfs als **[!UICONTROL Allow Guest Checkout]** is uit

De ACSD-47920-patch verhelpt het probleem waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als de **[!UICONTROL Allow Guest Checkout]** is uitgeschakeld. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-47920. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Orders kunnen via de Rest API als gastgebruiker worden geplaatst, zelfs als de **[!UICONTROL Allow Guest Checkout]** is uitgeschakeld.

<u>Stappen om te reproduceren</u>:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > en stel de **[!UICONTROL Allow Guest Checkout]** tot _Nee_.
1. Gebruik REST API om een product aan een winkelwagentje toe te voegen en een bestelling te plaatsen.

<u>Verwachte resultaten</u>:

Uitchecken door gast API retourneert een fout *[!UICONTROL Sorry, guest checkout is not available]* indien **[!UICONTROL Allow Guest Checkout]** is ingesteld op _Nee_.

<u>Werkelijke resultaten</u>:

Met de API voor uitchecken van gasten kan een bestelling worden geplaatst, zelfs als **[!UICONTROL Allow Guest Checkout]** is ingesteld op _Nee_.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
