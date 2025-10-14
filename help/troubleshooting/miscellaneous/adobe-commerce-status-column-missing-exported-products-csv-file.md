---
title: Adobe Commerce-statuskolom ontbrekende geëxporteerde producten CSV-bestand
description: Dit artikel biedt een oplossing voor het probleem wanneer u de statuskolom niet kunt vinden in het CSV-bestand dat geëxporteerde producten bevat.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce-statuskolom ontbrekende geëxporteerde producten CSV-bestand

Dit artikel biedt een oplossing voor het probleem wanneer u de statuskolom niet kunt vinden (d.w.z. of het product is in- of uitgeschakeld) in het CSV-bestand dat geëxporteerde producten bevat. De status van het product wordt aangegeven met de kolom [!UICONTROL product_online] .

## Betrokken producten en versies

Adobe Commerce (alle plaatsingsmethodes) alle [&#x200B; gesteunde versies &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

U kunt de kolom [!UICONTROL status] niet vinden in het CSV-bestand dat geëxporteerde producten bevat. U exporteert bijvoorbeeld een CSV van alle SKU&#39;s met hun status, maar de kolom [!UICONTROL status] lijkt in de tabel te ontbreken.

<u> Stappen om te reproduceren:</u>

1. Selecteer in Adobe Commerce Admin de optie **[!UICONTROL System]** onder **[!UICONTROL Data Transfer]** select **[!UICONTROL Export]** .
1. Selecteer in de sectie **[!UICONTROL Export Settings]** in de vervolgkeuzelijst **[!UICONTROL Entity Type]** **[!UICONTROL Products]** .
1. Zoeken naar **[!UICONTROL status]** , weergegeven onder **[!UICONTROL Attribute Code]** . U ziet dat attributencode in de lijst van beschikbare attributen (**[!UICONTROL Enable Product]**).
1. Klik op **[!UICONTROL Export]** .

<u> Verwacht resultaat:</u>

In het CSV-bestand dat u net hebt geëxporteerd, ziet u een kolom met het label [!UICONTROL status] .

<u> Ware resultaat:</u>

Er wordt geen kolom met het label [!UICONTROL status] weergegeven in het geëxporteerde CSV-bestand.

## Oorzaak

De naam van het statuskenmerk van het product is gewijzigd in het CSV-bestand. Het is nu de kolom [!UICONTROL product_online] .

## Oplossing

1. Selecteer **[!UICONTROL System]** onder **[!UICONTROL Data Transfer]** Selecteren **[!UICONTROL Import]** .
1. Klik op **[!UICONTROL Download Sample File]**.
1. U kunt de kolom [!UICONTROL product_online] in het CSV-bestand zien.

## Gerelateerde lezing

* [&#x200B; Werkend met Csv- dossiers &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-csv) in onze gebruikersgids.
* [&#x200B; Verwijzing van de Attributen van de Uitvoer van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-attributes-product) in onze gebruikersgids.
