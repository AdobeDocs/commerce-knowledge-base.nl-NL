---
title: "ACSD-56616: Weergave van gebundelde producten bij eenvoudig voorraadtekort"
description: Pas de ACSD-56616-patch toe om het Adobe Commerce-probleem op te lossen, waarbij gebundelde producten onverwachts in de winkel verschijnen wanneer alle bijbehorende eenvoudige producten uit voorraad zijn.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: Storefront-weergave van gebundelde producten bij een eenvoudig voorraadtekort.

De ACSD-56616-patch verhelpt het probleem waarbij gebundelde producten onverwachts in de winkel verschijnen wanneer alle bijbehorende eenvoudige producten uit voorraad zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56616. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste storefront display van gebundelde producten tijdens eenvoudig voorraadtekort.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website/winkel/winkel.
1. Maak een nieuwe bron.
1. Maak een nieuwe voorraad en wijs deze toe aan de nieuwe website.
1. Configureer indexen om op schema bij te werken.
1. Genereer twee eenvoudige producten, S1 (qty = 1) en S2 (qty = 1), en wijs deze toe aan het nieuwe bestand en de nieuwe website.
1. Creeer *gebundeld1* product en associeer het met nieuwe website, plaatsend het in categorie *KAT*.
1. Bepaal twee vereiste dropdown opties en verbind eenvoudig product *S1* aan option1 en *S2* aan option2.
1. Sla de producten op.
1. Navigeer aan **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** en laat *toe toevoegt opslagcode aan URL* = *ja*.
1. Open de winkel en koop het gebundelde product.
1. Draai twee keer om.
1. Keer terug naar de *KAT* categorie.

<u> Verwachte resultaten </u>:

Het *bundle1* product is uit voorraad.

<u> Ware resultaten </u>:

Het *bundle1* product is zichtbaar met prijs = *$0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
