---
title: "ACSD-49628: [!DNL Page Builder] CORS-fouten verhinderen dat product wordt opgeslagen"
description: Pas de ACSD-49628-patch toe om het Adobe Commerce-probleem op te lossen waarbij de [!DNL Page Builder] Met CORS-fouten kunnen producten niet worden opgeslagen.
exl-id: c6e2f0b3-aea0-4caf-8b69-9644b38c909c
feature: Categories, Page Builder, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] Met CORS-fouten worden producten niet opgeslagen

De ACSD-49628-patch verhelpt het probleem waarbij: [!DNL Page Builder] Door CORS-fouten kan een beheerder een product niet opslaan. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.32 is geïnstalleerd. De patch-id is ACSD-49628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Page Builder] CORS-fouten verhinderen het opslaan van een product.

<u>Stappen om te reproduceren</u>:

1. Meld u aan als beheerder.
1. Maak een gebruikersrol met de volgende machtigingen:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Geen *[!UICONTROL Content]* machtigingen.
1. Maak nog een beheerder en wijs de rollen die hierboven zijn gemaakt toe aan deze gebruiker.
1. Maak een product en meld u af.
1. Meld u aan als tweede beheerder.
1. Probeer het product te bewerken en op te slaan.

<u>Verwachte resultaten</u>:

De tweede beheerder kan het product opslaan, maar de **[!UICONTROL Edit with Page Builder]** de knop wordt zonder *[!UICONTROL Content]* machtigingen.

<u>Werkelijke resultaten</u>:

De tweede beheerder kan het product niet opslaan vanwege meerdere [!DNL Page Builder] fouten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
