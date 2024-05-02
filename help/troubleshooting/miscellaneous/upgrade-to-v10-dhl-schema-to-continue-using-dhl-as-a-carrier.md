---
title: Upgrade naar v10 DHL-schema om DHL-verzending te blijven aanbieden
description: Dit artikel verstrekt een oplossing om handelaars toe te staan om DHL te blijven aanbieden verschepen nadat DHL schema 6.2 in December 2022 wordt afgekeurd, door aan schema 10.0 te bevorderen of door AC-3023 flard toe te passen.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Upgrade naar versie 10.0 DHL-schema om DHL-verzending te blijven aanbieden

Dit artikel biedt een oplossing waarmee handelaren DHL-scheepvaart kunnen blijven aanbieden nadat versie 6.2 van het DHL-schema eind december 2022 is afgekeurd.

## Betrokken producten en versies

* Adobe Commerce 2.4.5 en eerdere versies, alle implementatiemethoden.

## Probleem

In augustus 2022 hebben we de [upgrade van DHL-schema versie 6.2. samen met een patch voor repareren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) voor handelaren om DHL-scheepvaart te blijven aanbieden. DHL introduceert in oktober 2022 opnieuw een nieuw schema - versie 10.0 - en de vorige versie (6.2-schema) zal eind december 2022 verouderd zijn. Adobe Commerce 2.4.5 en eerdere DHL-integratie ondersteunen alleen versie 6.2.

## Oplossing

Adobe Commerce 2.4.5-p1 en 2.4.4-p2, die in oktober 2022 zijn uitgebracht, bevatten de nieuwe DHL-schemaversie 10.0. Handelaren die upgraden naar 2.4.5-p1 en 2.4.4-p2 hoeven dus niets te doen om de DHL-verzendingen te blijven aanbieden. Wij moedigen alle handelaren aan om aan 2.4.5-p1 en 2.4.4-p2 vóór de afschrijving van DHL schema 6.2. eind december 2022 te bevorderen.

Handelaren die niet willen upgraden naar 2.4.5-p1 en 2.4.4-p2, moeten een reparatiefragment toepassen als ze na december 2022 DHL-verzending willen blijven aanbieden.

## Reparatie

De patch-id is AC-3023 en is beschikbaar in de [!DNL Quality Patches Tool] versie 1.1.21.

Verwijs de volgende verbindingen op hoe te om te gebruiken [!DNL Quality Patches Tool] en installeer patches afhankelijk van uw implementatiemethoden:

* Adobe Commerce op locatie en Magento Open Source: [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in Adobe Experience League.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

**De patch is van toepassing op de volgende Adobe Commerce-versies (alle implementatiemethoden):**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Nuttige koppelingen

* [[!DNL Quality Patches Tool] > Opmerkingen bij de release](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) in Adobe Experience League.

* [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in Adobe Experience League.

## Gerelateerde lezing

* [Pas een patch toe om DHL als scheepvaartmaatschappij te blijven aanbieden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) in onze kennisbasis voor ondersteuning.

* [Shipping Carriers > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) in onze gebruikershandleiding.
* [Configuration Reference > Sales > Delivery Methods](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) in onze gebruikershandleiding.
