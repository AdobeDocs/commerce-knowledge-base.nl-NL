---
title: 'ACSD-54264: Fout wanneer klant probeert uit te checken met een verhandelbaar prijsopgave.'
description: Pas de ACSD-54264-patch toe om het Adobe Commerce-probleem op te lossen waarbij het foutbericht "U kunt het gevraagde kenmerk niet bijwerken. Rij-id:store_id" wordt weergegeven wanneer een klant een aanhalingsteken in een andere winkelweergave wil uitchecken met een verhandelbaar aanhalingsteken.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: Fout verschijnt wanneer de klant probeert uit te checken met verhandelbare aanhalingstekens

De ACSD-54264-patch verhelpt het probleem waarbij een foutbericht verschijnt *U kunt het gevraagde kenmerk niet bijwerken. Rij-id: store_id* verschijnt wanneer een klant probeert uit te checken met een verhandelbaar aanhalingsteken in een andere winkelweergave. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-54264. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutbericht *U kunt het gevraagde kenmerk niet bijwerken. Rij-id: store_id* verschijnt wanneer een klant probeert uit te checken met een verhandelbaar aanhalingsteken in een andere winkelweergave.

<u>Vereisten</u>:

Adobe Commerce B2B-modules worden geïnstalleerd en ingeschakeld.

<u>Stappen om te reproduceren</u>:

1. Maak een extra winkelweergave voor de standaardwebsite.
1. De optie *[!UICONTROL B2B Quote]* in de configuratie.
1. Meld u aan als klant van een bedrijf in een van de winkelweergaven.
1. Een product toevoegen aan de *[!UICONTROL Shopping Cart]*.
1. Het aanhalingsteken ter controle verzenden.
1. Ga als beheerder naar **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** en dient het goedgekeurde citaat in.
1. Als bedrijfklant, verander de opslagmening in een verschillende archiefmening.
1. Probeer uit te checken.

<u>Verwachte resultaten</u>:

De klant plaatst een bestelling met dit citaat.

<u>Werkelijke resultaten</u>:

* De fout treedt op bij het opslaan van de verzendgegevens:

  `You cannot update the request attribute. Row ID: store_id =#`

* De volgende fout wordt geregistreerd:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
