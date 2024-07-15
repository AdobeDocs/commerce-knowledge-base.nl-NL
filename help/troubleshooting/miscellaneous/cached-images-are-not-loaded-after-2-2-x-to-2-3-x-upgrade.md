---
title: Afbeeldingen in de cache worden niet geladen na een upgrade van 2.2.X naar 2.3.X
description: Dit artikel biedt de oplossing voor het probleem met cacheafbeeldingen die niet worden weergegeven na een upgrade van Adobe Commerce naar de cloudinfrastructuur 2.2.X naar 2.3.X.
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Afbeeldingen in de cache worden niet geladen na een upgrade van 2.2.X naar 2.3.X

Dit artikel biedt de oplossing voor het probleem met cacheafbeeldingen die niet worden weergegeven na een upgrade van Adobe Commerce naar de cloudinfrastructuur 2.2.X naar 2.3.X.

## Betrokken versies en edities:

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur 2.2.X, 2.3.X

## Probleem

Nadat Adobe Commerce is bijgewerkt van 2.2.X naar 2.3.X, zijn de productafbeeldingen in de cache niet beschikbaar en wordt in plaats daarvan een pagina van 404 weergegeven.

Het probleem wordt veroorzaakt door de onjuiste Nginx-configuratie die is ingesteld in `.magento.app.yaml` : `index.php` (of geen) wordt gebruikt voor de `"/media"` -locatie in plaats van `passthru: /get.php` .

## Oplossing

1. Controleer het `.magento.app.yaml` -configuratiebestand op de `"/media"` -locatie. De juiste configuratie ziet er als volgt uit:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Als `passthru` niet is ingesteld op `"/get.php"` en `expires` niet is ingesteld, voert u de volgende stappen uit.
1. Corrigeer het configuratiebestand.
   * Starterabonnement: corrigeer het bestand zelf en duw op de wijzigingen.
   * Pro-abonnement:
   * Integratie: corrigeer het bestand zelf en duw op de wijzigingen.
   * Het opvoeren en de Productie: verbeter het dossier zelf, duw de veranderingen, en creeer een [ de steunkaartje van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om het toe te passen te hebben.

1. Optimalisatie van snel renderen van afbeeldingen in Commerce-beheer inschakelen (eerst snel configureren), zoals beschreven in <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html> .

Als de configuratie correct is, maar u ervaart nog de kwestie, vervolg het onderzoek of contacteer [ de Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
