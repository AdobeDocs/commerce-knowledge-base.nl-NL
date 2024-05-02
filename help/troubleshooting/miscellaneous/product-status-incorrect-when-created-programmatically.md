---
title: De productstatus is onjuist bij het programmeren
description: Dit artikel verstrekt een moeilijke situatie voor wanneer de productstatus Gehandicapten is en de producten niet op de opslagvoorzijde worden getoond, of aan de verkeerde opslagmeningen toegewezen, wanneer gecreeerd/programmatically bijgewerkt.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# De productstatus is onjuist bij het programmeren

Dit artikel verstrekt een moeilijke situatie voor wanneer de productstatus Gehandicapten is en de producten niet op de opslagvoorzijde worden getoond, of aan de verkeerde opslagmeningen toegewezen, wanneer gecreeerd/programmatically bijgewerkt.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.X.X
* Adobe Commerce op locatie 2.X.X

## Probleem

Wanneer de catalogusproducten programmatically van een manuscript met Adobe Commerce toepassing bootstrapped worden gecreeerd of worden bijgewerkt, zouden de producten de status van Uitgeschakeld kunnen hebben en/of aan de verkeerde opslagmeningen toegewezen.

## Oorzaak

De kwestie zou wegens ACL beperkingen kunnen verschijnen die voor de instantie van Adobe Commerce admin rollen worden geplaatst. In het geval van bootstrapped toepassing, zullen er geen geïnitialiseerde admin zittingen met aangewezen ACL montages zijn. Hierdoor zouden validaties mislukken in het dialoogvenster `Magento_AdminGws` die verantwoordelijk is voor het controleren van machtigingen voor dergelijke handelingen.

## Oplossing voor onjuiste productstatus

Stel een dynamische voorkeur in voor de `Magento\Framework\Authorization\PolicyInterface`, zoals beschreven in de [ObjectManager>Programmatische productupdates](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* [Github: Kan de productstatus van het product dat met productRepository wordt gemaakt, niet wijzigen](https://github.com/magento/magento2/issues/5664)
