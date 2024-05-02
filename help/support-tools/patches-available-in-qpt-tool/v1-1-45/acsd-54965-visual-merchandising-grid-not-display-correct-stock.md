---
title: '"ACSD-54965: [!UICONTROL Visual Merchandising] raster geeft de juiste voorraad niet weer'''
description: Pas de ACSD-54965-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!UICONTROL Visual Merchandising] het raster geeft niet de juiste voorraad weer wanneer een product wordt toegewezen aan aangepaste voorraad.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] raster geeft de juiste voorraad niet weer

De ACSD-54965-patch verhelpt het probleem waarbij de [!UICONTROL Visual Merchandising] het raster geeft niet de juiste voorraad weer wanneer een product wordt toegewezen aan aangepaste voorraad. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-54965. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!UICONTROL Visual Merchandising] het raster geeft niet de juiste voorraad weer wanneer een product wordt toegewezen aan aangepaste voorraad.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe bron.
1. Maak een nieuwe voorraad.
1. Twee producten maken:
   * Eén product met alleen de aangepaste voorraad.
   * Eén product met alleen de standaardvoorraad.
1. Voeg deze producten toe aan een categorie.
1. Ga naar de [!UICONTROL visual Merchandising] raster (*[!UICONTROL Products in Category]*).

<u>Werkelijke resultaten</u>:

In de *[!UICONTROL All Store Views]* het product met aangepaste voorraad geen hoeveelheid bevat. Het is alleen *[!UICONTROL Default Store View]* het toepassingsgebied is geselecteerd , de aangepaste voorraad geeft de hoeveelheid van het product aan .

<u>Verwachte resultaten</u>:

Het net toont alle voorraadinformatie als het werkingsgebied is *[!UICONTROL All Store Views]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
