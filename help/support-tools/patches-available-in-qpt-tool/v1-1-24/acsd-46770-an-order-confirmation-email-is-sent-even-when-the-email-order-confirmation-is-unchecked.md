---
title: '''ACSD-46770: bevestiging-e-mail voor bestelling wordt verzonden, zelfs als [!UICONTROL Email Order Confirmation] is uitgeschakeld.'
description: Pas de ACSD-46770-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mails ter bevestiging van de bestelling worden verzonden, zelfs als [!UICONTROL Email Order Confirmation] is niet geselecteerd.
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770: bevestiging-e-mail voor bestelling wordt verzonden, zelfs als **[!UICONTROL Email Order Confirmation]** is uitgeschakeld

De ACSD-46770-patch verhelpt het probleem waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als **[!UICONTROL Email Order Confirmation]** is niet geselecteerd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-46770. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een bevestigingsbericht voor bestelling wordt verzonden, zelfs als **[!UICONTROL Email Order Confirmation]** is niet geselecteerd.

<u>Stappen om te reproduceren</u>:

1. Maak een klantenaccount.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Order]** en klik op  **[!UICONTROL Create New Order]**.
1. Selecteer de klant, voeg de producten aan de bestelling toe, vul het adres in en selecteer de verzendings- en betalingsmethode.
1. Voordat u de bestelling verzendt, schakelt u de optie **[!UICONTROL Email Order confirmation]** selectievakje.
1. Klikken op **[!UICONTROL Submit Order]** om de volgorde te maken.

<u>Verwachte resultaten</u>:

Een bevestigingsbericht voor bestelling mag niet worden verzonden als de **[!UICONTROL Email Order Confirmation]** is niet geselecteerd.

<u>Werkelijke resultaten</u>:

Er wordt een bevestigingsbericht voor bestelling verzonden, ongeacht of deze is uitgeschakeld **[!UICONTROL Email Order Confirmation]** selectievakje.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
