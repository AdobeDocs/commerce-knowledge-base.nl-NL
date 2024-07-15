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

De ACSD-48293-patch verhelpt het probleem waar de samengestelde producten uit voorraad verdwijnen wanneer de uitverkochte kinderproducten naar voorraad worden teruggestuurd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48293. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Samengestelde producten gaan uit voorraad wanneer de uitgekozen kinderproducten naar voorraad worden teruggebracht.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Maak twee bronnen en voorraden en wijs deze toe aan elke website.
1. Schakel de optie voor het weergeven van producten buiten de voorraad in onder **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]* .
1. Maak een configureerbaar product met één gekoppeld product met behulp van de voorraadbron van de primaire website (set qty = 1).
1. Plaats een orde voor het configureerbare product.
1. Voer de uitsnede uit.
1. Open het configureerbare product vanuit de winkel en bevestig dat het uit voorraad is.
1. Open het configureerbare product vanuit de [!UICONTROL Admin] en stel de **[!UICONTROL Manage Stock Option]** in op *[!UICONTROL No]* .
1. Voer de uitsnede uit.
1. Verplaats de bestelling en voeg hoeveelheid toe aan het eenvoudige product dat de bestelling in voorraad maakt.
1. Voer de uitsnede uit.
1. Controleer de beschikbaarheid van het product op de winkel.

<u> Verwachte resultaten </u>:

Het configureerbare product is in voorraad.

<u> Ware resultaten </u>:

Het configureerbare product is uit voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
