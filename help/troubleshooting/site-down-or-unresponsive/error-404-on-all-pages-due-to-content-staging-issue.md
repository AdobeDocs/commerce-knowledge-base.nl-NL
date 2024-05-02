---
title: Fout 404 op alle pagina's vanwege probleem met het opslaan van inhoud
description: Dit artikel bevat een oplossing voor het probleem met de Adobe Commerce-infrastructuur op locatie en Adobe Commerce met betrekking tot de cloud-infrastructuur. Er is een fout van 404 opgetreden bij het openen van een winkelpagina of Commerce Admin.
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Fout 404 op alle pagina&#39;s vanwege probleem met het opslaan van inhoud

Dit artikel bevat een oplossing voor het probleem met de Adobe Commerce-infrastructuur op locatie en Adobe Commerce met betrekking tot de cloud-infrastructuur. Er is een fout van 404 opgetreden bij het openen van een winkelpagina of Commerce Admin.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

>[!NOTE]
>
>Dit artikel is niet van toepassing op de situatie waarin u een fout van 404 krijgt wanneer u probeert om [voorvertoning van de gefaseerde update](https://docs.magento.com/user-guide/cms/content-staging-scheduled-update.html#preview-the-scheduled-change). Als u dat probleem hebt opgelost, opent u een [ondersteuningsticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

Als u een winkelpagina of de beheerderspagina opent, treedt de fout van 404 op (de pagina &quot;Wiops, our bad...&quot;) nadat u bewerkingen hebt uitgevoerd met geplande updates voor elementen van opslaginhoud met behulp van [Inhoud stapelen](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (updates voor elementen voor opslaginhoud die zijn gepland via de [Magento\_Staging, module](https://developer.adobe.com/commerce/php/module-reference/)). U hebt bijvoorbeeld een product met een geplande update verwijderd of de einddatum voor de geplande update verwijderd.

Een opslaginhoudselement bevat:

* Product
* Categorie
* Catalogusprijsregel
* Regel voor winkelprijs
* CMS-pagina
* CMS-blok
* Widget

Sommige scenario&#39;s worden besproken in de hieronder sectie van de Oorzaak.

## Oorzaak

De `flag` de tabel in de database (DB) bevat ongeldige koppelingen naar de `staging_update` tabel.

Het probleem heeft te maken met het opslaan van inhoud. Hieronder volgen twee specifieke scenario&#39;s. Houd er rekening mee dat er wellicht meer situaties zijn die de kwestie veroorzaken.

**Scenario 1** Een opslaginhoudselement verwijderen dat:

* heeft een update gepland met Inhoud het Staging
* de update heeft een einddatum (de vervaldatum waarna het bijgewerkte element terugkeert naar de vorige versie)
* de einddatum van de update in het verleden ligt

Het is mogelijk dat de uitgave niet optreedt als een verwijderd element geen einddatum heeft voor de geplande update.

**Scenario 2** De einddatum/tijd van een geplande update verwijderen.

### Identificeer als uw kwestie verwant is

Voer de volgende DB-query uit om te bepalen of het probleem dat u ondervindt het probleem is dat in dit artikel wordt beschreven:

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Als de vraag een lijst terugkeert waar `update_exists` waarde is &quot;0&quot;, dan een ongeldige koppeling naar de `staging_update` de tabel bestaat in uw database en de stappen worden beschreven in de [Sectie Oplossing](#solution) zal helpen het probleem op te lossen. Hier volgt een voorbeeld van het queryresultaat met `update_exists` waarde gelijk aan 0:

![update_exists_0.png](assets/update_exists_0.png)

Als de vraag een lijst terugkeert waar `update_exists` waarde is &quot;1&quot; of een leeg resultaat; dit betekent dat uw uitgave niet gerelateerd is aan het uitvoeren van een testupdate. Hier volgt een voorbeeld van het queryresultaat met `update_exists` waarde gelijk aan &quot;1&quot;:

![updates_exist_1.png](assets/updates_exist_1.png)

In dit geval kunt u verwijzen naar de [Problemen met site-onderaan oplossen](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) voor het oplossen van problemenideeën.

## Oplossing

1. Voer de volgende query uit om de ongeldige koppeling naar de `staging_update` tabel:

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Wacht tot de uitsnijdtaak is uitgevoerd (kan maximaal vijf minuten worden uitgevoerd als de functie correct is ingesteld) of voer de taak handmatig uit als u de uitsnijdbewerking niet hebt ingesteld.

Het probleem moet direct worden opgelost nadat de ongeldige koppeling is hersteld. Als het probleem zich blijft voordoen, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
