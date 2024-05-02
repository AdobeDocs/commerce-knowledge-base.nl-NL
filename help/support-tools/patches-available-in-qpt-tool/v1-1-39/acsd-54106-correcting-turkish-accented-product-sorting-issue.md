---
title: "ACSD-54106: Turks geaccentueerde sortering van tekens in productcategorie corrigeren"
description: Pas de ACSD-54106-patch toe om het Adobe Commerce-probleem op te lossen waarbij de sortering van categorieproducten op naam voor tekens met accent in het Turks onjuist is.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Turks geaccentueerde tekensortering corrigeren in productcategorie

De ACSD-54106-patch verhelpt het probleem waarbij de sortering van categorieproducten op naam voor tekens met accent in het Turks onjuist is. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39 is geïnstalleerd. De patch-id is ACSD-54106. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het sorteren van producten binnen categorieën op naam is onjuist voor tekens met accent in het Turks.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij het deelvenster Beheer.
1. Maak eenvoudige producten met de volgende naam en wijs deze aan elke gewenste categorie toe:

* Naam A
* Naam Rock
* Naam D
* Naam
* Naam M
* Naam Ö
* Naam Ü
* Naam Y
* Naam Z

1. Navigeer naar de winkel en open de categorie die de producten bevat.
1. De sorteervolgorde wijzigen in *[!UICONTROL By Name]*.

<u>Verwachte resultaten</u>:

De producten worden correct gesorteerd in de volgende orde:

* Naam A
* Naam Rock
* Naam D
* Naam
* Naam M
* Naam Ö
* Naam Ü
* Naam Y
* Naam Z

<u>Werkelijke resultaten</u>:

De producten worden verkeerd gesorteerd in de volgende orde:

* Naam A
* Naam D
* Naam M
* Naam Y
* Naam Z
* Naam Rock
* Naam Ö
* Naam Ü
* Naam

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
