---
title: Kan de bron niet verwijderen of de code ervan wijzigen
description: Dit artikel biedt een oplossing voor het geval dat u een bron niet volledig kunt verwijderen en/of de code ervan kunt wijzigen.
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Als u een bron uit [&#x200B; SSA &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/basics/selection-reservations) berekeningen en de ordeverwerking van de Inventaris van Adobe Commerce moet verwijderen, kunt u de bron onbruikbaar maken. Uitgeschakelde bronnen bewaren alle gegevens, toegewezen producten en inventarishoeveelheden en kunnen op elk moment weer worden ingeschakeld om opnieuw te beginnen met verzenden.

Zie de [&#x200B; Create Brongids &#x200B;](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources) voor details op hoe te om een bron onbruikbaar te maken.
