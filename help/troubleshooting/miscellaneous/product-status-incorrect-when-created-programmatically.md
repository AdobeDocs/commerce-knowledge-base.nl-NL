---
title: De productstatus is onjuist bij het programmeren
description: Dit artikel verstrekt een moeilijke situatie voor wanneer de productstatus Gehandicapten is en de producten niet op de opslagvoorzijde worden getoond, of aan de verkeerde opslagmeningen toegewezen, wanneer gecreeerd/programmatically bijgewerkt.
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

De kwestie zou wegens ACL beperkingen kunnen verschijnen die voor de instantie van Adobe Commerce admin rollen worden geplaatst. In het geval van bootstrapped toepassing, zullen er geen geïnitialiseerde admin zittingen met aangewezen ACL montages zijn. Hierdoor zouden validaties mislukken in de module `Magento_AdminGws` , die verantwoordelijk is voor het controleren van machtigingen voor dergelijke handelingen.

## Oplossing voor onjuiste productstatus

Plaats een dynamische voorkeur van DI voor `Magento\Framework\Authorization\PolicyInterface`, zoals die in het [ wordt beschreven ObjectManager>Programmatic product werkt ](https://developer.adobe.com/commerce/php/development/components/object-manager/) onderwerp in onze ontwikkelaarsdocumentatie bij.

## Gerelateerde lezing

* [ Github: Kan productstatus niet veranderen die het product met productRepository ](https://github.com/magento/magento2/issues/5664) werd gecreeerd
