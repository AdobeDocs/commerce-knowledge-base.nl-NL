---
title: "ACSD-52287: De status van gearchiveerde orders verandert niet"
description: Pas de ACSD-52287-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van gearchiveerde bestellingen niet verandert van *completed* in *closed* op het raster nadat het creditmemo is verzonden.
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# ACSD-52287: De status van gearchiveerde orders verandert niet

De ACSD-52287-patch verhelpt het probleem waarbij de status van gearchiveerde bestellingen niet verandert van *voltooid* tot *gesloten* op het netwerk nadat de kredietmemo is ingediend. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 is geïnstalleerd. De patch-id is ACSD-52287. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van gearchiveerde bestellingen verandert niet van *voltooid* tot *gesloten* op het netwerk nadat de kredietmemo is ingediend.

<u>Stappen om te reproduceren</u>:

1. Configureren *[!UICONTROL Asynchronous Indexing]*.
   * Ga op de zijbalk Beheerder naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Vouw in het linkerdeelvenster de **[!UICONTROL Advanced]** en kiest u **[!UICONTROL Developer]** onder.
   * Vouw de sectie **[!UICONTROL Grid Settings]** uit.
   * Set *[!UICONTROL Asynchronous indexing]* tot *Ja*.
   * Klik op **[!UICONTROL Save Config]**.
1. Vorm *[!UICONTROL Order Archive]*.
   * Ga op de zijbalk Beheerder naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Vouw in het linkerdeelvenster de **[!UICONTROL Sales]** en kiest u **[!UICONTROL Sales]** onder.
   * Vouw de sectie **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** uit.
   * Set *[!UICONTROL Enable Archiving]* tot *Ja* (De rest van de configuraties als standaard blijven gebruiken).
   * Klik op **[!UICONTROL Save Config]**.
1. Plaats een volgorde op de voorgrond.
1. Voer de [!DNL cron]  om in de *[!UICONTROL Admin Order Grid]*.
1. Factuur en verzend de bestelling om de status van de bestelling bij te werken naar *Voltooid*.
1. Voer de [!DNL cron]  om de *[!UICONTROL Sales Order Grid]* met de meest recente orderstatus.
1. Archiveer de bestelling.
1. Ga naar de *[!UICONTROL Archived order grid]*.
1. Open de gearchiveerde volgorde en verdien de volgorde offline door een [!UICONTROL Credit Memo] om [!UICONTROL Order status]: *Gesloten*.
1. Voer de [!DNL cron] voor een paar keer.
1. Controleer de *[!UICONTROL Archived order grid]* voor de nieuwe orderstatus.

<u>Verwachte resultaten</u>:

De volgorde wordt weergegeven als *Gesloten*.

<u>Werkelijke resultaten</u>:

De volgorde wordt weergegeven als *Voltooid*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
