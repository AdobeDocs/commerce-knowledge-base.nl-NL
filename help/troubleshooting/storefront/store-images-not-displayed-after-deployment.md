---
title: Afbeeldingen opslaan die niet worden weergegeven na implementatie
description: Dit artikel biedt een oplossing voor het geval dat afbeeldingen na de implementatie niet correct worden weergegeven.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Afbeeldingen opslaan die niet worden weergegeven na implementatie

Dit artikel biedt een oplossing voor het geval dat afbeeldingen na de implementatie niet correct worden weergegeven.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Wanneer u een storefront thema met beeld resizing gebruikt, tonen de beelden niet of verdwijnen uit cataloguspagina&#39;s wanneer opgesteld.

## Oorzaak

Dit kan gebeuren als de afbeeldingen uit de cache worden geladen.

## Oplossing

Als dit gebeurt, kunt u de opdracht Magento gebruiken om de afbeeldingscache opnieuw te genereren en de afbeeldingen correct weer te geven.

Om dit uit te voeren, hebt u de informatie van SSH en opslag URL beschikbaar door de [ Console van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL) nodig.

1. SSH aan uw project dat een bron voor de [ gegevensbestandstortplaats ](/help/how-to/general/create-database-dump-on-cloud.md) was, zoals die in [ SSH aan milieu ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/secure-connections) in onze ontwikkelaarsdocumentatie wordt beschreven.
1. De afbeeldingscache opnieuw genereren door uit te voeren:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Test de categoriepagina&#39;s via de winkel-URL.
