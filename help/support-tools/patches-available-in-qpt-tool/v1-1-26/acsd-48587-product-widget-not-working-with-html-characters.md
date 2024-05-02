---
title: '''ACSD-48587: productwidget die niet werkt met SKU''s die HTML-tekens bevatten'''
description: Pas de ACSD-48587-patch toe om het Adobe Commerce-probleem op te lossen, waarbij speciale HTML-tekens in de widgetovereenkomsten voorkomen dat overeenkomende producten worden weergegeven.
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587: productwidget werkt niet met SKU&#39;s die HTML-tekens bevatten

De ACSD-48587-patch verhelpt het probleem waarbij speciale HTML-tekens in de widgetregels voorkomen dat overeenkomende producten worden weergegeven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 is geïnstalleerd. De patch-id is ACSD-48587. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productwidget werkt niet met SKU&#39;s die *&quot;&amp;&quot;* symbolen.

<u>Stappen om te reproduceren</u>:

1. Een product maken dat *&quot;&amp;&quot;* in de SKU (bijvoorbeeld s000&amp;01).
1. De inhoud van een CMS-pagina bewerken op de *Page Builder*.
1. Een widget producten toevoegen.
1. De widget en set bewerken **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Voer de SKU in die de *&quot;&amp;&quot;* in het veld SKU&#39;s.
1. Sla de inhoud en de CMS-pagina op.
1. Controleer de *CMS-pagina* inhoud voor de *Voorvertoning van Page Builder* en de productwinkel.

<u>Verwachte resultaten</u>:

Het product *&quot;&amp;&quot;* in SKU wordt getoond in de voorproef van de Bouwer van de Pagina en op de winkel.

<u>Werkelijke resultaten</u>:

Het product *&quot;&amp;&quot;* in SKU wordt niet getoond in de voorproef van de Bouwer van de Pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
