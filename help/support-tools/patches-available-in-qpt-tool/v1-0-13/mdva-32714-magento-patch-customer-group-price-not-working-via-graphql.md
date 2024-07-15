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
>Met een nieuwe patch met de naam MDVA-33975 worden problemen met de prijsberekening door GraphQL opgelost. MDVA-32714 wordt afgeschreven en het wordt aanbevolen de pleister MDVA-33975 aan te brengen. Om tot dit flard toegang te hebben, verwijs naar [ mDVA-33975 flard: de prijsberekeningen van GraphQL ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) in onze steunkennisbasis.

De patch MDVA-32714 verhelpt het probleem waarbij с prijs van de klantengroep niet wordt toegevoegd aan de antwoorden op de productvraag van GraphQL. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13 geïnstalleerd is. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.3.4 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijs van de klantgroep voor de algemene klant wordt niet toegevoegd in de antwoorden op GraphQL-productvragen.

<u> Stappen om </u> te reproduceren:

1. Schakel Speciale prijs in voor elk product voor elke klantengroep.
1. De productvraag van het gebruik in GraphQL om prijzen voor dit product te trekken, zoals die in wordt beschreven: [ de vraag van Producten > de vraag van de Steekproef ](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) in onze ontwikkelaarsdocumentatie.

<u> Verwachte resultaten </u>:

```api
price_range
```

geeft de gedisconteerde prijs voor algemene klanten weer volgens wat in het Admin Panel is bepaald.

<u> Ware resultaten </u>:

```api
price_range
```

geeft de verlaagde prijs voor algemene klanten niet weer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
