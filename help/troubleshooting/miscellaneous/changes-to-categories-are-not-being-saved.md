---
title: Wijzigingen in categorieën worden niet opgeslagen
description: Dit artikel bevat een oplossing voor het bijwerken van productcategorieën via Commerce Admin. De wijzigingen worden niet weergegeven op de beheerdersinterface en de winkel. Het probleem wordt veroorzaakt door de bedorven gegevens in ` catalog_category_entity lijst `. U lost het probleem op door de updaterecords voor problematische categorieën in de tabel te corrigeren of te verwijderen. Daarna kunt u de productcategorieën bijwerken met de Admin.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Wijzigingen in categorieën worden niet opgeslagen

Dit artikel bevat een oplossing voor het bijwerken van productcategorieën via Commerce Admin. De wijzigingen worden niet weergegeven op de beheerdersinterface en de winkel. Het probleem wordt veroorzaakt door de beschadigde gegevens in de tabel `catalog_category_entity` . U lost het probleem op door de updaterecords voor problematische categorieën in de tabel te corrigeren of te verwijderen. Daarna kunt u de productcategorieën bijwerken met de Admin.

## Probleem

Nadat u wijzigingen hebt aangebracht in een productcategorie in Beheer en deze hebt opgeslagen, worden de nieuwe updates niet opgeslagen en niet weergegeven in de beheerdersruimte en de opslagruimte.

### Stappen om te reproduceren

1. Ga naar **Catalogus** > **Categorieën**.
1. Selecteer een categorie.
1. Breng veranderingen aan, dan klik **sparen**.
1. Het bericht wordt getoond: *u bewaarde de categorie*.
1. De wijziging die u hebt aangebracht, is niet opgeslagen.

## Mogelijke oorzaak: beschadigde gegevens in de tabel `catalog_category_entity`

Het probleem wordt veroorzaakt door dezelfde waarden in de kolom `created_in` van de categorierecords in de database (DB) die hierdoor worden beïnvloed.

![ Beschadigde gegevens in de catalog_category_entity lijst ](assets/catalog_category_entity.png)

Details:

* De `catalog_category_entity` DB-tabel heeft twee of meer records voor de desbetreffende categorie (deze records hebben dezelfde `entity_id` -waarde).
* Deze categorierecords hebben **de zelfde waarden in de `created_in` kolom**.

### Hoe verschijnt de tweede ingang van DB (en alle volgende) in OB voor één en de zelfde categorie?

De tweede DB-record (en mogelijk de volgende record) voor de desbetreffende categorie betekent dat er categorietoewijzingen zijn gepland met de module Magento\_Staging. De module maakt een extra record voor een categorie in de `catalog_category_entity` . Dit is het verwachte gedrag van de toepassing. Het probleem is dat de records dezelfde waarden hebben voor de kolom `created_in` .

### Hoe worden dezelfde waarden weergegeven?

We kunnen de redenen voor gegevenscorruptie niet met zekerheid noemen. De mogelijke redenen kunnen zijn:

* aanpassingen (code, thema&#39;s, enz.)
* onjuiste gegevensmigratie
* onjuiste gegevensherstel van back-up

Voor zover wij weten is dergelijke gegevensbeschadiging niet typisch voor het &quot;schone&quot; (out-of-the-box) Adobe Commerce-exemplaar en kan deze niet worden gereproduceerd op een Adobe Commerce-installatie zonder aanpassingen.

### Hoe dit te verifiëren is uw probleem

De `catalog_category_entity` -tabel moet meerdere records voor de desbetreffende categorie bevatten (records moeten dezelfde `entity_id` -waarde hebben) en ten minste twee van deze records moeten dezelfde `created_in` -waarden hebben. Met dit, zouden de het Staging-Geplande updates niet in Commerce Admin worden getoond; u zou slechts het lege Geplande blok van Veranderingen zien.

#### Stappen om te verifiëren

1. Open de tabel met catalogi\_category\_entity in uw database.
1. Entiteiten filteren op entiteit\_id, met entiteit\_id die de desbetreffende categorie identificeert.
1. Als de waarden in de kolom created\_in gelijk zijn voor verschillende items met dezelfde entiteit\_id, is dat onze zaak. Normaal gesproken zijn de `created_in` -waarden verschillend voor elke record.

![ Beschadigde gegevens in de catalog_category_entity lijst ](assets/catalog_category_entity.png)

## Oplossing

U kunt een van de volgende oplossingen kiezen:

1. **Schrap** de problematische verslagen van de categoriesupdate
1. **Repareer** de problematische verslagen van de categorieupdate

### De updaterecords voor problematische categorieën verwijderen

In deze oplossing moet u de juiste `updated_in` waarde instellen voor de eerste categorierecord en alle andere records voor deze categorie verwijderen. Hiermee worden alle geplande rubriekupdates verwijderd.

Voer de volgende stappen uit:

1. Zoek de DB-records met de `entity_id` van de desbetreffende categorie.
1. Selecteer de record met het grootste gehele getal in de kolom `updated_in` .
1. Kopieer de `updated_in` -waarde uit de geselecteerde record.
1. Selecteer de record met `row_id` = `entity_id` (eerste categorierecord) en plak de gekopieerde waarde in de kolom `updated_in` van deze record.
1. Rijen verwijderen waarvoor `row_id` niet gelijk is aan `entity_id` .

### De problematische update-records voor categorieën repareren

1. Zoek de categorierecords met dezelfde `entity_id` en dezelfde `created_in` -waarde.
1. Selecteer de record waar `row_id` = `entity_id` en kopieer de `updated_in` -waarde.
1. Selecteer de record waarin `row_id` niet gelijk is aan `entity_id` en plak de gekopieerde `updated_in` waarde als de `created_in` waarde. Zie de onderstaande schermafbeelding als illustratie.    ![ het Kopiëren van created_in value.png ](assets/copy_created-in_value.png)
1. Controleer of de update-record voor de categorie, waarvan u de `created_in` -waarde hebt bijgewerkt (in stap 3), bestaat in de `staging_update` -tabel. *bijvoorbeeld:* ALS de gekopieerde `created_in` waarde 1509281953 is, DAN moet de entiteit met `row_id` = 1509281953 in de `staging_update` lijst bestaan.

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
