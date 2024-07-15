---
title: "ACSD-51204: Het product keert na het aanmaken van de kredietmemo niet terug in voorraad."
description: Pas de ACSD-51204-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product na het maken van de creditmemo niet opnieuw in voorraad wordt genomen.
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: Het product retourneert na het aanmaken van de kredietmemo niet meer in voorraad

De ACSD-51204-patch verhelpt het probleem waarbij het product na het maken van de creditmemo niet opnieuw in voorraad terugkeert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51204. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitgekozen product keert niet terug in voorraad na het aanmaken van de kredietmemo.

<u> Stappen om </u> te reproduceren:

1. Installeer **[!UICONTROL Adobe Commerce]** en laat **[!UICONTROL Inventory Management Module]** met standaard *bron* en *voorraad* slechts toe.
1. Voeg a **[!UICONTROL new product]** met een hoeveelheid *10* toe.
1. Wijs het product toe aan de **[!UICONTROL default stock]** .
1. Voeg het product in de winkel toe aan de kar en plaats een bestelling voor een totale beschikbare hoeveelheid van 10.
1. In het admin paneel, produceer een *factuur* en *lading* voor de orde.
1. Creeer a **[!UICONTROL Credit Memo]** met de *terugkeer aan voorraad* checkbox die voor alle punten wordt geselecteerd.
1. Controleer de **[!UICONTROL Salable Quantity]** van het product in Admin.

<u> Verwachte resultaten </u>:

De verkoopbare hoeveelheid van het product moet aan *10* terugkeren.

<u> Ware resultaten </u>:

De verkoopbare hoeveelheid van het product wordt verlaten als *0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
