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

De ACSD-56447-patch verhelpt het probleem dat het toevoegen van hetzelfde product aan het winkelwagentje via parallelle REST API-aanvragen leidt tot twee afzonderlijke items in het winkelwagentje. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u hetzelfde product via een parallel web REST API-verzoek aan het winkelwagentje toevoegt, resulteert dit in twee aparte items in het winkelwagentje.

<u> Stappen om </u> te reproduceren:

1. Genereer een klanttoken voor het aanvragen van de REST API-aanroepen met [!DNL Postman] .
1. Maak een winkelwagentje voor de klant.
1. Gebruik het hierboven gegenereerde token om een lege winkelwagen voor de klant te maken.
1. Gebruik CURL om twee `AddProductsToCart` -verzoeken tegelijk uit te voeren. Volg de instructies in het [ verwerkingsleerprogramma van de Orde ](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in de ontwikkelaarsdocumentatie.

<u> Verwachte resultaten </u>:

Items met meerdere hoeveelheden worden op één regel weergegeven.

<u> Ware resultaten </u>:

Dezelfde SKU&#39;s worden weergegeven in meerdere regelitems.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
