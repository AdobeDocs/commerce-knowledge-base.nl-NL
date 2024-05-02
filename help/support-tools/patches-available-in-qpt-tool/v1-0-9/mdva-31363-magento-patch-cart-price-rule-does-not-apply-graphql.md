---
title: 'MDVA-31363 patch: Cart price rule is not apply (GraphQL)'
description: De MDVA-31363-patch stelt de kwestie vast waar de regel van de kartonprijs met coupon niet van toepassing is via GraphQL wanneer de actie 'Vaste korting voor het hele winkelwagentje' wordt gebruikt. Deze patch is beschikbaar wanneer het gereedschap Kwaliteitspatches (QPT) 1.0.9 is geïnstalleerd. Het probleem wordt opgelost in Adobe Commerce versie 2.4.2.
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-31363 patch: Cart price rule is not apply (GraphQL)

>[!WARNING]
>
>Met een nieuwe patch met de naam MDVA-33975 worden problemen met de prijsberekening door GraphQL opgelost. MDVA-31363 wordt afgeschreven en het wordt aanbevolen de pleister MDVA-33975 aan te brengen. Voor toegang tot deze patch raadpleegt u [MDVA-33975 patch: GraphQL price calculations](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

De MDVA-31363-patch stelt de kwestie vast waar de regel van de kartonprijs met coupon niet van toepassing is via GraphQL wanneer de actie &#39;Vaste korting voor het hele winkelwagentje&#39; wordt gebruikt. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9 is geïnstalleerd. Het probleem wordt opgelost in Adobe Commerce versie 2.4.2.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

Adobe Commerce over cloudinfrastructuur 2.4.0

**Compatibel met Adobe Commerce-versies:**

Adobe Commerce over cloudinfrastructuur en Adobe Commerce op locatie 2.3.2 - 2.4.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u de totalen van aanhalingstekens opnieuw berekent voordat u een reactie geeft over de prijsopgave, gaan de toegepaste regels verloren.

<u>Stappen om te reproduceren</u>:

1. Maak een eenvoudig product.
1. Maak een regel voor de winkelwagenprijs met een korting op een vast bedrag voor de hele winkelwagen.
1. Maak een nieuw winkelwagentje met GraphQL.
1. Sla de kaart\_id op uit het antwoord en voeg het product van stap 1 toe aan de wagen met GraphQL.
1. Activeer de prijsregel voor winkelwagentjes door de couponcode toe te voegen aan het winkelwagentje met GraphQL.
1. Controleer de prijs als reactie.

<u>Verwachte resultaten</u>:

Korting wordt toegepast.

<u>Werkelijke resultaten</u>:

Korting wordt niet toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in onze ontwikkelaarsdocumentatie.
