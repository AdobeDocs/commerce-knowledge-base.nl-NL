---
title: 'ACSD-57854: *GraphQL* response bevat uitgeschakelde categorieën die niet in de categoriesamenvoegingen moeten worden vermeld'
description: Pas de ACSD-57854-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de *GraphQL*-respons uitgeschakelde categorieën bevat die niet in de categoriesamenvoegingen moeten worden vermeld.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: *GraphQL* reactie bevat gehandicapte categorieën die niet in de categorieconcentraties zouden moeten worden vermeld

Het ACSD-57854 flard bevestigt de kwestie waar de *GraphQL* reactie gehandicapte categorieën bevat die niet in de categoriesamenvoegingen zouden moeten worden vermeld. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57854. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*GraphQL* reactie bevat gehandicapte categorieën die niet in de categoriesamenvoegingen zouden moeten worden vermeld.

<u> Stappen om </u> te reproduceren:

1. Maak twee categorieën.
1. Maak een product (Testproduct voor Adobe) en wijs het product aan beide categorieën toe.
1. Schakel een van de categorieën uit die is gemaakt.
1. De producten van het gebruik *GraphQL* om het product te zoeken.
1. Controleer de lijst van de productcategorieën in de *GraphQL* reactie.

<u> Verwachte resultaten </u>:

De gehandicapte categorieën zijn niet vermeld in de *GraphQL* reactie.

<u> Ware resultaten </u>:

De gehandicapte categorieën zijn vermeld in de reactie van de categoriesamenvoeging *GraphQL*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
