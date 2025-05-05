---
title: 'ACSD-51238: de inventarisbron wordt verwijderd wanneer een configureerbaar product wordt bijgewerkt en de prijs wordt bewerkt'
description: Pas de ACSD-51238-patch toe om het Adobe Commerce-probleem op te lossen waarbij de inventarisbron wordt verwijderd tijdens het bijwerken van een configureerbaar product en het bewerken van de prijs.
exl-id: ab2f60fd-5da3-45f7-a489-6f4f9d34e1f1
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51238: de inventarisbron wordt verwijderd wanneer een configureerbaar product wordt bijgewerkt en de prijs wordt bewerkt

De ACSD-51238-patch verhelpt het probleem waarbij de inventarisbron wordt verwijderd bij het bijwerken van een configureerbaar product en het bewerken van de prijs. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51238. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventarisbron wordt verwijderd wanneer u een configureerbaar product bijwerkt en de prijs bewerkt.

<u> Stappen om </u> te reproduceren:

1. **[!DNL Adobe Commerce]** installeren met **[!DNL Inventory module]**
1. Ga naar **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** en creeer *twee bronnen* en *twee voorraden*.
1. Maak een **[!UICONTROL configurable product]** en wijs deze toe aan **[!UICONTROL default sources]** of **[!UICONTROL newly created sources]** .
1. Klik op **[!UICONTROL next button]** en *sparen* het product.
1. Bewerk nu dezelfde **[!UICONTROL Configurable Product]** en klik op **[!UICONTROL Edit Configuration]** in de **[!UICONTROL Configuration tab]** .
1. Wijzig in `Step 3: Bulk Images,Price and Quantity` de waarden `price` en `Quantity` en `Images` to `Skip quantity at this time` respectievelijk `Skip image uploading at this time` .
1. Klik op **[!UICONTROL next button]** en genereer het product.

<u> Verwachte resultaten </u>

De hoeveelheid per bron in de **[!UICONTROL Configuration tab]** mag niet leeg zijn.

<u> Ware resultaten </u>

De hoeveelheid per bron in de **[!UICONTROL Configuration tab]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL>) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.
