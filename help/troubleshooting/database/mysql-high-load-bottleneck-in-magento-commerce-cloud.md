---
title: MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur
description: Dit onderwerp bespreekt een oplossing wanneer de hoge lading van MySQL een prestatiesknelpunt in Adobe Commerce op wolkeninfrastructuur veroorzaakt.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 075f55b94202f75839abd25bd47824eeb5226485
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur

Dit onderwerp bespreekt een oplossing wanneer de hoge lading van MySQL een prestatiesknelpunt in Adobe Commerce op wolkeninfrastructuur veroorzaakt.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure 2.x.x, Pro accounts.

### Vereisten

* ECE Tools versie 2002.0.16 en hoger
* New Relic APM-service (**Uw Adobe Commerce on cloud Infrastructure-account bevat de software voor de New Relic APM-service** samen met een licentiecode.)

Ga voor meer informatie over de New Relic APM-service en de installatie ervan met uw Adobe Commerce op een cloud-infrastructuuraccount naar [New Relic Services](https://devdocs.magento.com/guides/v2.3/cloud/project/new-relic.html) en [Inleiding tot New Relic APM](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Probleem

<u>Stappen om te zien of beïnvloedt de kwestie u</u>

1. Controleer in uw New Relic APM Overview Chart de eerste aanwijzing dat MySQL een knelpunt is geworden. Bekijk de voorbeeldafbeelding hieronder waar MySQL een knelpunt is geworden en de meeste tijd van webtransacties in beslag neemt:

   ![KB-372_image002.png](assets/KB-372_image002.png)

   U ziet hoe de rode onderbroken lijn in de afbeelding een waarneembare opwaartse trend in de tijd van de MySQL-webtransacties laat zien en vervolgens op nog hogere niveaus piekt.
1. Vanaf hier kun je naar je **Database** scherm waar u de tweede aanwijzing van hoge productie of langzaam kunt zien `SELECT` query&#39;s in MySQL en in de onderstaande voorbeeldafbeelding kunt u zien wanneer u sorteert op **Meest tijdrovend** in dit voorbeeld is de winkel traag `SELECT` MySQL-query&#39;s.

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

Analyseer de trage transacties in New Relic APM. Als u een hoog volume van vragen of hoge druk op een gegevensbestand MySQL ziet, kunt u de lading over verschillende knopen verspreiden door toe te laten `SLAVE` verbindingen.

## Oorzaak

Uw Adobe Commerce on cloud Infrastructure Store heeft hoge doorvoer of is langzaam `SELECT` MySQL-query&#39;s.

## Oplossing

>[!WARNING]
>
>Voor geschaalde architectuur (gesplitste architectuur), Redis slave-verbindingen **NIET** worden ingeschakeld. U kunt controleren of u op geschaalde architectuur bent door naar uw project-URL te gaan, bijvoorbeeld `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`. Klikken op **[!UICONTROL SSH]**. Als er meer dan drie knopen zijn, bent u op geschraapte architectuur. Als u Redis slave Reads inschakelt op geschaalde architectuur, ontvangt de klant fouten op Redis-verbindingen die geen verbinding kunnen maken. Dit heeft te maken met de manier waarop de clusters zijn geconfigureerd om Redis-verbindingen te verwerken. Redis Slaves is nog steeds actief, maar wordt niet gebruikt voor Redis Reads. Wij adviseren voor geschaalde architectuur om Adobe Commerce 2.3.5 of later te gebruiken en nieuwe Redis achterste-eindconfiguratie uit te voeren en L2 caching voor Redis uit te voeren.

Als deze twee indicaties zich voordoen, kan `SLAVE` De verbindingen voor het MySQL gegevensbestand en Redis kunnen helpen om lading over verschillende knopen uit te spreiden.

Adobe Commerce kan meerdere databases of Redis asynchroon lezen. De `.magento.env.yaml` bestand door in te stellen op `true` de waarden `MYSQL_USE_SLAVE_CONNECTION` en `REDIS_USE_SLAVE_CONNECTION` om een **alleen-lezen** verbinding met het gegevensbestand om read-only verkeer op een niet hoofdknoop te ontvangen. Dit verbetert prestaties door lading het in evenwicht brengen omdat slechts één knoop read-write verkeer moet behandelen. Instellen op `false` om een bestaande alleen-lezen-verbindingsarray te verwijderen uit de `env.php` bestand.

### Stappen

1. Bewerk uw `.magento.env.yaml` en voeg de volgende inhoud toe:

   ![KB-372_image004.png](assets/KB-372_image004.png)

   Meer informatie vindt u in [Variabelen implementeren in DevDocs](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection).

1. Leg de wijzigingen vast en duw op de wijzigingen.
1. Het duwen van veranderingen zal een nieuw plaatsingsproces in werking stellen. Nadat de implementatie is voltooid, moet de Adobe Commerce op de cloudinframinstallatie nu zijn geconfigureerd voor gebruik van slave-verbindingen.

## Veelvoorkomende vragen

Hieronder volgen de veelgestelde vragen die u kunt stellen wanneer u overweegt de functionaliteit voor slave-verbindingen te gebruiken voor uw Adobe Commerce in de cloud-infrastructuurwinkel.

* Zijn er bekende problemen of beperkingen bij het gebruik van slave-verbindingen? **Er zijn geen bekende problemen met het gebruik van slave-verbindingen. Zorg gewoon dat u het meest recente bijgewerkte pakket met gereedschappen gebruikt. Hier vindt u instructies [hoe u het pakket met gereedschappen voor Griekenland bijwerkt](https://devdocs.magento.com/cloud/project/ece-tools-update.html).**
* Is er een extra latentie door de Verbindingen van de Slave te gebruiken? *Ja, cross-AZ (cross-Availability Zones) latentie is hoger en vermindert de prestaties van een Adobe Commerce op een cloudinframinstantie in het geval dat de instantie niet overbelast is en de volledige lading kan dragen. Maar duidelijk, als de instantie overbelast is - master-slave zal met prestaties helpen door de lading op het Gegevensbestand MySQL of Redis over verschillende knopen te spreiden.*

  **Bij niet-overbelaste clusters** -  **Slave Connections vertraagt de prestaties met 10-15%**, wat een van de redenen is waarom het niet standaard is.

  *Maar bij overbelaste clusters is er een prestatieverhoging omdat deze 10-15% worden beperkt door de belasting van het verkeer te verminderen.*
* Moet ik deze instellingen voor mijn winkel inschakelen? *Als u hoge lading hebt of hoge lading op het Gegevensbestand MySQL of Redis verwacht, moet u zeker de Verbindingen van de Slave toelaten. Voor een regelmatige klant met gemiddeld verkeer, is dit **niet**een optimale instelling die moet worden ingeschakeld.*

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Variabelen implementeren](https://devdocs.magento.com/cloud/env/variables-deploy.html).
* [Optionele databasereplicatie instellen](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master_slavedb.html).
* [ece-tools-pakket](https://devdocs.magento.com/cloud/reference/ece-tools-reference.html).

>[!NOTE]
>
>We zijn ons ervan bewust dat dit artikel mogelijk nog steeds standaardsoftwaretermen bevat die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen doen voelen gekwetst, getraumatiseerd of onwelkom. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.
