---
title: "Adobe Commerce 2.4.2 B2B: e-mailsjabloon niet bijwerken e-mail"
description: In dit artikel wordt een bekende Adobe Commerce 2.4.2 B2B-uitgave beschreven waarbij het bijwerken van bepaalde gegevens in een e-mailsjabloon niet in e-mailberichten wordt bijgewerkt. Dit probleem is van invloed op e-mailinhoud zoals klantgegevens, wisselkoersen, valutasymbool, wijziging van e-mailsjabloon, enzovoort. Er is momenteel geen oplossing beschikbaar, maar onderaan dit artikel vindt u een oplossing.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B: e-mailsjabloon werkt e-mail niet bij

In dit artikel wordt een bekende Adobe Commerce 2.4.2 B2B-uitgave beschreven waarbij het bijwerken van bepaalde gegevens in een e-mailsjabloon niet in e-mailberichten wordt bijgewerkt. Dit probleem is van invloed op e-mailinhoud zoals klantgegevens, wisselkoersen, valutasymbool, wijziging van e-mailsjabloon, enzovoort. Er is momenteel geen oplossing beschikbaar, maar onderaan dit artikel vindt u een oplossing.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.4.2
* Adobe Commerce cloud-infrastructuur 2.4.2
* B2B 1.3.1

## Probleem

<u>Stappen om te reproduceren</u>:

1. Bedrijfsbeheerder maakt vooraf een inkooporder (inkooporder).
1. Controleer het automatisch goedgekeurde e-mailbericht. De **naam klant** / **valutakoers** moeten verwachte waarden zijn.
1. Valutasymbool wijzigen (**Stores > Configuration > Currency Setup > Currency Options**) in de beheernaam van Admin en het bedrijf op de pagina Customer Account.
1. Beheerder van de klant maakt een andere inkooporder in Admin.
1. Controleer het automatisch goedgekeurde e-mailbericht.

<u>Verwachte resultaten:</u>

De naam en het valutasymbool van de klant worden gewijzigd in e-mailberichten en hebben de nieuwe waarden zoals verwacht.

<u>Werkelijke resultaten</u>:

De naam en het valutasymbool van de klant worden niet gewijzigd in e-mailberichten en hebben hun vorige waarden.

## Workaround

Voer handmatig de snijtaak of de consument uit om de nieuwe informatie te verspreiden.

## Gerelateerde lezing

* [Berichtenrijen beheren](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html) in onze ontwikkelaarsdocumentatie.
