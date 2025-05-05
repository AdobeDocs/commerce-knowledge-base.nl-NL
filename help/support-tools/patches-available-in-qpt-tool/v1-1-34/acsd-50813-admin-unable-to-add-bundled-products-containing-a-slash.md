---
title: 'ACSD-50813: Admin kan geen gebundelde producten met een schuine streep toevoegen'
description: Pas de ACSD-50813-patch toe om het Adobe Commerce-prestatieprobleem op te lossen waarbij de beheerder geen gebundelde producten met een schuine streep (&grave;/&grave;) in de SKU kan toevoegen met de functie *Producten door SKU* toevoegen aan de beheervolgorde.
exl-id: 80dfe877-9dfd-44a9-9bf0-37e929642fc0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-50813: Admin kan geen gebundelde producten met een schuine streep toevoegen

De ACSD-50813-patch verhelpt het probleem waarbij de beheerder geen gebundelde producten met een schuine streep (`/`) in de SKU kan toevoegen met de *[!UICONTROL Add Products by SKU]* -functionaliteit in de beheervolgorde. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-50813. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin kan geen gebundelde producten toevoegen die een schuine streep (`/`) in SKU met de *[!UICONTROL Add Products by SKU]* functionaliteit aan de admin orde bevatten.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Maak een eenvoudig product.
1. Maak een nieuw gebundeld product.
1. Voeg een schuine streep (`/`) in het midden van SKU (Voorbeeld: *Bu/ndle*) toe.
1. Voeg een gebundelde optie toe met **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]* .
1. Wijs minstens één eenvoudig product aan de optie toe.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en maak een nieuwe volgorde.
1. Klik op **[!UICONTROL Add Products by SKU]** .
1. Voer uw SKU in en klik op **[!UICONTROL Add to Order]** .
1. Open de browserconsole.
1. Klik op **[!UICONTROL Configure]** .

<u> Verwachte resultaten </u>:

Er is geen fout.

<u> Ware resultaten </u>:

JS-fout in console:

*Uncaught Fout: De fout van de Syntaxis, niet erkende uitdrukking: div [ id=sku_bu/ndle]*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
