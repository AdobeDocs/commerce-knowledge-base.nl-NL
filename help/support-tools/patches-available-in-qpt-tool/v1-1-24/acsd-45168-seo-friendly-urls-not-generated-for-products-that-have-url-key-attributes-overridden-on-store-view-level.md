---
title: 'ACSD-45168: SEO-vriendelijke URL''s die niet zijn gegenereerd voor producten met overschreven URL_key-kenmerken'
description: Pas de ACSD-45168-patch toe om het Adobe Commerce-probleem op te lossen waarbij geen SEO-vriendelijke URL's worden gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op archiefweergaveniveau.
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168: SEO-vriendelijke URL&#39;s die niet zijn gegenereerd voor producten met overschreven URL_key-kenmerken

De ACSD-45168-patch verhelpt het probleem dat er geen SEO-vriendelijke URL&#39;s worden gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-45168. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

SEO-vriendelijke URL&#39;s worden niet gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Stel de configuratie als volgt in door naar **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** te gaan:
   * [!UICONTROL Use Categories Path for Product URLs] = *ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *ja*
1. Reinig de configuratiecache.
1. Maak twee categorieën: [!UICONTROL Category 1] en [!UICONTROL Category 2] .
1. Maak twee producten: [!UICONTROL Product 1] in [!UICONTROL Category 1] , [!UICONTROL Product 2] in [!UICONTROL Category 1] .
1. Wijzig het bereik in [!UICONTROL Default Store View] for [!UICONTROL Product 1] .
1. Schakel de optionele URL [!UICONTROL Key] uit in [!UICONTROL Search Engine Optimization] .
1. Sla het product op.
1. Ga terug naar [!UICONTROL All Store Views] .
1. Voeg [!UICONTROL Product 1] toe aan [!UICONTROL Category 2] en voeg [!UICONTROL Product 2] toe aan [!UICONTROL Category 2] .
1. Controleer de [!UICONTROL url_rewrite] tabel of [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites] .

<u> Verwachte resultaten </u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] wordt gemaakt voor [!UICONTROL Product 1] .

<u> Ware resultaten </u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] ontbreekt voor [!UICONTROL Product 1] omdat het URL-sleutelkenmerk is overschreven voor het weergavebereik van de winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
