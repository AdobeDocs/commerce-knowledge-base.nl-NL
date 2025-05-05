---
title: De onderzoekmachine van de fout  [!DNL opensearch]  bestaat niet. Bezig met terugvallen naar  [!DNL livesearch] .
description: Dit artikel verstrekt een oplossing aan de kwestie waar u de fout ziet, &grave; fout -  [!DNL opensearch]  onderzoeksmotor bestaat niet. Terugvallen naar  [!DNL livesearch].&grave;, in Adobe Commerce op wolkeninfrastructuur.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Fout [!DNL opensearch] zoekmachine bestaat niet. Terugvallen naar [!DNL livesearch] .

Dit artikel biedt een oplossing voor het probleem waarbij de fout optreedt: *Fout: [!DNL opensearch] zoekengine bestaat niet. Terugvallen naar [!DNL livesearch] .* in Adobe Commerce op cloudinfrastructuur waar [!DNL Live Search] wordt gebruikt.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies
* [!DNL Live Search] is geïnstalleerd en in gebruik

## Probleem

Het volgende bericht wordt weergegeven in de logboeken (en kan worden waargenomen in [!DNL New Relic] ):
*Fout: [!DNL opensearch] zoekmachine bestaat niet. Terugvallen naar [!DNL livesearch].*

## Oplossing

1. Wijzig het `.magento.env.yaml` bestand.
1. Zoek de volgende regels:

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Als u deze regels niet hebt, voegt u ze toe aan het `.magento.env.yaml` -bestand.
1. Als deze lijnen bestaan, **wijzigt de motor** van *[!DNL opensearch]* aan *[!DNL livesearch]*.
1. Leg de wijziging vast en implementeer deze opnieuw.

## Gerelateerde lezing

* [ installeer  [!DNL Live Search] ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=nl-NL) in onze Levende Gids van het Onderzoek
