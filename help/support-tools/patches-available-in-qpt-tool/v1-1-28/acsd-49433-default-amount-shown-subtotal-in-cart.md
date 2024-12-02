---
title: 'ACSD-49433: Standaardbedrag weergegeven als subtotaal in winkelwagentje voor cadeaukaart"'
description: Pas de ACSD-49433-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het standaardbedrag als subtotaal wordt weergegeven in het winkelwagentje voor cadeaukaart met een open bedrag.
exl-id: e2a887bb-c15a-43a6-a145-b295deef399b
feature: Admin Workspace, Gift, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-49433: Standaardbedrag weergegeven als subtotaal in karretje voor cadeaukaart

De ACSD-49433-patch verhelpt het probleem waarbij het standaardbedrag als subtotaal in het winkelwagentje voor de cadeaukaart met een open bedrag wordt weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49433. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardbedrag wordt weergegeven als subtotaal in het winkelwagentje voor de cadeaukaart met een open bedrag.

<u> Stappen om </u> te reproduceren:

1. Maak een cadeaukaart.
1. Zorg ervoor dat het open bedrag is ingesteld op *[!UICONTROL Yes]* (tussen 50 en 500 €).
1. Ga naar het [!UICONTROL Gift Card] -product in de winkel en kies een andere hoeveelheid in de vervolgkeuzelijst.
1. Geef $100 op in het bedrag in USD.
1. Vul andere velden in en voeg deze toe aan het winkelwagentje.
1. Ga naar de miniwinkelwagentje of de winkelwagentje pagina.

<u> Verwachte resultaten </u>:

Het subtotaal toont het bedrag de gebruiker inging.

<u> Ware resultaten </u>:

Het subtotaal toont het standaardbedrag van de cadeau-kaart.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
