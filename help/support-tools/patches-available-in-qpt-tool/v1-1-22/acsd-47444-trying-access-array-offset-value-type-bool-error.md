---
title: 'ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_ error when access certain non-existing category paths for known products on PHP 7.4'
description: Pas de ACSD-47444-patch toe om het Adobe Commerce-probleem op te lossen waarbij er een _[!UICONTROL Trying to access array offset on value of type bool]_ fout is bij het benaderen van bepaalde niet-bestaande categoriepaden voor bekende producten, op PHP 7.4.
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444: _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;fout bij het openen van bepaalde niet-bestaande categoriepaden voor bekende producten op PHP 7.4

De ACSD-47444-patch lost het probleem op waarbij _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;error optreedt wanneer je bepaalde niet-bestaande categoriepaden opent voor bekende producten op PHP 7.4. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.22 wordt geïnstalleerd.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De volgende fout treedt op: _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;wanneer u bepaalde niet-bestaande categoriepaden opent voor bekende producten, gaat u naar PHP 7.4.

<u> Eerste vereisten </u>:

PHP 7.4.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw product met de naam &quot;test&quot;.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > plaats **[!UICONTROL Generate "category/product" URL Rewrites]** = _Nr_.
1. Ga naar de winkel en ga naar de URL, bijvoorbeeld ../abc/test.html (&quot;abc&quot; - zou niet moeten bestaan).

<u> Verwachte resultaten </u>:

404 pagina.

<u> Ware resultaten </u>:

500-fout:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
