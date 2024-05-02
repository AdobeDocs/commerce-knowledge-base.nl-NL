---
title: "ACSD-48293: samengestelde producten uit voorraad bij de verkoop van in voorraad zijnde kinderproducten"
description: Pas de ACSD-48293-patch toe om het Adobe Commerce-probleem op te lossen waarbij de samengestelde producten uit voorraad verdwijnen wanneer de verkochte onderliggende producten naar voorraad worden teruggestuurd.
exl-id: 74ca34fe-e015-4daf-a608-4756c8ab3558
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48293: samengestelde producten uit voorraad bij de verkoop van in voorraad zijnde kinderproducten

De ACSD-48293-patch verhelpt het probleem waar de samengestelde producten uit voorraad verdwijnen wanneer de uitverkochte kinderproducten naar voorraad worden teruggestuurd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48293. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Samengestelde producten gaan uit voorraad wanneer de uitgekozen kinderproducten naar voorraad worden teruggebracht.

<u>Stappen om te reproduceren</u>:

1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Maak twee bronnen en voorraden en wijs deze toe aan elke website.
1. De optie voor producten uit de voorraad weergeven inschakelen onder **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Maak een configureerbaar product met één gekoppeld product met behulp van de voorraadbron van de primaire website (set qty = 1).
1. Plaats een orde voor het configureerbare product.
1. Voer de uitsnede uit.
1. Open het configureerbare product vanuit de winkel en bevestig dat het uit voorraad is.
1. Open het configureerbare product vanuit de [!UICONTROL Admin] en stelt de **[!UICONTROL Manage Stock Option]** tot *[!UICONTROL No]*.
1. Voer de uitsnede uit.
1. Verplaats de bestelling en voeg hoeveelheid toe aan het eenvoudige product dat de bestelling in voorraad maakt.
1. Voer de uitsnede uit.
1. Controleer de beschikbaarheid van het product op de winkel.

<u>Verwachte resultaten</u>:

Het configureerbare product is in voorraad.

<u>Werkelijke resultaten</u>:

Het configureerbare product is uit voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
