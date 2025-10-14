---
title: Het product wordt niet weergegeven op de winkel
description: Dit artikel biedt oplossingen voor het gebruik van producten die niet in de winkel worden weergegeven.
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Het product wordt niet weergegeven op de winkel

Dit artikel biedt oplossingen voor het gebruik van producten die niet in de winkel worden weergegeven.

## Betrokken producten en versies

* Adobe Commerce op locatie X.X.X
* Adobe Commerce op cloud-infrastructuur X.X.X

## Probleem

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar **Catalogus** > **Producten**.

   ![&#x200B; open_product_page_magento_2.4.1.png &#x200B;](assets/open_product_page_magento_2.4.1.png)

1. Klik **toevoegen Product** en ga door het proces van de productverwezenlijking. Of importeer producten uit een CSV-bestand.

<u> Verwacht resultaat </u>:

Het product wordt weergegeven op de winkel.

<u> Werkelijk resultaat </u>:

Het product wordt niet weergegeven.

## Oorzaak

Dit kan om verschillende redenen worden veroorzaakt. Volg de onderstaande stappen om de belangrijkste punten te controleren die kunnen helpen om het probleem te identificeren en op te lossen.

## Oplossing

Elk van de volgende punten zou de kwestie kunnen oplossen.

* Controleer de productinstellingen in Admin. Ga naar **Catalogus** > **Producten**, open de productpagina en zorg ervoor de volgende gebieden correct worden gevormd:
   * **laat Product** toe = *ja.*
   * **Status van de Beeld**: *in Voorraad*. Of als *uit Voorraad* de correcte waarde is, zorg ervoor dat **Vertoning uit de Producten van de Voorraad** (**STORES** > **Montages** > **Configuratie** > **CATALOGUS** > **Voorraad** > **Opties van de Voorraad** 6&rbrace; Vertoning uit de Producten van de Voorraad **) wordt geplaatst aan *ja* (gevormd op globaal niveau).**
   * **Categorieën**: Als u probeert om het product op een categoriepagina te vinden, verifieer dat het product aan de categorie wordt toegewezen. Om het oplossen van problemen te vereenvoudigen, creeer een nieuwe categorie van de huidige pagina en wijs een product aan het toe.
   * **Zichtbaarheid** = *Catalogus, Onderzoek.*
   * In het **Product in Websites** sectie, zorg ervoor het product aan de correcte website wordt toegewezen.
   * Schakel de bereikkiezer naar de winkelweergave waar u het product op de winkel probeert te vinden en controleer dezelfde instellingen.
* Voer de volledige herdex uit, door `bin/magento indexer:reindex` van de console in werking te stellen, en al geheim voorgeheugen in Admin, onder **Systeem** te spoelen > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen**, of van de console door `bin/magento cache:clean` in werking te stellen.
* Als het bovenstaande niet helpt, kunt u verder onderzoek starten door logbestanden in de map `var/log` te controleren.

## Gerelateerde lezing in onze kennisbasis voor support

* [Loglocaties (mappen) voor Pro-architectuur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Loglocaties (directory&#39;s) voor starterarchitectuur](/help/how-to/general/log-locations-directories-for-starter-plan.md)
