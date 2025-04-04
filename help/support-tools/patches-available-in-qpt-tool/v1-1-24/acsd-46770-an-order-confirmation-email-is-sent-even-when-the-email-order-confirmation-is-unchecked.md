---
title: 'ACSD-46770: bevestiging-e-mail voor bestelling wordt verzonden, zelfs als [!UICONTROL Email Order Confirmation] niet is ingeschakeld'
description: Pas de ACSD-46770-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mails ter bevestiging van de bestelling worden verzonden, zelfs als [!UICONTROL Email Order Confirmation] niet is geselecteerd.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: bevestiging-e-mail voor bestelling wordt verzonden, zelfs als **[!UICONTROL Email Order Confirmation]** niet is ingeschakeld

De ACSD-46770-patch verhelpt het probleem waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als **[!UICONTROL Email Order Confirmation]** niet is geselecteerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46770. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een bevestigingsbericht voor bestelling verzonden, zelfs als **[!UICONTROL Email Order Confirmation]** niet is geselecteerd.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Order]** en klik op **[!UICONTROL Create New Order]** .
1. Selecteer de klant, voeg de producten aan de bestelling toe, vul het adres in en selecteer de verzendings- en betalingsmethode.
1. Schakel het selectievakje **[!UICONTROL Email Order confirmation]** uit voordat u de volgorde verzendt.
1. Klik op **[!UICONTROL Submit Order]** om de volgorde te maken.

<u> Verwachte resultaten </u>:

Er moet geen bevestigingsbericht voor bestelling worden verzonden als de optie **[!UICONTROL Email Order Confirmation]** niet is geselecteerd.

<u> Ware resultaten </u>:

Er wordt een bevestigingsbericht voor bestelling verzonden, ongeacht het selectievakje **[!UICONTROL Email Order Confirmation]** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
