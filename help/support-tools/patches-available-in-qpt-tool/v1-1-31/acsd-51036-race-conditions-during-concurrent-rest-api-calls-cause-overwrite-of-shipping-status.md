---
title: 'ACSD-51036: Ongelijke omstandigheden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijvingen van de verzendstatus'
description: Pas de ACSD-51036-patch toe om het Adobe Commerce-probleem op te lossen waarbij er rasvoorwaarden zijn tijdens gelijktijdige REST API-aanroepen die leiden tot het overschrijven van de verzendstatus in de tabel met items die zijn besteld.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: De omstandigheden van de ruimte tijdens gelijktijdige vraag REST API resulteren in een overschrijving van de verzendstatus in de punten bevolen lijst

De ACSD-51036-patch verhelpt het probleem waarbij de rasomstandigheden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijving van de verzendstatus in de geordende tabel. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.31 is geïnstalleerd. De patch-id is ACSD-51036. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De rassenvoorwaarden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijving van de verzendstatus in de items die zijn geordend in de tabel.

<u>Stappen om te reproduceren</u>:

1. Maak een bestelling met twee items.
1. Factuurpost A.
1. Verzend tegelijkertijd een aanvraag voor terugbetaling voor object A via REST API terwijl u een aanvraag voor het object B verzendt.
1. Ga naar de volgorde in **[!UICONTROL Admin Panel]**.

<u>Verwachte resultaten</u>

*[!UICONTROL Shipped 1]* status moet aanwezig zijn voor item B in de *[!UICONTROL Items]* geordende tabel.

<u>Werkelijke resultaten</u>

*[!UICONTROL Shipped 1]* status is niet aanwezig voor item B in het gedeelte *[!UICONTROL Items]* geordende tabel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
