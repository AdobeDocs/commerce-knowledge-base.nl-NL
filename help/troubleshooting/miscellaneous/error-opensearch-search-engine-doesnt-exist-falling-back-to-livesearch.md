---
title: Fout [!DNL opensearch] zoekmachine bestaat niet. Terugvallen op [!DNL livesearch].
description: Dit artikel biedt een oplossing voor het probleem waarbij de fout optreedt. [!DNL opensearch] zoekmachine bestaat niet. Terugvallen op [!DNL livesearch].", in Adobe Commerce op cloudinfrastructuur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fout [!DNL opensearch] zoekmachine bestaat niet. Terugvallen op [!DNL livesearch].

Dit artikel biedt een oplossing voor het probleem waarbij de fout optreedt: *Fout: [!DNL opensearch] zoekmachine bestaat niet. Terugvallen op [!DNL livesearch].* in Adobe Commerce over cloudinfrastructuur waar [!DNL Live Search] wordt gebruikt.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies
* [!DNL Live Search] geïnstalleerd en in gebruik

## Probleem

Het volgende bericht wordt weergegeven in de logbestanden (en kan worden waargenomen in [!DNL New Relic]):
*Fout: [!DNL opensearch] zoekmachine bestaat niet. Terugvallen op [!DNL livesearch].*

## Oplossing

1. Wijzig de `.magento.env.yaml` bestand.
1. Zoek de volgende regels:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Als u deze regels niet hebt, voegt u deze toe aan de `.magento.env.yaml` bestand.
1. Indien deze regels bestaan, **de motor wijzigen** van *[!DNL opensearch]* tot *[!DNL livesearch]*.
1. Leg de wijziging vast en implementeer deze opnieuw.

## Gerelateerde lezing

* [Installeren [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) in onze gids Live zoeken
