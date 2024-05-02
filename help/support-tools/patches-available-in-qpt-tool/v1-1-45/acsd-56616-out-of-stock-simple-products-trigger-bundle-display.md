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

De ACSD-56616-patch verhelpt het probleem waarbij gebundelde producten onverwachts in de winkel verschijnen wanneer alle bijbehorende eenvoudige producten uit voorraad zijn. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-56616. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste storefront display van gebundelde producten tijdens eenvoudig voorraadtekort.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuwe website/winkel/winkel.
1. Maak een nieuwe bron.
1. Maak een nieuwe voorraad en wijs deze toe aan de nieuwe website.
1. Configureer indexen om op schema bij te werken.
1. Genereer twee eenvoudige producten, S1 (qty = 1) en S2 (qty = 1), en wijs deze toe aan het nieuwe bestand en de nieuwe website.
1. Maken *gebundeld1* product en koppelen aan nieuwe website, plaatsen deze in categorie *CAT*.
1. Twee vereiste vervolgkeuzemogelijkheden definiëren en een eenvoudig product koppelen *S1* naar optie1 en *S2* aan optie 2.
1. Sla de producten op.
1. Navigeren naar **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** en *Winkelcode toevoegen aan URL* = *Ja*.
1. Open de winkel en koop het gebundelde product.
1. Draai twee keer om.
1. Terugkeren naar de *CAT* categorie.

<u>Verwachte resultaten</u>:

De *bundel1* het product is uit voorraad.

<u>Werkelijke resultaten</u>:

De *bundel1* product is zichtbaar met prijs = *$0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
