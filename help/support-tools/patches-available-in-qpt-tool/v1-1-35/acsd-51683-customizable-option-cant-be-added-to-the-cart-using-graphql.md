---
title: "ACSD-51683: aanpasbare optie kan niet aan het winkelwagentje worden toegevoegd met GraphQL"
description: Pas de ACSD-51683-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanpasbare optie niet met GraphQL aan het winkelwagentje kan worden toegevoegd.
feature: GraphQL
role: Admin
exl-id: 4de0d8b7-714e-4bbf-8a0d-bb6e0c3aae55
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51683: aanpasbare optie kan niet aan de wagen worden toegevoegd met GraphQL

De ACSD-51683-patch verhelpt het probleem waarbij de aanpasbare optie niet met GraphQL aan het winkelwagentje kan worden toegevoegd. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 is geïnstalleerd. De patch-id is ACSD-51683. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aanpasbare optie kan niet met GraphQL aan de winkelwagen worden toegevoegd.

<u>Stappen om te reproduceren</u>:

1. Een eenvoudig product maken met een aanpasbare **Tekstveld** -optie.
1. [Toevoegen aan winkelwagentje](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) het gemaakte product met de vereiste aanpasbare optie via GraphQL.
1. Verzend de [karretje](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL vraagt om het product en zijn gegevens in het karretje te controleren.

<u>Verwachte resultaten</u>

De `Customizable_options` in het GraphQL-antwoord bevat de gegevens die zijn opgegeven wanneer het product aan het winkelwagentje wordt toegevoegd.

<u>Werkelijke resultaten</u>

De `Customizable_options` in het GraphQL-antwoord is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
