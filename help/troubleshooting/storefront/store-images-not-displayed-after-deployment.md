---
title: Afbeeldingen opslaan die niet worden weergegeven na implementatie
description: Dit artikel biedt een oplossing voor het geval dat afbeeldingen na de implementatie niet correct worden weergegeven.
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
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

Om dit uit te voeren, hebt u de informatie van SSH en de opslag URL beschikbaar door [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

1. SSH voor uw project dat een bron voor [databasedruk](/help/how-to/general/create-database-dump-on-cloud.md), zoals beschreven in [SSH naar omgeving](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh) in onze ontwikkelaarsdocumentatie.
1. De afbeeldingscache opnieuw genereren door uit te voeren:

   ```bash
   php bin/magento catalog:images:resize
   ```

1. Test de categoriepagina&#39;s via de winkel-URL.
