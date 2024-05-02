---
title: "MDVA-33975 patch: GraphQL price calculations"
description: '''De MDVA-33975-patch corrigeert problemen met de prijsberekening van GraphQL. Deze kwesties zijn onder meer:"'
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# MDVA-33975 patch: GraphQL price calculations

Met de MDVA-33975-patch worden problemen met de prijsberekening voor GraphQL opgelost. Deze kwesties zijn onder meer:

* Wanneer een regel voor catalogusprijzen wordt toegepast op een bepaalde klantengroep, worden de prijzen van artikelen in het winkelwagentje en het ordertotaal niet correct berekend in GraphQL.
* Catalogusprijsregels zijn niet opgenomen in `CartItemPrices` in de API.
* De prijs van de klantgroep voor de algemene klant wordt niet toegevoegd aan de GraphQL-productzoekopdracht.
* Als u de totalen van aanhalingstekens opnieuw berekent voordat u een reactie geeft over de prijsopgave, gaan de toegepaste regels verloren.
* De korting op het verzendbedrag is niet opgehaald bij de laatste factureringsstap en het totaalbedrag is onjuist weergegeven.
* De korting wordt in GraphQL niet toegepast wanneer het klantensegment wordt gebruikt in de regel van de kartonprijs.

Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.14 is geïnstalleerd.

## Betrokken producten en versies

* De pleister is ontworpen voor Adobe Commerce op locatie 2.4.1.
* De patch is ook compatibel met de volgende Adobe Commerce-versies: Adobe Commerce op locatie en Adobe Commerce op cloud-infrastructuur 2.3.4 - 2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## De patch toepassen

Als u afzonderlijke patches wilt toepassen, gebruikt u de volgende koppelingen, afhankelijk van uw Adobe Commerce-product:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Raadpleeg voor meer informatie over andere patches die beschikbaar zijn in het gereedschap QPT de [Reparaties beschikbaar in het gereedschap QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sectie.
