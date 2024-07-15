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

Het ACSD-52287 flard bevestigt de kwestie waar het statuut van gearchiveerde orden niet van *voltooide* aan *gesloten* op net verandert nadat het creditmemo werd voorgelegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-52287. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het statuut van gearchiveerde orden verandert niet van *voltooide* aan *gesloten* op net nadat het creditmemo werd voorgelegd.

<u> Stappen om </u> te reproduceren:

1. Configureer *[!UICONTROL Asynchronous Indexing]*.
   * Ga op de zijbalk Beheerder naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** .
   * Vouw in het linkerdeelvenster de sectie **[!UICONTROL Advanced]** uit en kies **[!UICONTROL Developer]** eronder.
   * Vouw de sectie **[!UICONTROL Grid Settings]** uit.
   * Plaats *[!UICONTROL Asynchronous indexing]* aan *ja*.
   * Klik op **[!UICONTROL Save Config]**.
1. Configureer de *[!UICONTROL Order Archive]* .
   * Ga op de zijbalk Beheerder naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** .
   * Vouw in het linkerdeelvenster de sectie **[!UICONTROL Sales]** uit en kies **[!UICONTROL Sales]** eronder.
   * Vouw de sectie **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** uit.
   * Plaats *[!UICONTROL Enable Archiving]* aan *ja* (de rest van de configuraties als gebrek verlaten).
   * Klik op **[!UICONTROL Save Config]**.
1. Plaats een volgorde op de voorgrond.
1. Voer de [!DNL cron] uit, zodat deze in de *[!UICONTROL Admin Order Grid]* wordt weergegeven.
1. De factuur en verschepen de orde om de ordestatus aan *Volledige* bij te werken.
1. Voer de [!DNL cron] uit om de *[!UICONTROL Sales Order Grid]* met de meest recente orderstatus bij te werken.
1. Archiveer de bestelling.
1. Ga naar de *[!UICONTROL Archived order grid]* .
1. Open de gearchiveerde orde en verbeter offline de orde door a [!UICONTROL Credit Memo] te creëren om [!UICONTROL Order status] te maken: *Gesloten*.
1. Voer de [!DNL cron] een paar keer uit.
1. Controleer *[!UICONTROL Archived order grid]* voor de nieuwe ordestatus.

<u> Verwachte resultaten </u>:

De orde wordt getoond als *Gesloten*.

<u> Ware resultaten </u>:

De orde wordt getoond als *Volledig*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
