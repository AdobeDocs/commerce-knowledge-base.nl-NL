---
title: '"ACSD-56790: **[!UICONTROL move out of stock to bottom]** werkt niet tijdens het sorteren van producten in de  [!DNL Visual Merchandiser]'''
description: Pas de ACSD-56790-patch toe om het Adobe Commerce-probleem op te lossen waarbij de optie 'van voorraad naar onderkant' niet werkt tijdens het sorteren van producten in Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** werkt niet tijdens het sorteren van producten in het dialoogvenster [!DNL Visual Merchandiser]

De ACSD-56790-patch verhelpt het probleem dat de optie om van voorraad naar onderkant te gaan niet werkt bij het sorteren van producten in het dialoogvenster [!DNL Visual Merchandiser]. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44 is geïnstalleerd. De patch-id is ACSD-56790. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL move out of stock to bottom]** werkt niet tijdens het sorteren van producten in het dialoogvenster [!DNL Visual Merchandiser]

<u>Stappen om te reproduceren</u>:

1. Adobe Commerce installeren.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en maak de volgende kenmerken.
1. Een nieuwe website maken: **Niet-hoofdmap**.
1. Een **Niet-hoofdwinkel** op deze nieuwe website.
1. Twee winkels maken:

   * Eerste in het dialoogvenster **Hoofdwebsitearchief**.
   * Tweede in de **Niet-hoofdwinkel**.

1. Maak twee bronnen:
   * Letters.
   * Getallen.

1. Twee bestanden maken:
   * Eerste hoofdkanaal - verkoopkanalen: hoofdwebsite - toegewezen bronnen: letters.
   * Tweede niet-hoofdproduct - verkoopkanalen: niet-hoofdbronnen - toegewezen bronnen: getallen.

1. Maak drie eenvoudige producten op beide websites, allemaal in de categorie Standaard, die allemaal zijn toegewezen aan beide bronnen:

   * ProductA - Aantal *10* in letters, hoeveelheid *0* in getallen.
   * Product1 - Aantal *0* in letters, hoeveelheid *10* in getallen.
   * ProductA1 - Aantal *10* in letters, hoeveelheid *10* in getallen.

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en selecteert u  **[!UICONTROL Default category]**.
1. Het bereik wijzigen in **Eerste**.
1. Vouw de producten uit in de sectie Categorie.
1. Kies de sorteervolgorde als: **[!UICONTROL move out of stock to bottom]**

<u>Verwachte resultaten</u>:

De lijst van de producten met de **uit voorraad** producten worden naar de onderkant verplaatst.

<u>Werkelijke resultaten</u>:

De producten kunnen niet worden geladen. Een pagina wordt omgeleid naar het dashboard voor beheer met het foutbericht: `Invalid security or form key. Please refresh the page`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
