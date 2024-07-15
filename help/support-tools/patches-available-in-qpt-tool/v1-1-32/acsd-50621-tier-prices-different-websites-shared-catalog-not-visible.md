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

De ACSD-50621-patch verhelpt het probleem dat de prijzen op niveaus voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer deze worden bewerkt in een omgeving met meerdere websites. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-50621. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niveauprijzen voor verschillende websites in de gedeelde catalogus zijn niet zichtbaar wanneer u deze in een omgeving met meerdere websites bewerkt.

<u> Stappen om </u> te reproduceren:

1. Stel de waarde **[!UICONTROL Catalog Price Scope]** in op **[!UICONTROL Website]** .
1. Maak een aanvullende website, winkel en voorvertoning.
1. Maak een eenvoudig product en wijs dit toe aan alle websites.
1. Een aangepaste gedeelde catalogus maken.
1. Ga naar **[!UICONTROL Set Pricing and Structure]** voor de aangepaste gedeelde catalogus die u hebt gemaakt.
1. In Stap 1: selecteer producten voor catalogus. Voeg het eenvoudige product toe dat u hebt gemaakt.
1. In stap 2: stel aangepaste prijzen in en klik op **[!UICONTROL Configure]** .
1. Stel verschillende laagprijzen in voor verschillende websites.
1. Selecteer **[!UICONTROL Done]** en klik op **[!UICONTROL Generate Catalog]** en klik vervolgens op **[!UICONTROL Save]** .
1. Uitsnijden uitvoeren.
1. Navigeer naar **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** en controleer de laagprijs.

<u> Verwachte resultaten </u>:

Alle eerder geconfigureerde laagprijzen voor verschillende websites zijn aanwezig.

<u> Ware resultaten </u>:

Eerder geconfigureerde Tier-prijzen zijn niet aanwezig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
