---
title: '"ACSD-51857: Trage baan van ` aggregate_sales_report_bestsellers_data'' beïnvloedt prestaties'''
description: Pas ACSD-51857 flard toe om de kwestie van Adobe Commerce te bevestigen waar de langzame bouwbaan ` aggregate_sales_report_bestsellers_data ` grote ` verkoop_order ` en ` verkoop_order_item' gegevensbestandlijsten beïnvloedt.
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857: Trage uitsnijdtaak van `aggregate_sales_report_bestsellers_data` beïnvloedt de prestaties

De ACSD-51857-patch verhelpt het probleem waarbij de langzame snijtaak `aggregate_sales_report_bestsellers_data` beïnvloedt groot `sales_order` en `sales_order_item` databasetabellen. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34 is geïnstalleerd. De patch-id is ACSD-51857. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prestaties van snijtaken van `aggregate_sales_report_bestsellers_data` is traag `sales_order` en `sales_order_item` databasetabellen.

Om dit op te lossen, is de belangrijkste gegevensvraag die grabs gegevens voor het rapport aan een efficiëntere vorm opnieuw geschreven. Het gebruikt nu een subquery om gegevenssubset te bepalen.

Om subquery zo snel mogelijk te laten werken, is een nieuwe index toegevoegd voor de `sales_order` databasetabel: `SALES_ORDER_STORE_STATE_CREATED` gebaseerd op `store_id`, `state`, en `created_at` kolommen.

<u>Vereisten</u>

Zorg voor een groot aantal bestellingen per dag.

<u>Stappen om te reproduceren</u>

1. Voer de `aggregate_sales_report_bestsellers_data` snijtaak.
1. Controleer de gegevens die moeten worden weergegeven op het dashboard voor beheer, onder het tabblad **[!UICONTROL Bestsellers]** tab.

<u>Verwachte resultaten</u>:

*[!UICONTROL Quantity per source]* onder de **[!UICONTROL Configuration]** mag niet leeg zijn.

<u>Werkelijke resultaten</u>:

*[!UICONTROL Quantity per source]* onder de **[!UICONTROL Configuration]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
