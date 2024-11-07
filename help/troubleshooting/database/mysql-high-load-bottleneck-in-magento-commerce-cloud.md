---
title: MySQL-knelpunt voor hoge belasting in Adobe Commerce op cloudinfrastructuur
description: Dit onderwerp bespreekt een oplossing wanneer de hoge lading van MySQL een prestatiesknelpunt in Adobe Commerce op wolkeninfrastructuur veroorzaakt.
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
* De dienst van New Relic APM (**Uw Adobe Commerce op de rekening van de wolkeninfrastructuur omvat de software voor de dienst van New Relic APM** samen met een vergunningssleutel.)

Voor meer informatie over de dienst van New Relic APM en zijn opstelling met uw Adobe Commerce op de rekening van de wolkeninfrastructuur, ga naar [ de Diensten van New Relic ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service) en [ Inleiding aan New Relic APM ](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/).

## Probleem

<u> stappen om te zien of beïnvloedt de kwestie u </u>

1. Controleer in uw New Relic APM Overview Chart de eerste aanwijzing dat MySQL een knelpunt is geworden. Bekijk de voorbeeldafbeelding hieronder waar MySQL een knelpunt is geworden en de meeste tijd van webtransacties in beslag neemt:

   ![ KB-372_image002.png ](assets/KB-372_image002.png)

   U ziet hoe de rode onderbroken lijn in de afbeelding een waarneembare opwaartse trend in de tijd van de MySQL-webtransacties laat zien en vervolgens op nog hogere niveaus piekt.
1. Van hier kunt u dan naar het uw **1} scherm van het Gegevensbestand {gaan waar u de tweede aanwijzing van hoge productie of langzame `SELECT` vragen in MySQL kunt zien, en in het hieronder steekproefbeeld kunt u zien wanneer het sorteren door** Meest tijdrovend **, uw opslag, in dit voorbeeld, is langzaam op `SELECT` vragen MySQL.**

   ![ KB-372_image003_BlurredExtension.png ](assets/KB-372_image003_BlurredExtension.png)

Analyseer de trage transacties in New Relic APM. Als u een hoog volume van vragen of hoge druk op een gegevensbestand MySQL ziet, kunt u de lading over verschillende knopen verspreiden door `SLAVE` verbindingen toe te laten.

## Oorzaak

Uw Adobe Commerce on cloud Infrastructure Store heeft een hoge doorvoer of is traag bij `SELECT` MySQL-query&#39;s.

## Oplossing

>[!WARNING]
>
>Voor geschaalde architectuur (gespleten architectuur), ZOU de slave verbindingen van Redis **NIET** moeten worden toegelaten. U kunt controleren of u op geschaalde architectuur bent door naar uw project-URL te gaan, bijvoorbeeld `https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>` . Klik op **[!UICONTROL SSH]** . Als er meer dan drie knopen zijn, bent u op geschraapte architectuur. Als u Redis slave Reads inschakelt op geschaalde architectuur, ontvangt de klant fouten op Redis-verbindingen die geen verbinding kunnen maken. Dit heeft te maken met de manier waarop de clusters zijn geconfigureerd om Redis-verbindingen te verwerken. Redis Slaves is nog steeds actief, maar wordt niet gebruikt voor Redis Reads. Wij adviseren voor geschaalde architectuur om Adobe Commerce 2.3.5 of later te gebruiken en nieuwe Redis achterste-eindconfiguratie uit te voeren en L2 caching voor Redis uit te voeren.

Als u deze twee indicaties ervaart en `SLAVE` -verbindingen inschakelt voor de MySQL-database en Redis, kunt u de laadbewerking verspreiden over verschillende knooppunten.

Adobe Commerce kan meerdere databases of Redis asynchroon lezen. Het bijwerken van het `.magento.env.yaml` dossier door aan `true` de waarden `MYSQL_USE_SLAVE_CONNECTION` en `REDIS_USE_SLAVE_CONNECTION` te plaatsen om a **read-only** verbinding aan het gegevensbestand te gebruiken om read-only verkeer op een niet hoofdknoop te ontvangen. Dit verbetert prestaties door lading het in evenwicht brengen omdat slechts één knoop read-write verkeer moet behandelen. Stel in op `false` om een bestaande alleen-lezen-verbindingsarray uit het `env.php` -bestand te verwijderen.

### Stappen

1. Bewerk het `.magento.env.yaml` -bestand en voeg de volgende inhoud toe:

   ![ KB-372_image004.png ](assets/KB-372_image004.png)

   U kunt meer details in [ vinden stelt Variabelen in DevDocs ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) op.

1. Leg de wijzigingen vast en duw op de wijzigingen.
1. Het duwen van veranderingen zal een nieuw plaatsingsproces in werking stellen. Nadat de implementatie is voltooid, moet de Adobe Commerce op de cloudinframinstallatie nu zijn geconfigureerd voor gebruik van slave-verbindingen.

## Veelvoorkomende vragen

Hieronder volgen de veelgestelde vragen die u kunt stellen wanneer u overweegt de functionaliteit voor slave-verbindingen te gebruiken voor uw Adobe Commerce in de cloud-infrastructuurwinkel.

* Zijn er bekende problemen of beperkingen bij het gebruik van slave-verbindingen? **wij hebben geen bekende kwesties van het gebruiken van de Verbindingen van de slave. Zorg gewoon dat u het meest recente bijgewerkte pakket met gereedschappen gebruikt. De instructies zijn hier op [ hoe te om uw kind-hulpmiddelen pakket ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) bij te werken.**
* Is er een extra latentie door de Verbindingen van de Slave te gebruiken? *ja, dwars-AZ (cross-Availability Zones) latentie is hoger en vermindert prestaties van een Adobe Commerce op de instantie van de wolkeninfrastructuur in het geval als de instantie niet overbelast is en de volledige lading kan dragen. Maar duidelijk, als de instantie wordt overbelast - master-slave zal met prestaties helpen door de lading op het Gegevensbestand MySQL of Redis over verschillende knopen te spreiden.*

  **op niet-overbelaste clusters** - **de Verbindingen van de Slave zullen prestaties door 10-15%** vertragen, die één van de redenen is het niet gebrek.

  *maar op overbelaste clusters, is er een prestatiesverhoging omdat deze 10-15% door lading door verkeer te verminderen worden verlicht.*
* Moet ik deze instellingen voor mijn winkel inschakelen? *als u hoge lading hebt of hoge lading op het Gegevensbestand MySQL of Redis verwacht, moet u zeker de Verbindingen van de Slave toelaten. Voor een regelmatige klant met gemiddeld verkeer, is dit **niet**het optimale plaatsen om worden toegelaten.*

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ stelt variabelen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy) op.
* [ de facultatieve opstellings gegevensbestandreplicatie ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication).
* [ knoop-hulpmiddelen pakket ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview).

>[!NOTE]
>
>We zijn ons ervan bewust dat dit artikel mogelijk nog steeds standaardsoftwaretermen bevat die sommigen racistisch, seksistisch of onderdrukkend vinden en die de lezer kunnen doen voelen gekwetst, getraumatiseerd of onwelkom. Adobe werkt eraan deze termen te verwijderen uit onze code, documentatie en gebruikerservaring.
