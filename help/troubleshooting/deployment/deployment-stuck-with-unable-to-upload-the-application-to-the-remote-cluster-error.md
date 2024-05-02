---
title: Implementatie is vastgelopen met de fout "Kan de toepassing niet uploaden naar de externe cluster"
description: 'Dit artikel biedt een oplossing voor het Adobe Commerce-probleem, waarbij de implementatie vastloopt en het volgende foutbericht kan worden gevonden in het implementatielogboek: *"Fout: kan de toepassing niet uploaden naar de externe cluster"*.'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Implementatie is vastgelopen met de fout &quot;Kan de toepassing niet uploaden naar de externe cluster&quot;

Dit artikel verstrekt een oplossing voor de kwestie van Adobe Commerce, waar de plaatsing geplakt wordt, en het volgende foutenbericht kan in het opstellen logboek worden gevonden: *&quot;Fout: kan de toepassing niet uploaden naar de externe cluster&quot;*.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u>Stappen om te reproduceren</u>:

Trigger plaatsing manueel of door een fusie, duw, of synchronisatie van uw milieu uit te voeren.

<u>Verwacht resultaat</u>:

De implementatie is voltooid.

<u>Werkelijk resultaat</u>:

De implementatie blijft vastzitten, en in het logboek van de plaatsingsfout in wolk UI, wordt het volgende foutenbericht getoond: *&quot;Fout: kan de toepassing niet uploaden naar de externe cluster&quot; gevonden in implementatielogboek na mislukte implementatie, geeft de site mogelijk de fout &quot;503 eerste byte timeout&quot; weer*.

## Oorzaak

Het probleem wordt veroorzaakt door het uitvallen van de beschikbare opslagruimte.

## Oplossing

U kunt overwegen de logboekfolders en/of het verhogen van schijfruimte te reinigen.

Mappen die in aanmerking komen voor opruiming:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Ga voor meer informatie over hoe u schijfruimte kunt vergroten als u op de Adobe Commerce werkt op de Starter-architectuur van de cloud-infrastructuur naar [Schijfruimte vergroten voor integratieomgeving in de cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) in onze kennisbasis voor ondersteuning. Dezelfde instructies kunnen worden gebruikt voor het vergroten van de ruimte van de Adobe Commerce in de omgeving voor integratie van de architectuur van de cloudinfrastructuur van de Pro-cloudinfrastructuur. Voor Pro Productie/Staging moet u [een ticket naar Adobe Commerce-ondersteuning indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) en vraag meer schijfruimte. Maar doorgaans hoeft u dit niet te doen met betrekking tot de ophaling/productie van het Pro-plan, aangezien Adobe Commerce deze parameters voor u controleert en waarschuwingen geeft en/of acties uitvoert volgens het contract.
