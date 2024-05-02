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

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar **Catalogus** > **Producten**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. Klikken **Product toevoegen** en doorloopt het proces voor het maken van producten. Of importeer producten uit een CSV-bestand.

<u>Verwacht resultaat</u>:

Het product wordt weergegeven op de winkel.

<u>Werkelijk resultaat</u>:

Het product wordt niet weergegeven.

## Oorzaak

Dit kan om verschillende redenen worden veroorzaakt. Volg de onderstaande stappen om de belangrijkste punten te controleren die kunnen helpen om het probleem te identificeren en op te lossen.

## Oplossing

Elk van de volgende punten zou de kwestie kunnen oplossen.

* Controleer de productinstellingen in Admin. Ga naar **Catalogus** > **Producten**, opent u de productpagina en controleert u of de volgende velden correct zijn geconfigureerd:
   * **Product inschakelen** = *Ja.*
   * **Status van voorraad**: *In voorraad*. of als *Uit voorraad* is de juiste waarde, zorg ervoor dat **Producten uit voorraad weergeven** (**VOORRADEN** > **Instellingen** > **Configuratie** > **CATALOGUS** > **Inventaris** > **Opties voor voorraad** > **Producten uit voorraad weergeven**) is ingesteld op *Ja* (geconfigureerd op mondiaal niveau).
   * **Categorieën**: Als u het product op een categoriepagina probeert te vinden, controleert u of het product aan de categorie is toegewezen. Om het oplossen van problemen te vereenvoudigen, creeer een nieuwe categorie van de huidige pagina en wijs een product aan het toe.
   * **Zichtbaarheid** = *Catalogus, zoeken.*
   * In de **Product op websites** , zorgt u ervoor dat het product aan de juiste website wordt toegewezen.
   * Schakel de bereikkiezer naar de winkelweergave waar u het product op de winkel probeert te vinden en controleer dezelfde instellingen.
* Voer de volledige herindex uit door `bin/magento indexer:reindex` vanaf de console, en verwijder alle cache in de Admin, onder **Systeem** > **Gereedschappen** > **Cachebeheer** of vanaf de console door `bin/magento cache:clean`.
* Als het bovenstaande niet helpt, kunt u verder onderzoek starten door logbestanden in te checken in het dialoogvenster `var/log` directory.

## Gerelateerde lezing in onze kennisbasis voor support

* [Loglocaties (mappen) voor Pro-architectuur](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [Loglocaties (directory&#39;s) voor starterarchitectuur](/help/how-to/general/log-locations-directories-for-starter-plan.md)
