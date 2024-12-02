---
title: 'ACSD-55566: [!UICONTROL mergeCart] de mutatie ontbreekt met interne serverfout in  [!DNL GraphQL]  reactie'
description: Pas ACSD-55566 flard toe om de kwestie van Adobe Commerce te bevestigen waar de "mergeCart"mutatie met een interne serverfout in  [!DNL GraphQL]  reactie ontbreekt wanneer het samenvoegen van de bron en de bestemmingstaarten die de zelfde bundelpunten hebben.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566: `mergeCart` mutatie mislukt bij interne serverfout in [!DNL GraphQL] response

De ACSD-55566-patch verhelpt het probleem waarbij de `mergeCart` -mutatie mislukt als er een interne serverfout optreedt in [!DNL GraphQL] -reactie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-5566. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`mergeCart` mutatie mislukt met een interne serverfout in de reactie van [!DNL GraphQL] wanneer de bron- en doelwinkelwagentjes met dezelfde bundelitems worden samengevoegd.

<u> Stappen om </u> te reproduceren:

1. Een aangepaste bron en een aangepaste voorraad maken.
1. Wijs de gemaakte voorraad toe aan de hoofdwebsite.
1. Creeer een eenvoudig product en wijs aan het de gecreeerde bron (qty=2) toe.
1. Maak een bundelproduct met één optie en één onderliggend product (product gemaakt in stap 3).
1. Maak een gastenwagen via [!DNL GraphQL] .
1. Voeg een bundelproduct toe met beide geselecteerde opties.
1. Sparen *cartID*.
1. Maak een klant en genereer een klanttoken.
1. Maak een klantenkar.
1. Voeg hetzelfde bundelproduct met dezelfde configuratie toe aan het winkelwagentje.
1. Probeer de gastkar met de klantenkar samen te voegen.

<u> Verwachte resultaten </u>:

De klantenkar bevat producten van beide kisten.

<u> Ware resultaten </u>:

Er treedt een interne fout op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
