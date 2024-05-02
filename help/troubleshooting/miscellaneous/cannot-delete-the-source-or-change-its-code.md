---
title: Kan de bron niet verwijderen of de code ervan wijzigen
description: Dit artikel biedt een oplossing voor het geval dat u een bron niet volledig kunt verwijderen en/of de code ervan kunt wijzigen.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Kan de bron niet verwijderen of de code ervan wijzigen

Dit artikel biedt een oplossing voor het geval dat u een bron niet volledig kunt verwijderen en/of de code ervan kunt wijzigen.

## Probleem

Bronnen kunnen niet worden verwijderd, ongeacht de producttoewijzing.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur (alle versies), met Magento Inventory geïnstalleerd
* Adobe Commerce op locatie 2.3.0 en hoger, met Magento Inventory geïnstalleerd
* Magento Open Source 2.3.0 en hoger, met Magento Inventory geïnstalleerd

## Oorzaak

Door ontwerp, is het niet mogelijk om een bron volledig te verwijderen en/of zijn code te veranderen.

Als u een bron volledig verwijdert, ontstaan er problemen met ordergegevens omdat bronnen deel uitmaken van productinventarissen, orders, verzendgegevens en nog veel meer.

De code is essentieel voor het verbinden van de bron met orden. Dit is een unieke id voor de bron en kan niet worden bewerkt.

## Oplossing

U kunt een bron uit een product verwijderen door de voorraad over te brengen of het product van alle verzendingen op een locatie te laten vallen.

Als u een bron moet verwijderen uit [SSA](https://devdocs.magento.com/guides/v2.3/inventory/source-selection-algorithms.html) U kunt de bron uitschakelen door berekeningen en Adobe Commerce Inventory Order-verwerking uit te voeren. Uitgeschakelde bronnen bewaren alle gegevens, toegewezen producten en inventarishoeveelheden en kunnen op elk moment weer worden ingeschakeld om opnieuw te beginnen met verzenden.

Zie de [Hulplijn Bronnen maken](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) voor meer informatie over het uitschakelen van een bron.
