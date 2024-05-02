---
title: '"ACSD-55566: [!UICONTROL mergeCart] mutatie mislukt vanwege interne serverfout in [!DNL GraphQL] response'''
description: Pas de ACSD-55566-patch toe om het Adobe Commerce-probleem op te lossen waarbij de "mergeCart"-mutatie mislukt met een interne serverfout in [!DNL GraphQL] reactie bij het samenvoegen van de bron- en doelwinkelwagentjes die dezelfde bundelitems hebben.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-5566: `mergeCart` mutatie mislukt vanwege interne serverfout in [!DNL GraphQL] reactie

De ACSD-55566-patch verhelpt het probleem waarbij de `mergeCart` mutatie mislukt vanwege een interne serverfout in [!DNL GraphQL] reactie. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48 is geïnstalleerd. De patch-id is ACSD-5566. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`mergeCart` mutatie mislukt vanwege een interne serverfout in [!DNL GraphQL] reactie bij het samenvoegen van de bron- en doelwinkelwagentjes die dezelfde bundelitems hebben.

<u>Stappen om te reproduceren</u>:

1. Een aangepaste bron en een aangepaste voorraad maken.
1. Wijs de gemaakte voorraad toe aan de hoofdwebsite.
1. Creeer een eenvoudig product en wijs aan het de gecreeerde bron (qty=2) toe.
1. Maak een bundelproduct met één optie en één onderliggend product (product gemaakt in stap 3).
1. Een gastransport maken via [!DNL GraphQL].
1. Voeg een bundelproduct toe met beide geselecteerde opties.
1. Sla de *cartID*.
1. Maak een klant en genereer een klanttoken.
1. Maak een klantenkar.
1. Voeg hetzelfde bundelproduct met dezelfde configuratie toe aan het winkelwagentje.
1. Probeer de gastkar met de klantenkar samen te voegen.

<u>Verwachte resultaten</u>:

De klantenkar bevat producten van beide kisten.

<u>Werkelijke resultaten</u>:

Er treedt een interne fout op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
