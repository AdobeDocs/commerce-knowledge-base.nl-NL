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

Dit artikel verstrekt een oplossing voor de kwestie van Adobe Commerce, waar de plaatsing geplakt wordt, en het volgende foutenbericht kan in het opstellen logboek worden gevonden: *&quot;Fout: Onbekwaam om de toepassing aan de verre cluster&quot;te uploaden*.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u> Stappen om </u> te reproduceren:

Trigger plaatsing manueel of door een fusie, duw, of synchronisatie van uw milieu uit te voeren.

<u> Verwacht resultaat </u>:

De implementatie is voltooid.

<u> Werkelijk resultaat </u>:

De plaatsing wordt geplakt, en in het login van de plaatsingsfout in wolk UI, wordt het volgende foutenbericht getoond: *&quot;Fout: kan niet de toepassing aan de verre cluster&quot;uploaden die in plaatsingslogboek na ontbroken plaatsing wordt gevonden, kan de plaats fout &quot;503 eerste byteonderbreking&quot;tonen*.

## Oorzaak

Het probleem wordt veroorzaakt door het uitvallen van de beschikbare opslagruimte.

## Oplossing

U kunt overwegen de logboekfolders en/of het verhogen van schijfruimte te reinigen.

Mappen die in aanmerking komen voor opruiming:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Voor details op hoe te om schijfruimte te verhogen als u op Adobe Commerce op het planarchitectuur van de Aanzet van de wolkeninfrastructuur bent, zie [ de schijfruimte van de Verhoging voor het milieu van de Integratie op wolk ](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) in onze basis van de steunkennis. Dezelfde instructies kunnen worden gebruikt voor het vergroten van de ruimte van de Adobe Commerce in de omgeving voor integratie van de architectuur van de cloudinfrastructuur van de Pro-cloudinfrastructuur. Voor ProProductie/het Staging, moet u een kaartje aan de Steun van Adobe Commerce [&#128279;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) dossier  en verzoek verhoogde schijfruimte. Maar doorgaans hoeft u dit niet te doen met betrekking tot de ophaling/productie van het Pro-plan, aangezien Adobe Commerce deze parameters voor u controleert en waarschuwingen geeft en/of acties uitvoert volgens het contract.
