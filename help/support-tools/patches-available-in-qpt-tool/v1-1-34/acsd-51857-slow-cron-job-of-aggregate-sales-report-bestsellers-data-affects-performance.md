---
title: 'ACSD-51857: Trage baan van &grave; aggregate_sales_report_bestsellers_data'' beïnvloedt prestaties'
description: Pas ACSD-51857 flard toe om de kwestie van Adobe Commerce te bevestigen waar de langzame bouwbaan &grave; aggregate_sales_report_bestsellers_data &grave; grote &grave; verkoop_order &grave; en &grave; verkoop_order_item' gegevensbestandlijsten beïnvloedt.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: langzame uitsnijdtaak van `aggregate_sales_report_bestsellers_data` heeft invloed op de prestaties

De ACSD-51857-patch verhelpt het probleem waarbij de trage uitsnijdtaak `aggregate_sales_report_bestsellers_data` van invloed is op grote `sales_order` - en `sales_order_item` databasetabellen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-51857. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van de snijtaak van `aggregate_sales_report_bestsellers_data` zijn traag bij `sales_order` - en `sales_order_item` -databasetabellen.

Om dit op te lossen, is de belangrijkste gegevensvraag die grabs gegevens voor het rapport aan een efficiëntere vorm opnieuw geschreven. Het gebruikt nu een subquery om gegevenssubset te bepalen.

De subquery werkt zo snel mogelijk als volgt: er is een nieuwe index toegevoegd voor de databasetabel `sales_order` : `SALES_ORDER_STORE_STATE_CREATED` gebaseerd op de kolommen `store_id` , `state` en `created_at` .

<u> Eerste vereisten </u>

Zorg voor een groot aantal bestellingen per dag.

<u> Stappen om te reproduceren </u>

1. Voer de `aggregate_sales_report_bestsellers_data` -uitsnijdtaak uit.
1. Controleer de gegevens die moeten worden weergegeven op het dashboard Beheer, onder het tabblad **[!UICONTROL Bestsellers]** .

<u> Verwachte resultaten </u>:

*[!UICONTROL Quantity per source]* onder de tab **[!UICONTROL Configuration]** mag niet leeg zijn.

<u> Ware resultaten </u>:

*[!UICONTROL Quantity per source]* onder de tab **[!UICONTROL Configuration]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
