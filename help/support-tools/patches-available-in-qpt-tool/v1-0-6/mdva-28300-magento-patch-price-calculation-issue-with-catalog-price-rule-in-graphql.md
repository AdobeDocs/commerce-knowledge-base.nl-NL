---
title: "MDVA-28300: Uitgave voor berekening van de prijs met toepassing van de catalogusprijsregel in GraphQL"
description: De patch MDVA-28300 verhelpt het probleem dat GraphQL-aanvraag geen weerspiegeling is van prijswijzigingen in catalogusprijsregels. Deze patch is beschikbaar wanneer het hulpmiddel van de Patches van de Kwaliteit (QPT) v.1.0.6 wordt geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.6.
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300: Uitgifte van een prijsberekening met inachtneming van de catalogusprijsregel in GraphQL

>[!WARNING]
>
>Met een nieuwe patch met de naam MDVA-33975 worden problemen met de prijsberekening door GraphQL opgelost. MDVA-28300 wordt afgeschreven en het wordt aanbevolen de pleister MDVA-33975 aan te brengen. Voor toegang tot deze patch raadpleegt u [MDVA-33975: GraphQL-prijsberekeningen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

De patch MDVA-28300 verhelpt het probleem dat GraphQL-aanvraag geen weerspiegeling is van prijswijzigingen in catalogusprijsregels. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versie 1.0.6 is geïnstalleerd. Het probleem is opgelost in Adobe Commerce versie 2.3.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce op locatie 2.3.5-p1

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een regel voor catalogusprijzen wordt toegepast op een bepaalde klantengroep, worden de objectprijzen in het winkelwagentje en het ordertotaal niet correct berekend in GraphQL.

<u>Stappen om te reproduceren:</u>

1. Maak een nieuwe klantenaccount en wijzig de klantgroep in Groothandel.
1. Nieuwe regel voor catalogi maken in **Marketing** > **Aanbiedingen** > **Catalogusprijsregels** met de volgende parameters:
   * Klantengroepen: Groothandelsacties:
   * Toepassen: *Toepassen als percentage van origineel*
   * Korting: *50*


1. Maak een nieuw product met prijs=100.
1. Meld u aan bij de frontend met behulp van de eerder gemaakte klantenaccount (als u al was aangemeld, meldt u zich af en meldt u zich opnieuw aan).
1. Voeg het product toe aan de kar. De prijs van het product is 50 (normale prijs 100) en Order Total: 55 (50 + 5 van de verzendkosten).
1. Voer de GraphQL API-aanroep uit zoals beschreven in [customerCart-query](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) in onze ontwikkelaarsdocumentatie.

<u>Verwacht resultaat:</u>

Zowel API als frontend hebben het zelfde orde totaal met de korting die door de catalogusregel wordt geïntroduceerd die wordt toegepast.

<u>Werkelijk resultaat:</u>

Het totaal van de orde past de geen korting van de catalogusregel toe.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Patches toepassen met het gereedschap Kwaliteitspatches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply patches](https://devdocs.magento.com/cloud/project/project-patch.html).

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar de Patches beschikbaar in de sectie QPT.
