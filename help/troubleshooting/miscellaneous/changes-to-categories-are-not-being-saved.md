---
title: Wijzigingen in categorieën worden niet opgeslagen
description: Dit artikel bevat een oplossing voor het bijwerken van productcategorieën via Commerce Admin. De wijzigingen worden niet weergegeven op de beheerdersinterface en de winkel. Het probleem wordt veroorzaakt door de bedorven gegevens in ` catalog_category_entity lijst `. U lost het probleem op door de updaterecords voor problematische categorieën in de tabel te corrigeren of te verwijderen. Daarna kunt u de productcategorieën bijwerken met de Admin.
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Wijzigingen in categorieën worden niet opgeslagen

Dit artikel bevat een oplossing voor het bijwerken van productcategorieën via Commerce Admin. De wijzigingen worden niet weergegeven op de beheerdersinterface en de winkel. Het probleem wordt veroorzaakt door de beschadigde gegevens in het dialoogvenster `catalog_category_entity` tabel. U lost het probleem op door de updaterecords voor problematische categorieën in de tabel te corrigeren of te verwijderen. Daarna kunt u de productcategorieën bijwerken met de Admin.

## Probleem

Nadat u wijzigingen hebt aangebracht in een productcategorie in Beheer en deze hebt opgeslagen, worden de nieuwe updates niet opgeslagen en niet weergegeven in de beheerdersruimte en de opslagruimte.

### Stappen om te reproduceren

1. Ga naar **Catalogus** > **Categorieën**.
1. Selecteer een categorie.
1. Breng wijzigingen aan en klik vervolgens op **Opslaan**.
1. Het bericht wordt weergegeven: *Je hebt de rubriek opgeslagen*.
1. De wijziging die u hebt aangebracht, is niet opgeslagen.

## Mogelijke oorzaak: beschadigde gegevens in de `catalog_category_entity` table

Het probleem wordt veroorzaakt door dezelfde waarden in het dialoogvenster `created_in` kolom van de desbetreffende categorieregisters in de database (DB).

![Beschadigde gegevens in de tabel catalog_category_entity](assets/catalog_category_entity.png)

Details:

* De `catalog_category_entity` De DB-tabel bevat twee of meer records voor de desbetreffende categorie (deze records hebben dezelfde `entity_id` waarde).
* Deze categorieregisters bevatten **dezelfde waarden in de `created_in` kolom**.

### Hoe verschijnt de tweede ingang van DB (en alle volgende) in OB voor één en de zelfde categorie?

De tweede DB-record (en mogelijk de volgende record) voor de desbetreffende categorie betekent dat er categorietoewijzingen zijn gepland met de module Magento\_Staging. De module maakt een extra record voor een categorie in het dialoogvenster `catalog_category_entity` en dat is het verwachte toepassingsgedrag; het probleem is dat de verslagen de zelfde waarden voor hebben `created_in` kolom.

### Hoe worden dezelfde waarden weergegeven?

We kunnen de redenen voor gegevenscorruptie niet met zekerheid noemen. De mogelijke redenen kunnen zijn:

* aanpassingen (code, thema&#39;s, enz.)
* onjuiste gegevensmigratie
* onjuiste gegevensherstel van back-up

Voor zover wij weten is dergelijke gegevensbeschadiging niet typisch voor het &quot;schone&quot; (out-of-the-box) Adobe Commerce-exemplaar en kan deze niet worden gereproduceerd op een Adobe Commerce-installatie zonder aanpassingen.

### Hoe dit te verifiëren is uw probleem

De `catalog_category_entity` de tabel moet meerdere records voor de desbetreffende categorie bevatten (de records moeten dezelfde hebben `entity_id` waarde) en ten minste twee van deze records moeten dezelfde `created_in` waarden. Met dit, zouden de het Staging-Geplande updates niet in Commerce Admin worden getoond; u zou slechts het lege Geplande blok van Veranderingen zien.

#### Stappen om te verifiëren

1. Open de tabel met catalogi\_category\_entity in uw database.
1. Entiteiten filteren op entiteit\_id, met entiteit\_id die de desbetreffende categorie identificeert.
1. Als de waarden in de kolom created\_in gelijk zijn voor verschillende items met dezelfde entiteit\_id, is dat onze zaak. Normaal gesproken worden de `created_in` waarden zijn verschillend voor elke record.

![Beschadigde gegevens in de tabel catalog_category_entity](assets/catalog_category_entity.png)

## Oplossing

U kunt een van de volgende oplossingen kiezen:

1. **Verwijderen** de problematische categoriesupdate
1. **Repareren** de problematische categoriesupdate

### De updaterecords voor problematische categorieën verwijderen

In deze oplossing, zult u het correcte moeten plaatsen `updated_in` waarde voor de eerste categorierecord en verwijder alle andere records voor deze categorie. Hiermee worden alle geplande rubriekupdates verwijderd.

Voer de volgende stappen uit:

1. Zoek de DB-records met de `entity_id` van de betrokken categorie.
1. Selecteer de record met het grootste gehele getal in het dialoogvenster `updated_in` kolom.
1. De `updated_in` waarde uit de geselecteerde record.
1. Selecteer de record met `row_id` = `entity_id` (eerste categorierecord) en plak de gekopieerde waarde in de `updated_in` kolom van deze record.
1. Rij(en) verwijderen met `row_id` niet gelijk aan `entity_id` .

### De problematische update-records voor categorieën repareren

1. Zoeken naar rubriekrecords met dezelfde gegevens `entity_id` en `created_in` waarde.
1. Selecteer de record waar `row_id` = `entity_id` en kopieer de `updated_in` waarde.
1. Selecteer de record waar `row_id` is niet gelijk aan `entity_id` en plak de gekopieerde `updated_in` waarde als de `created_in` waarde. Zie de onderstaande schermafbeelding als illustratie.    ![created_in value.png kopiëren](assets/copy_created-in_value.png)
1. Controleer of de categorie update-record bevat. `created_in` waarvan u de waarde hebt bijgewerkt (in stap 3), bestaat in de `staging_update` tabel. *Bijvoorbeeld:* IF gekopieerd `created_in` waarde is 1509281953, EN de entiteit met `row_id` = 1509281953 moet in de `staging_update` table
