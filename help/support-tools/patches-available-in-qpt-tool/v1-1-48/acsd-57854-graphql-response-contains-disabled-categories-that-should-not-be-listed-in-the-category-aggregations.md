---
title: "ACSD-57854: *GraphQL* response bevat uitgeschakelde categorieën die niet in de categorieconcentraties mogen worden vermeld"
description: Pas de ACSD-57854-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de *GraphQL*-respons uitgeschakelde categorieën bevat die niet in de categoriesamenvoegingen moeten worden vermeld.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: *GraphQL* reactie bevat uitgeschakelde categorieën die niet moeten worden vermeld in de categoriesamenvoegingen

De ACSD-57854-patch verhelpt het probleem waarbij de *GraphQL* de reactie bevat gehandicapte categorieën die niet in de categoriesamenvoegingen zouden moeten worden vermeld. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.48 is geïnstalleerd. De patch-id is ACSD-57854. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*GraphQL* de reactie bevat gehandicapte categorieën die niet in de categoriesamenvoegingen zouden moeten worden vermeld.

<u>Stappen om te reproduceren</u>:

1. Maak twee categorieën.
1. Maak een product (Testproduct voor Adobe) en wijs het product aan beide categorieën toe.
1. Schakel een van de categorieën uit die is gemaakt.
1. Producten gebruiken *GraphQL* om het product te doorzoeken.
1. Controleer de lijst met productcategorieën in het dialoogvenster *GraphQL* reactie.

<u>Verwachte resultaten</u>:

De uitgeschakelde categorieën worden niet vermeld in de *GraphQL* reactie.

<u>Werkelijke resultaten</u>:

De uitgeschakelde categorieën worden vermeld in de categoriesamenvoeging *GraphQL* reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
