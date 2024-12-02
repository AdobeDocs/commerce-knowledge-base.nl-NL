---
title: 'ACSD-51683: aanpasbare optie kan niet aan de wagen worden toegevoegd met GraphQL'
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

De ACSD-51683-patch verhelpt het probleem waarbij de aanpasbare optie niet met GraphQL aan het winkelwagentje kan worden toegevoegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-51683. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aanpasbare optie kan niet met GraphQL aan de winkelwagen worden toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Creeer een eenvoudig product met een klantgerichte **het gebied van de Tekst** optie.
1. [ voeg aan wortel ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) toe het gecreeerde product met de vereiste klantgerichte optie via GraphQL.
1. Verzend het [ karretje ](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) verzoek van GraphQL om het product en zijn details in het karretje te controleren.

<u> Verwachte resultaten </u>

De sectie `Customizable_options` in het GraphQL-antwoord bevat de gegevens die zijn opgegeven tijdens het toevoegen van het product aan het winkelwagentje.

<u> Ware resultaten </u>

De sectie `Customizable_options` in het GraphQL-antwoord is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
