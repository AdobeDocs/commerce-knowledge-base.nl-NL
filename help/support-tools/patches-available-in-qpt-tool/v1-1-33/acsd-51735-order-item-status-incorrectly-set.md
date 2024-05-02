---
title: '''ACSD-51735: status van orderitem onjuist ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is.'
description: Pas de ACSD-51735-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van het orderitem onjuist is ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: status van orderitem onjuist ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is

De ACSD-51735-patch verhelpt het probleem waarbij de status van het orderitem onjuist is ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van een orderitem is onjuist ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is.

<u>Vereisten</u>:

* Adobe Commerce Inventory management-modules (MSI) zijn geïnstalleerd.
* Backorders zijn ingeschakeld in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe voorraad.
1. Maak een nieuwe bron.
1. Wijs de standaardwebsite toe aan de nieuwe voorraad en wijs de nieuwe bron toe.
1. Maak een nieuw product.

   * Stel de standaardbronhoeveelheid in op 10 en de nieuwe bronhoeveelheid op 0.

1. Voeg het product toe aan de winkelwagentje.
1. Neem de backorder waarschuwing bij kassa op, erop wijzend dat het product uit een nieuwe bron komt.
1. Plaats de bestelling.
1. Open de volgorde in Beheer en controleer de status van de backorder.

<u>Verwachte resultaten</u>:

De orde toont aan dat Aantal 1 achtergeordend is.

<u>Werkelijke resultaten</u>:

De orde toont aan dat Aantal 1 wordt bevolen, niet backordered.

>[!MORELIKETHIS]
>
>[De status van een orderitem is onjuist ingesteld op *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
