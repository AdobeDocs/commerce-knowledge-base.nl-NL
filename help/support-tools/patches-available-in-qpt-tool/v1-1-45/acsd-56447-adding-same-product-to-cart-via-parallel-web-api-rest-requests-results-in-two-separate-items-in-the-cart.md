---
title: 'ACSD-56447: Toevoegen van hetzelfde product aan het winkelwagentje via parallelle web REST API resulteert in twee aparte artikelen in het winkelwagentje.'
description: Pas de ACSD-56447-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het toevoegen van hetzelfde product aan de winkelwagentje via parallel REST API-aanvragen resulteert in twee aparte items in de winkelwagentje.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: c63874be-a8a6-4143-adaa-ba3e9e107dd4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-56447: Als hetzelfde product via parallelle web REST API aan het winkelwagentje wordt toegevoegd, ontstaan er twee aparte items in het winkelwagentje

De ACSD-56447-patch verhelpt het probleem dat het toevoegen van hetzelfde product aan het winkelwagentje via parallelle REST API-aanvragen leidt tot twee afzonderlijke items in het winkelwagentje. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-56447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u hetzelfde product via een parallel web REST API-verzoek aan het winkelwagentje toevoegt, resulteert dit in twee aparte items in het winkelwagentje.

<u>Stappen om te reproduceren</u>:

1. Een klanttoken genereren voor het aanvragen van REST API-aanroepen met behulp van [!DNL Postman].
1. Maak een winkelwagentje voor de klant.
1. Gebruik het hierboven gegenereerde token om een lege winkelwagen voor de klant te maken.
1. CURL gebruiken om twee te maken `AddProductsToCart` aanvragen die parallel lopen. Volg de instructies in de [Zelfstudie voor het verwerken van bestellingen](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in de ontwikkelaarsdocumentatie.

<u>Verwachte resultaten</u>:

Items met meerdere hoeveelheden worden op één regel weergegeven.

<u>Werkelijke resultaten</u>:

Dezelfde SKU&#39;s worden weergegeven in meerdere regelitems.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
