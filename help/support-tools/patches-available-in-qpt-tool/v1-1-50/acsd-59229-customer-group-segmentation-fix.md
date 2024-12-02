---
title: 'ACSD-59229: onjuiste toewijzing van gegevens aan de klantengroep als gevolg van een verouderde waarde voor X-Magento-Variabele'
description: Pas de ACSD-59229-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de groepsgerelateerde informatie van de klant in het verkeerde segment wordt opgeslagen vanwege een verouderde X-Magento-Variabele waarde in het verzoek.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: 090b674a-5103-48cd-9426-41166bf9272c
source-git-commit: 06f751e43ef825c0eb29cb9b42eb41f07c308625
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: onjuiste toewijzing van gegevens aan de klantengroep als gevolg van een verouderde waarde voor X-Magento-Variabele

De ACSD-59229-patch verhelpt het probleem waarbij groepsgerelateerde informatie van klanten wordt opgeslagen in het verkeerde segment vanwege een verouderde X-Magento-Variabele waarde in het verzoek. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59229. De kwestie is opgelost in 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aan de groep gerelateerde informatie van de klant wordt opgeslagen in het verkeerde segment vanwege een verouderde waarde voor X-Magento-Variant in het verzoek.

<u> Eerste vereisten </u>:

Controleer of Adobe Commerce B2B met voorbeeldgegevens is geïnstalleerd en of [!DNL Varnish] is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Geavanceerde prijzen instellen voor de [!DNL SKU 24-MB01] :
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Wholesale* = *$200*
      * *Detailhandelaar* = *$30*

1. Maak twee klantenaccounts.
1. Wijs beide klanten aan de **Groothandel** groep toe.
1. Open twee verschillende browsersessies en meld u aan bij elke klant.
1. Navigeer naar de **[!UICONTROL 24-MB01]** productpagina voor elke klant en controleer of de weergegeven prijs *$200* is.
1. Verander de klantengroep voor één van de klanten in **Detailhandel**.
1. Wis het cachegeheugen met de opdracht: `bin/magento cache:flush full_page` .
1. Vernieuw de productpagina voor elke klant.

<u> Verwachte resultaten </u>:

1. De detailhandelsklant kan de correcte prijs van *$30* voor het product zien.
1. De grootafnemer kan de correcte prijs van *$200* voor het product zien.

<u> Ware resultaten </u>:

1. De detailhandelsklant kan de correcte prijs van *$30* voor het product zien.
1. De grootafnemer ziet een onjuiste prijs van *$30* (kleinhandelsprijs) voor het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
