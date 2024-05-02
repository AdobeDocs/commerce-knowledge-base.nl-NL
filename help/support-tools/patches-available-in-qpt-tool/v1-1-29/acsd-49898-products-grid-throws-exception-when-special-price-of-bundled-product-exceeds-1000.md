---
title: 'ACSD-49898: Het raster Producten genereert een uitzondering'
description: Pas de ACSD-49898-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het productraster een uitzondering genereert wanneer een gebundeld product een speciale prijs heeft die hoger is dan 1000.
exl-id: 16a0ec90-7577-46ef-aeb3-a7e9658cf64b
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-49898: Het raster van producten werpt een uitzondering

De ACSD-49898-patch verhelpt het probleem waarbij het productraster een uitzondering genereert wanneer een gebundeld product een speciale prijs heeft die hoger is dan 1000. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 is geïnstalleerd. De patch-id is ACSD-49898. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het raster van producten werpt een uitzondering wanneer een gebundeld product een speciale prijs heeft die 1000 overschrijdt. Het probleem heeft te maken met het gebruik van komma&#39;s in plaats van punten voor decimale getallen in bepaalde landinstellingen.

<u>Stappen om te reproduceren</u>:

1. Maak een gebundeld product.
1. Stel de speciale prijs in op 9999; opslaan en sluiten.
1. Navigeren naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Zoek naar gebundelde product SKU als het niet zichtbaar is.

<u>Verwachte resultaten</u>:

* De gebruiker kan het gebundelde product met de speciale prijs filteren/zien.
* De speciale prijs wordt weergegeven als een percentage voor gebundelde producten en als prijs voor andere productsoorten.

<u>Werkelijke resultaten</u>:

De volgende fout wordt gegenereerd: *Niet-numerieke waarde aangetroffen*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
