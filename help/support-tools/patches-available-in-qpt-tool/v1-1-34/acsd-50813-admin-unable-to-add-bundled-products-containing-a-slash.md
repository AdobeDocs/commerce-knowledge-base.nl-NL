---
title: "ACSD-50813: Admin unable to add bundled products containing a slash"
description: Pas de ACSD-50813-patch toe om het Adobe Commerce-prestatieprobleem op te lossen waarbij de beheerder geen gebundelde producten met een schuine streep (`/`) in de SKU kan toevoegen met de functie *Producten door SKU* toevoegen aan de beheervolgorde.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: Admin kan geen gebundelde producten met een schuine streep toevoegen

De ACSD-50813-patch verhelpt het probleem waarbij de beheerder geen gebundelde producten met een schuine streep kan toevoegen (`/`) in de SKU met de *[!UICONTROL Add Products by SKU]* functionaliteit voor de beheervolgorde. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-50813. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin kan geen gebundelde producten toevoegen die een slash-teken bevatten (`/`) in de SKU met de *[!UICONTROL Add Products by SKU]* functionaliteit voor de beheervolgorde.

<u>Stappen om te reproduceren</u>:

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Maak een eenvoudig product.
1. Maak een nieuw gebundeld product.
1. Een slash toevoegen (`/`) in het midden van de SKU (Voorbeeld: *Bu/ndle*).
1. Een gebundelde optie toevoegen met **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Wijs minstens één eenvoudig product aan de optie toe.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en maakt u een nieuwe volgorde.
1. Klikken op **[!UICONTROL Add Products by SKU]**.
1. Voer uw SKU in en klik op **[!UICONTROL Add to Order]**.
1. Open de browserconsole.
1. Klikken op **[!UICONTROL Configure]**.

<u>Verwachte resultaten</u>:

Er is geen fout.

<u>Werkelijke resultaten</u>:

JS-fout in console:

*Uncaught Error: Syntax error, unrecognized expression: div[id=sku_bu/ndle]*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
