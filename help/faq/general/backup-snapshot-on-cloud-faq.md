---
title: 'Back-up (momentopname) op Cloud: Veelgestelde vragen'
description: In dit artikel worden de basisvereisten besproken voor het maken van back-ups van uw omgevingen met momentopnamen op Adobe Commerce op cloudinfrastructuur.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '709'
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
* De automatische momentopnamen worden gecreeerd **ongeacht de levende staat** van uw plaats (de momentopnamen worden ook gecreeerd voor plaatsen die nog niet zijn gelanceerd). De automatische steunen zijn niet openbaar toegankelijk omdat zij in een afzonderlijk systeem worden opgeslagen.
U kunt [&#x200B; een kaartje van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) voorleggen om een speciale steun te verzoeken of van een specifieke steun te herstellen die de datum, de tijd, en de tijdzone in het kaartje verstrekt. Zodra het team van de Infrastructuur de momentopname heeft verstrekt, om timestamp te bepalen toen het oorspronkelijk werd genomen, stel het volgende bevel van de plaats in werking waar de momentopname is geplaatst:

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Voorbeeld-uitvoer:

  <strong> 2025-01-13 08 :42: 17.123000+00 :00</strong>


* De steun produceert geen handmomentopnamen op bestelling. Let er ook op dat met ondersteuning de database niet wordt teruggedraaid of hersteld. De momentopname wordt opgehaald, maar u moet de database zelf terugzetten.
* De automatische momentopnamen worden gecreeerd **ongeacht de levende staat** van uw plaats (de momentopnamen worden ook gecreeerd voor plaatsen die nog niet zijn gelanceerd). Automatische back-ups worden opgeslagen in een afzonderlijk systeem en zijn niet toegankelijk voor het publiek.
U kunt [&#x200B; een kaartje van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) voorleggen om een speciale steun te verzoeken of van een specifieke steun te herstellen die de datum, de tijd, en de tijdzone in het kaartje verstrekt. De steun produceert geen handmomentopnamen op bestelling.
Let er ook op dat met ondersteuning de database niet wordt teruggedraaid of hersteld. De momentopname wordt opgehaald, maar u moet de database zelf terugzetten.
* De steunen worden gecreeerd gebruikend **gecodeerde momentopnamen van het Blok van Amazon Web Services Elastic (AWS EBS)**.
* Omgevingsmomentopnamen omvatten uw volledige systeem (bestandssysteem en de database).
* De tijd van het behoud voor automatische momentopnamen **is verschillend** en volgt [&#x200B; het programma &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>De Cloud Console toont altijd [!UICONTROL No backup] in het Opvoeren en Productiemilieu&#39;s. U kunt alleen back-ups maken vanuit de integratieomgeving. Selecteer **[!UICONTROL Backup]** in het keuzemenu voor ovaal.
>
>![&#x200B; cloud_console_backup.png &#x200B;](assets/cloud_console_backup.png)

### Integratie (ontwikkeling) omgeving

* Uw [&#x200B; milieu van de Integratie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-27242) wordt **niet automatisch gesteund**, maar u kunt momentopnamen **manueel** tot stand brengen.
* U kunt handmatige momentopnamen maken voor integratieomgevingen in niet-live winkels.
* U kunt **veelvoudige momentopnamen** hebben die manueel zijn teweeggebracht.
* Een manueel teweeggebrachte momentopname wordt opgeslagen voor **7 dagen**.

**Verwante artikelen in onze ontwikkelaarsdocumentatie:**

* [&#x200B; Steun en rampenterugwinning &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [&#x200B; creeer een momentopname &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Omgevingsmomentopname, Starterplan

* Alle soorten milieu&#39;s (Integratie, het Opvoeren, Productie) **worden niet automatisch gesteund**, maar u kunt momentopnamen manueel tot stand brengen.
* U kunt handmomentopnamen **ongeacht de levende staat** van uw plaats tot stand brengen (momentopnamen die ook voor plaatsen worden gecreeerd die nog niet zijn gelanceerd).
* Een manueel teweeggebrachte momentopname wordt opgeslagen voor **7 dagen**.

## Een omgevingsmomentopname herstellen

Om een bestaande momentopname (op het gesteunde milieu te herstellen: Integratie, het Opvoeren, Productie op het Plan van de Aanzet of Integratie op Pro plan), volg de stappen in [&#x200B; Reservemanagement: Herstel een handsteun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) in onze Commerce op de Gids van de Infrastructuur van de Wolk.

## Back-up van database (DB)

Back-up van database maakt deel uit van een Cloud-momentopname:

Een momentopname is een volledige steun van een milieu dat alle blijvende gegevens van alle lopende diensten (bijvoorbeeld, **uw gegevensbestand MySQL**, Redis, etc.) en om het even welke dossiers omvat die op de opgezette volumes worden opgeslagen.

>[!NOTE]
>
>De opgezette volumes omvatten slechts/verwijzen naar de [&#x200B; beschrijfbare steunen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) en zullen niet al uw `/app` folder omvatten. Zoals voor de andere dossiers, worden zij gecreeerd/geproduceerd door [&#x200B; het bouwstijl en plaatsingsproces &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), en u zult ook de resterende dossiers van uw bewaarplaats van het Git moeten uitchecken.

[&#x200B; Momentopnamen en reservebeheer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) in onze ontwikkelaarsdocumentatie.

Verzend slechts a [&#x200B; steunverzoek &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) voor een momentopname van DB van ProProductie en het Staging als u OB van een specifiek punt in tijd nodig hebt. Als u een huidige steun van uw OB slechts (op om het even welk milieu) nodig hebt, zie het artikel van de kennisbasis: [&#x200B; produceer gegevensbestanddumps op Wolk &#x200B;](/help/how-to/general/create-database-dump-on-cloud.md).
