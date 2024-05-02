---
title: '''ACSD-45168: SEO-vriendelijke URL''s die niet zijn gegenereerd voor producten met overschreven URL_key-kenmerken'''
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

De ACSD-45168-patch verhelpt het probleem dat er geen SEO-vriendelijke URL&#39;s worden gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24 is geïnstalleerd. De patch-id is ACSD-45168. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

SEO-vriendelijke URL&#39;s worden niet gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave.

<u>Stappen om te reproduceren</u>:

1. Stel de configuratie als volgt in door naar de **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Reinig de configuratiecache.
1. Twee categorieën maken: [!UICONTROL Category 1] en [!UICONTROL Category 2].
1. Twee producten maken: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Het bereik wijzigen in [!UICONTROL Default Store View] for [!UICONTROL Product 1].
1. De optionele URL uitschakelen [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Sla het product op.
1. Terug naar [!UICONTROL All Store Views].
1. Toevoegen [!UICONTROL Product 1] tot [!UICONTROL Category 2]en toevoegen [!UICONTROL Product 2] tot [!UICONTROL Category 2].
1. Controleer de [!UICONTROL url_rewrite] tabel of [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Verwachte resultaten</u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] is gemaakt voor [!UICONTROL Product 1].

<u>Werkelijke resultaten</u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] ontbreekt voor [!UICONTROL Product 1] omdat het URL-sleutelkenmerk is overschreven voor het weergavebereik van de winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
