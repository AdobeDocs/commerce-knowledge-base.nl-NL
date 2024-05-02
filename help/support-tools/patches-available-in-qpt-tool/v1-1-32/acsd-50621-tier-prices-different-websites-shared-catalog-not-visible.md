---
title: "ACSD-50621: Niveau-prijzen voor verschillende websites in gedeelde catalogus zijn niet zichtbaar"
description: Pas de ACSD-50621-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijzen op niveaus voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer u ze bewerkt in een omgeving met meerdere websites.
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621: Niveau-prijzen voor verschillende websites in gedeelde catalogus zijn niet zichtbaar

De ACSD-50621-patch verhelpt het probleem dat de prijzen op niveaus voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer deze worden bewerkt in een omgeving met meerdere websites. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-50621. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niveauprijzen voor verschillende websites in de gedeelde catalogus zijn niet zichtbaar wanneer u deze in een omgeving met meerdere websites bewerkt.

<u>Stappen om te reproduceren</u>:

1. Stel de **[!UICONTROL Catalog Price Scope]** tot **[!UICONTROL Website]**.
1. Maak een aanvullende website, winkel en voorvertoning.
1. Maak een eenvoudig product en wijs dit toe aan alle websites.
1. Een aangepaste gedeelde catalogus maken.
1. Ga naar **[!UICONTROL Set Pricing and Structure]** voor de aangepaste gedeelde catalogus die u hebt gemaakt.
1. In Stap 1: selecteer producten voor catalogus. Voeg het eenvoudige product toe dat u hebt gemaakt.
1. In stap 2: stel aangepaste prijzen in en klik op **[!UICONTROL Configure]**.
1. Stel verschillende laagprijzen in voor verschillende websites.
1. Selecteren **[!UICONTROL Done]** en klik op **[!UICONTROL Generate Catalog]** en klik vervolgens op **[!UICONTROL Save]**.
1. Uitsnijden uitvoeren.
1. Navigeren naar **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** en controleer de prijs op de laag.

<u>Verwachte resultaten</u>:

Alle eerder geconfigureerde laagprijzen voor verschillende websites zijn aanwezig.

<u>Werkelijke resultaten</u>:

Eerder geconfigureerde Tier-prijzen zijn niet aanwezig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
