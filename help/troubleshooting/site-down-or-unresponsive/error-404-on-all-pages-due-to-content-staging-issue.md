---
title: Fout 404 op alle pagina's vanwege probleem met het opslaan van inhoud
description: Dit artikel bevat een oplossing voor het probleem met de Adobe Commerce-infrastructuur op locatie en Adobe Commerce met betrekking tot cloudinfrastructuur. Er treedt een fout van 404 op bij het openen van een winkelpagina of de [!UICONTROL Commerce Admin] .
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 48f06a90108842e00745b75db2f56a320704faf5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Fout 404 op alle pagina&#39;s vanwege probleem met het opslaan van inhoud

Dit artikel bevat een oplossing voor het probleem met de Adobe Commerce-infrastructuur op locatie en Adobe Commerce met betrekking tot cloudinfrastructuur. Er treedt een fout van 404 op bij het openen van een winkelpagina of de [!UICONTROL Commerce Admin] .

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

>[!NOTE]
>
>Dit artikel is niet op de situatie van toepassing waarin u een fout 404 wanneer het proberen om [ voorproef de het opvoeren update ](https://experienceleague.adobe.com/nl/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change) krijgt. Als u in die kwestie loopt, te openen gelieve a [ steunkaartje ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

De toegang tot van om het even welke storefront pagina of Admin resulteert in de 404 fout (de &quot;Wiops, onze slechte...&quot;pagina) na het uitvoeren van verrichtingen met geplande updates voor de activa van de opslaginhoud gebruikend [ Inhoud het Opvoeren ](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=nl-NL) (updates voor de activa van de opslaginhoud die gebruikend de [ Magento \_Staging module ](https://developer.adobe.com/commerce/php/module-reference/) worden gepland). U hebt bijvoorbeeld een product met een geplande update verwijderd of de einddatum voor de geplande update verwijderd.

Een opslaginhoudselement bevat:

* Product
* Categorie
* Catalogusprijsregel
* Regel voor winkelprijs
* CMS-pagina
* CMS Block
* Widget

Sommige scenario&#39;s worden besproken in de hieronder sectie van de Oorzaak.

## Oorzaak

De `flag` -tabel in de database (DB) bevat ongeldige koppelingen naar de `staging_update` -tabel.

Het probleem heeft te maken met het opslaan van inhoud. Hieronder volgen twee specifieke scenario&#39;s. Houd er rekening mee dat er wellicht meer situaties zijn die de kwestie veroorzaken.

**Scenario 1:** het schrappen van een activa van de opslaginhoud die:

* heeft een update gepland met Inhoud het Staging
* de update heeft een einddatum (de vervaldatum waarna het bijgewerkte element terugkeert naar de vorige versie)
* de einddatum van de update in het verleden ligt

Het is mogelijk dat de uitgave niet optreedt als een verwijderd element geen einddatum heeft voor de geplande update.

**Scenario 2:** Verwijderend de einddatum/tijd van een geplande update.

### Identificeer als uw kwestie verwant is

Voer de volgende DB-query uit om te bepalen of het probleem dat u ondervindt het probleem is dat in dit artikel wordt beschreven:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Als de vraag een lijst terugkeert waar `update_exists` waarde &quot;0&quot;is, dan bestaat een ongeldige verbinding aan de `staging_update` lijst in uw gegevensbestand, en de stappen die in de [ sectie van de Oplossing ](#solution) worden beschreven zullen helpen om de kwestie op te lossen. Hieronder ziet u een voorbeeld van het queryresultaat met `update_exists` -waarde gelijk aan &quot;0&quot;:

![ update_exists_0.png ](assets/update_exists_0.png)

Als de query een tabel retourneert waarvan de `update_exists` -waarde &quot;1&quot; of een leeg resultaat is, betekent dit dat uw uitgave niet gerelateerd is aan het uitvoeren van testupdates. Hieronder ziet u een voorbeeld van het queryresultaat met `update_exists` -waarde gelijk aan &quot;1&quot;:

![ updates_exist_1.png ](assets/updates_exist_1.png)

In dit geval, zou u naar de [ Plaats neer Troubleshooter ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27152) voor het oplossen van problemenideeën kunnen verwijzen.

## Oplossing

1. Voer de volgende query uit om de ongeldige koppeling naar de tabel `staging_update` te verwijderen:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Wacht tot de [!DNL cron] -taak is uitgevoerd (kan maximaal vijf minuten worden uitgevoerd als de instelling correct is ingesteld) of voer de taak handmatig uit als u [!DNL cron] niet hebt ingesteld.

Het probleem moet direct worden opgelost nadat de ongeldige koppeling is hersteld. Als het probleem voortduurt, [ voorlegt een steunkaartje ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
