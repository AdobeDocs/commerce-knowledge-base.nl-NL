---
title: "MDVA-32714 patch: customer group price not working via GraphQL"
description: De patch MDVA-32714 verhelpt het probleem waarbij с prijs van de klantengroep niet wordt toegevoegd aan de antwoorden op de productvraag van GraphQL. Deze patch is beschikbaar wanneer het gereedschap Kwaliteitspatches (QPT) 1.0.13 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-32714 patch: Customer group price not working via GraphQL

>[!WARNING]
>
>Met een nieuwe patch met de naam MDVA-33975 worden problemen met de prijsberekening door GraphQL opgelost. MDVA-32714 wordt afgeschreven en het wordt aanbevolen de pleister MDVA-33975 aan te brengen. Voor toegang tot deze patch raadpleegt u [MDVA-33975 patch: GraphQL price calculations](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) in onze kennisbasis voor ondersteuning.

De patch MDVA-32714 verhelpt het probleem waarbij с prijs van de klantengroep niet wordt toegevoegd aan de antwoorden op de productvraag van GraphQL. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van de klantgroep voor de algemene klant wordt niet toegevoegd in de antwoorden op GraphQL-productvragen.

<u>Stappen om te reproduceren</u>:

1. Schakel Speciale prijs in voor elk product voor elke klantengroep.
1. Gebruik productquery in GraphQL om prijzen voor dit product te vragen, zoals beschreven in: [Products query > Sample query](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) in onze ontwikkelaarsdocumentatie.

<u>Verwachte resultaten</u>:

```api
price_range
```

geeft de gedisconteerde prijs voor algemene klanten weer volgens wat in het Admin Panel is bepaald.

<u>Werkelijke resultaten</u>:

```api
price_range
```

geeft de verlaagde prijs voor algemene klanten niet weer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
