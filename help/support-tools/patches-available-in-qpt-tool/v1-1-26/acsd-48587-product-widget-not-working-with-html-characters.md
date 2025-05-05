---
title: 'ACSD-48587: productwidget werkt niet met SKU''s die HTML-tekens bevatten'
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

De ACSD-48587-patch verhelpt het probleem waarbij speciale HTML-tekens in de widgetregels voorkomen dat overeenkomende producten worden weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48587. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De product widget werkt niet met SKUs die *&quot;&amp;&quot;* symbolen bevatten.

<u> Stappen om </u> te reproduceren:

1. Creeer een product dat *&quot;&amp;&quot;* in SKU (b.v., s000&amp;01) bevat.
1. Bewerk de inhoud van een pagina van CMS op de *Bouwer van de Pagina*.
1. Een widget producten toevoegen.
1. De widget bewerken en instellen **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** .
1. Ga SKU in die *&quot;&amp;&quot;* op het gebied van product SKUs bevat.
1. Sla de inhoud en de CMS-pagina op.
1. Controleer de *pagina van CMS* inhoud voor de *voorproef van de Bouwer van de Pagina* en productopslag.

<u> Verwachte resultaten </u>:

Het product met *&quot;&amp;&quot;* in SKU wordt getoond in de voorproef van de Bouwer van de Pagina en op de winkel.

<u> Ware resultaten </u>:

Het product met *&quot;&amp;&quot;* in SKU wordt niet getoond in de voorproef van de Bouwer van de Pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
