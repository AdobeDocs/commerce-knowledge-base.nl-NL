---
title: Adobe Commerce-statuskolom ontbrekende geëxporteerde producten CSV-bestand
description: Dit artikel biedt een oplossing voor het probleem wanneer u de statuskolom niet kunt vinden in het CSV-bestand dat geëxporteerde producten bevat.
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce-statuskolom ontbrekende geëxporteerde producten CSV-bestand

Dit artikel biedt een oplossing voor het probleem wanneer u de statuskolom niet kunt vinden (d.w.z. of het product is in- of uitgeschakeld) in het CSV-bestand dat geëxporteerde producten bevat. De status van het product wordt aangegeven door de [!UICONTROL product_online] kolom.

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) alle [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Probleem

U kunt de map [!UICONTROL status] in het CSV-bestand dat geëxporteerde producten bevat. Zo, bijvoorbeeld, voert u een CSV van alle SKUs, met hun status uit, maar de lijst schijnt te ontbreken [!UICONTROL status] kolom.

<u>Stappen om te reproduceren:</u>

1. Selecteer in Adobe Commerce Admin de optie **[!UICONTROL System]**, onder **[!UICONTROL Data Transfer]** selecteren **[!UICONTROL Export]**.
1. In de **[!UICONTROL Export Settings]** in de sectie **[!UICONTROL Entity Type]** vervolgkeuzelijst **[!UICONTROL Products]**.
1. Zoeken naar **[!UICONTROL status]**, vermeld onder **[!UICONTROL Attribute Code]**. Deze kenmerkcode wordt weergegeven in de lijst met beschikbare kenmerken (**[!UICONTROL Enable Product]**).
1. Klikken op **[!UICONTROL Export]**.

<u>Verwacht resultaat:</u>

In het CSV-bestand dat u net hebt geëxporteerd, ziet u een kolom met het label [!UICONTROL status].

<u>Werkelijk resultaat:</u>

Er wordt geen kolom met het label weergegeven [!UICONTROL status] in het geëxporteerde CSV-bestand.

## Oorzaak

De naam van het statuskenmerk van het product is gewijzigd in het CSV-bestand. Het is nu [!UICONTROL product_online] kolom.

## Oplossing

1. Selecteren **[!UICONTROL System]**, onder **[!UICONTROL Data Transfer]** selecteren **[!UICONTROL Import]**.
1. Klik op **[!UICONTROL Download Sample File]**.
1. U kunt de [!UICONTROL product_online] in het CSV-bestand.

## Gerelateerde lezing

* [Werken met CSV-bestanden](https://docs.magento.com/user-guide/system/data-csv.html) in onze gebruikershandleiding.
* [Referentie productkenmerken exporteren](https://docs.magento.com/user-guide/system/data-attributes-product.html) in onze gebruikershandleiding.
