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

De kwestie wordt veroorzaakt door de onjuiste configuratie Nginx die in wordt geplaatst `.magento.app.yaml`: `index.php` (of geen) wordt gebruikt voor de `"/media"` locatie in plaats van `passthru: /get.php`.

## Oplossing

1. Controleer uw `.magento.app.yaml` configuratiebestand, in het `"/media"` locatie. De juiste configuratie ziet er als volgt uit:

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. Indien `passthru` is niet ingesteld op `"/get.php"` en `expires` niet is ingesteld, voert u de volgende stappen uit.
1. Corrigeer het configuratiebestand.
   * Starterabonnement: corrigeer het bestand zelf en duw op de wijzigingen.
   * Pro-abonnement:
   * Integratie: corrigeer het bestand zelf en duw op de wijzigingen.
   * Staging en productie: corrigeer het bestand zelf, duw de wijzigingen en maak een [Adobe Commerce-ondersteuningsticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om het toe te passen.

1. Snellere optimalisatie van afbeeldingen inschakelen in Commerce Admin (eerst snel configureren), zoals beschreven in <https://devdocs.magento.com/guides/v2.3/cloud/cdn/fastly-image-optimization.html>.

Als de configuratie correct is, maar u ervaart nog de kwestie, vervolg het onderzoek of contact [Adobe Commerce-ondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
