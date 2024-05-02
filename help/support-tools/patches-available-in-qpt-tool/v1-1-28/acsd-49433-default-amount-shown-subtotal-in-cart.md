---
title: "ACSD-49433: Standaardbedrag weergegeven als subtotaal in winkelwagentje voor cadeaukaart"
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

De ACSD-49433-patch verhelpt het probleem waarbij het standaardbedrag als subtotaal in het winkelwagentje voor de cadeaukaart met een open bedrag wordt weergegeven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28 is geïnstalleerd. De patch-id is ACSD-49433. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardbedrag wordt weergegeven als subtotaal in het winkelwagentje voor de cadeaukaart met een open bedrag.

<u>Stappen om te reproduceren</u>:

1. Maak een cadeaukaart.
1. Zorg ervoor dat de hoeveelheid is ingesteld op *[!UICONTROL Yes]* (tussen 50 en 500 dollar).
1. Ga naar de [!UICONTROL Gift Card] in de winkel en kies een ander bedrag uit de vervolgkeuzelijst.
1. Geef $100 op in het bedrag in USD.
1. Vul andere velden in en voeg deze toe aan het winkelwagentje.
1. Ga naar de miniwinkelwagentje of de winkelwagentje pagina.

<u>Verwachte resultaten</u>:

Het subtotaal toont het bedrag de gebruiker inging.

<u>Werkelijke resultaten</u>:

Het subtotaal toont het standaardbedrag van de cadeau-kaart.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
