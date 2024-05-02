---
title: "ACSD-48910: gebundeld product met meerdere bronnen verlaat de voorraad na factuur en verzending."
description: Pas de ACSD-48910-patch toe om het Adobe Commerce-probleem op te lossen waarbij het gebundelde product dat aan meerdere bronnen is toegewezen, uit voorraad raakt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul.
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910: Gebundeld product met meerdere bronnen heeft geen voorraad na factuur en verzending

De ACSD-48910-patch verhelpt de kwestie waar het gebundelde product dat aan meerdere bronnen is toegewezen uit voorraad komt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-48910. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het gebundelde product dat aan veelvoudige bronnen wordt toegewezen gaat uit voorraad na facturering en verzending, zelfs als het nog beschikbaar is.

<u>Stappen om te reproduceren</u>:

1. Maak twee websites.
1. Maak twee weergaven voor winkels/winkels (één per website).
1. Maak twee eenvoudige producten (qty = 10) en wijs deze toe aan zowel voorraden als websites.
1. Maak een gebundeld product en voeg deze eenvoudige producten eraan toe. Wijs het gebundelde product aan beide websites toe.
1. Ga naar de winkel en voeg het gebundelde product aan de kar toe.
1. Check uit en plaats de bestelling.
1. Van Admin, factuur en verzend de orde.

<u>Verwachte resultaten</u>:

Het gebundelde product blijft in voorraad omdat we slechts 1 van de 10 artikelen hebben gekocht.

<u>Werkelijke resultaten</u>:

Het gebundelde product wijzigt zijn status in out-of-stock.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
