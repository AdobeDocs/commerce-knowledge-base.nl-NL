---
title: 'Back-up (momentopname) op Cloud: Veelgestelde vragen'
description: In dit artikel worden de basisvereisten besproken voor het maken van back-ups van uw omgevingen met momentopnamen op Adobe Commerce op cloudinfrastructuur.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 0958a8923e27c1341f4b536812b26205685b2b81
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Back-up (momentopname) op Cloud: Veelgestelde vragen

Dit artikel behandelt het maken van back-ups van uw omgevingen met momentopnamen op Adobe Commerce op cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur 2.4.x
* Architectuurplannen: Starter, Pro Legacy, Pro

## Omgevingsmomentopname, Pro-plan

### Staging- en productieomgevingen

* Handmatige momentopnamen zijn niet beschikbaar voor staging- en productieomgevingen op Pro-plan.
* Automatische momentopnamen worden gemaakt **ongeacht de live status** van uw site (momentopnamen die ook zijn gemaakt voor sites die nog niet zijn gestart). De automatische steunen zijn niet openbaar toegankelijk omdat zij in een afzonderlijk systeem worden opgeslagen. U kunt [een Adobe Commerce-ondersteuningsticket verzenden](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) om een speciale steun te verzoeken of van een specifieke steun te herstellen die de datum, de tijd, en de tijdzone in het kaartje verstrekt. Let er ook op dat met ondersteuning de database niet wordt teruggedraaid of hersteld. De momentopname wordt opgehaald, maar u moet de database zelf terugzetten.
* De back-ups worden gemaakt met de **momentopnamen van de gecodeerde Amazon Web Services Elastic Block Store (AWS EBS)**.
* Omgevingsmomentopnamen omvatten uw volledige systeem (bestandssysteem en de database).
* Retentietijd voor automatische momentopnamen **is verschillend** en volgt [het schema](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>De Cloud Console toont altijd [!UICONTROL No backup] in een afbouw- en productieomgeving. U kunt alleen back-ups maken vanuit de integratieomgeving. Selecteren **[!UICONTROL Backup]** in het keuzemenu voor ovaal.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Integratie (ontwikkeling) omgeving

* Uw [Integratieomgeving](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) is **wordt niet automatisch reservekopie gemaakt**, maar u kunt momentopnamen maken **handmatig**.
* U kunt handmatige momentopnamen maken voor integratieomgevingen in niet-live winkels.
* U kunt **meerdere momentopnamen** die handmatig zijn geactiveerd.
* Een handmatig geactiveerde momentopname wordt opgeslagen voor **7 dagen**.

**Verwante artikelen in onze ontwikkelaarsdocumentatie:**

* [Back-up en noodherstel](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Een opname maken](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Omgevingsmomentopname, Starterplan

* Alle soorten milieu&#39;s (Integratie, het Opvoeren, Productie) **wordt niet automatisch een back-up gemaakt**, maar u kunt momentopnamen handmatig maken.
* U kunt handmatige momentopnamen maken **ongeacht de live status** van uw site (momentopnamen die ook zijn gemaakt voor sites die nog niet zijn gestart).
* Een handmatig geactiveerde momentopname wordt opgeslagen voor **7 dagen**.

## Een omgevingsmomentopname herstellen

Om een bestaande momentopname (op het gesteunde milieu te herstellen: Integratie, het Staging, Productie op het Plan van de Aanzet of Integratie op Pro plan), volg de stappen in [Back-upbeheer: een handmatige back-up herstellen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) in onze Commerce on Cloud Infrastructure Guide.

## Back-up van database (DB)

Back-up van database maakt deel uit van een Cloud-momentopname:

>>
Een momentopname is een volledige steun van een milieu dat alle blijvende gegevens van alle lopende diensten omvat (bijvoorbeeld **uw MySQL-database**, Redis, enzovoort) en bestanden die zijn opgeslagen op de gekoppelde volumes.

>[!NOTE]
>
>De gemonteerde volumes omvatten uitsluitend/verwijzen naar de [beschrijfbare montage](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) en bevat niet al uw map /app. De andere bestanden worden gemaakt/gegenereerd door [het ontwikkelings- en implementatieproces](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow)en u moet ook de resterende bestanden uitchecken in uw Git-opslagplaats.

[Momentopnamen en back-upbeheer](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) in onze ontwikkelaarsdocumentatie.

Alleen een [supportverzoek](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) voor een momentopname van DB van ProProductie en het Staging als u OB van een specifiek punt in tijd nodig hebt. Als u een huidige steun van uw OB slechts (op om het even welk milieu) nodig hebt, zie het kennisbankartikel: [Databasedumpen genereren op cloud](/help/how-to/general/create-database-dump-on-cloud.md).
