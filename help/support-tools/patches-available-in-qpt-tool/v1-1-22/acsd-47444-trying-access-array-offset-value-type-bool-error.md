---
title: '"ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ fout bij het openen van bepaalde niet bestaande categoriepaden voor bekende producten op PHP 7.4'''
description: Pas de ACSD-47444-patch toe om het Adobe Commerce-probleem op te lossen als er een _ is[!UICONTROL Trying to access array offset on value of type bool]_ fout bij het openen van bepaalde niet bestaande categoriepaden voor bekende producten, op PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-4744: _[!UICONTROL Trying to access array offset on value of type bool]_Fout bij het openen van bepaalde niet-bestaande categoriepaden voor bekende producten op PHP 7.4

De ACSD-47444-patch lost het probleem op waar u ziet _[!UICONTROL Trying to access array offset on value of type bool]_fout bij het openen van bepaalde niet bestaande categoriepaden voor bekende producten op PHP 7.4. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met Adobe Commerce-versies:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout treedt op: _[!UICONTROL Trying to access array offset on value of type bool]_Als je bepaalde niet bestaande categoriepaden opent voor bekende producten, ga je naar PHP 7.4.

<u>Vereisten</u>:

PHP 7.4.

<u>Stappen om te reproduceren</u>:

1. Maak een nieuw product met de naam &quot;test&quot;.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > set **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nee_.
1. Ga naar de winkel en ga naar de URL, bijvoorbeeld ../abc/test.html (&quot;abc&quot; - zou niet moeten bestaan).

<u>Verwachte resultaten</u>:

404 pagina.

<u>Werkelijke resultaten</u>:

500-fout:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
