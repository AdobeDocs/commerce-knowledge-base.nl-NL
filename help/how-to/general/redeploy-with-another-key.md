---
title: 'Adobe Commerce on cloud: verificatietoetsen wijzigen en opnieuw implementeren'
description: Dit artikel bevat instructies voor het opnieuw implementeren van Adobe Commerce op cloudinfrastructuur met verschillende verificatietoetsen. U hebt bijvoorbeeld mogelijk de toetsen voor een ander account gebruikt of u hebt Magento Open Source-toetsen gebruikt in plaats van Adobe Commerce-toetsen.
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce on cloud: verificatietoetsen wijzigen en opnieuw implementeren

Dit artikel bevat instructies voor het opnieuw implementeren van Adobe Commerce op cloudinfrastructuur met verschillende verificatietoetsen. U hebt bijvoorbeeld mogelijk de toetsen voor een ander account gebruikt of u hebt Magento Open Source-toetsen gebruikt in plaats van Adobe Commerce-toetsen.

Als u de onjuiste toetsen hebt gebruikt, mislukt de implementatie. Als u wilt herstellen, moet u het project klonen, de juiste toetsen aan `auth.json` toevoegen en de wijziging doorvoeren in de hoofdvertakking.

In dit artikel, veronderstellen wij dat uw project een `master` tak slechts heeft (`master` is de standaardtak wanneer u eerst een project creeert).

Opnieuw implementeren met de juiste verificatietoetsen:

1. Meld u aan bij de computer met de Adobe Commerce op SSH-sleutels voor cloudinfrastructuur.
1. Meld u aan bij het project:

   ```
   magento-cloud login
   ```

1. Maak een vertakking om de code bij te werken met de naam `auth` :

   ```
   magento-cloud environment:branch auth master
   ```

1. Verandering in de folder van de projectwortel.
1. Open `auth.json` in een teksteditor.

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Voeg de juiste verificatietoetsen toe.
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Leg uw wijzigingen vast en voeg deze samen.

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. Wacht tot de implementatie is voltooid.

De berichten wijzen erop of de plaatsing succesvol was. U kunt een succesvolle plaatsing bevestigen door naar één van de **routes van het Milieu** te gaan die op uw scherm worden getoond.
