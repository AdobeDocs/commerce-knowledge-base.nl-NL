---
title: 'ACSD-45675: Bij het exporteren van producten worden categorienamen gebruikt van het standaardweergavebereik van de winkel.'
description: De ACSD-45675-patch verhelpt het probleem waarbij het exportproduct categorienamen uit het standaardweergavebereik van de winkel gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-45675. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675: Bij het exporteren van producten worden categorienamen gebruikt van het standaardweergavebereik van de winkel

De ACSD-45675-patch verhelpt het probleem waarbij het exportproduct categorienamen uit het standaardweergavebereik van de winkel gebruikt. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 is geïnstalleerd. De patch-id is ACSD-45675. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij exporteren van product worden categorienamen uit het standaardweergavebereik van de winkel gebruikt.

<u>Stappen om te reproduceren</u>:

1. Een aangepaste winkelweergave maken **[!UICONTROL Thai]** in de hoofdwinkel.
1. Merk **[!UICONTROL Thai]** de standaardwinkelweergave van de hoofdwebsite.
1. De volgende categoriestructuur maken onder **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Selecteer de categorie **[!UICONTROL Tea]** en wijzigt u **[!UICONTROL Scope]** tot **[!UICONTROL Thai]**.
1. Stel de **[!UICONTROL Category Name]** als **[!UICONTROL ชาดำ]**.
1. Een eenvoudig product maken **[!UICONTROL SP001]** en de categorie toewijzen **[!UICONTROL Black]**.
1. Controleer of de uitsnede niet wordt uitgevoerd.
1. Een product exporteren. Filteren op SKU en selecteren **[!UICONTROL SP001]**.
1. Controleer de **[!UICONTROL categories]** in de geëxporteerde CSV.

<u>Verwachte resultaten</u>:

Aangezien er tijdens het exporteren geen winkel is geselecteerd, kunt u het beste een categoriepad als het volgende ophalen: *[!UICONTROL Default Category/Tea/Black]*.

<u>Werkelijke resultaten</u>:

Categoriepad heeft gemengde talen: *[!UICONTROL Default Category/ชาดำ/Black]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tools] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in [!DNL QPT], zie [Patches beschikbaar in [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de handleiding voor het gereedschap Kwaliteitspatches.
