---
title: '''ACSD-51735: status van item bestellen is onjuist ingesteld op *[!UICONTROL Ordered]* als productvoorraad 0 is.'
description: Pas de markering ACSD-51735 toe om het Adobe Commerce-probleem op te lossen waarbij de status van het orderitem onjuist is ingesteld op * [!UICONTROL Ordered]* als de productvoorraad 0 is.
feature: Orders, Products
role: Admin
exl-id: c6376698-71dc-46b8-a5b2-86dc26a574ab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735: status van item bestellen is onjuist ingesteld op *[!UICONTROL Ordered]* als productvoorraad 0 is

De ACSD-51735-patch verhelpt het probleem waarbij de status van het orderitem onjuist is ingesteld op *[!UICONTROL Ordered]* als het productbestand 0 is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 is geïnstalleerd. De patch-id is ACSD-50895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van het orderitem wordt onjuist ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad 0 is.

<u> Eerste vereisten </u>:

* Adobe Commerce Inventory management-modules (MSI) zijn geïnstalleerd.
* Backorders zijn ingeschakeld in **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]** .

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe voorraad.
1. Maak een nieuwe bron.
1. Wijs de standaardwebsite toe aan de nieuwe voorraad en wijs de nieuwe bron toe.
1. Maak een nieuw product.

   * Stel de standaardbronhoeveelheid in op 10 en de nieuwe bronhoeveelheid op 0.

1. Voeg het product toe aan de winkelwagentje.
1. Neem de backorder waarschuwing bij kassa op, erop wijzend dat het product uit een nieuwe bron komt.
1. Plaats de bestelling.
1. Open de volgorde in Beheer en controleer de status van de backorder.

<u> Verwachte resultaten </u>:

De orde toont aan dat Aantal 1 achtergeordend is.

<u> Ware resultaten </u>:

De orde toont aan dat Aantal 1 wordt bevolen, niet backordered.

>[!MORELIKETHIS]
>
>[ De status van het item van de orde wordt verkeerd geplaatst aan *[!UICONTROL Backordered]*](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
