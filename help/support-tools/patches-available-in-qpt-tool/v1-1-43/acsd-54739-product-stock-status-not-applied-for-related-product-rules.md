---
title: '"ACSD-54739: *[!UICONTROL Product Stock]* status niet aangevraagd voor *[!UICONTROL Related Product Rules]*'''
description: Pas de ACSD-54739-patch toe om het Adobe Commerce-probleem op te lossen waar *[!UICONTROL Product Stock]* status is niet aangevraagd voor *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: 7bc106b1-2c97-46a1-8bb6-71b99511e480
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* status niet aangevraagd *[!UICONTROL Related Product Rules]*

De ACSD-54739-patch verhelpt het probleem waarbij de *[!UICONTROL Product stock]* status wordt niet aangevraagd *[!UICONTROL Related Product Rules]*. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43 is geïnstalleerd. De patch-id is ACSD-54739. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*[!UICONTROL Product stock]* status wordt niet aangevraagd *[!UICONTROL Related Product Rules]*.

<u>Stappen om te reproduceren</u>:

1. Stel de **[!UICONTROL Display Out of Stock Products]** configuratie aan *Ja*.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** en instellen *Ja* voor de voorwaarde van de bevorderingsregel.
1. Maak de regel Verwante producten. Ga naar **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Voeg een voorwaarde met kenmerkhoeveelheid toe (selecteer in voorraad/uit voorraad).
1. Controleer de producten aan de voorzijde.

<u>Verwachte resultaten</u>:

De in-/uitslagproducten komen overeen met *[!UICONTROL Related Product Rules]*.

<u>Werkelijke resultaten</u>:

Het product uit de voorraad/uit de voorraad komt niet overeen met het *[!UICONTROL Related Product Rules]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
