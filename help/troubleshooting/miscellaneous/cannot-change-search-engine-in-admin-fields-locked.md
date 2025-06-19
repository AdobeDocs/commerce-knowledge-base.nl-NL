---
title: Kan zoekmachine niet wijzigen in "app/etc/env.php"
description: Dit artikel biedt een oplossing voor het probleem waarbij u het zoekprogramma probeert te wijzigen in Commerce Admin, maar de velden zijn vergrendeld.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Kan zoekengine niet wijzigen in `app/etc/env.php`

Dit artikel biedt een oplossing voor het probleem waarbij u probeert de configuratie van de zoekmachine uit het `app/etc/env.php` -bestand te verwijderen, maar na de herimplementatie wordt de configuratie teruggezet naar de vorige instelling of wordt deze standaard gewijzigd in [!DNL OpenSearch] .

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

U probeert het zoekprogramma te wijzigen in Commerce Admin, maar de velden zijn vergrendeld.

## Oorzaak

De configuratie van de zoekmachine is vergrendeld in het `app/etc/env.php` -bestand of de zoekmachine is expliciet gedefinieerd in het `.magento.env.yaml` -bestand.

## Oplossing

1. Controleer het `.magento.env.yaml` -bestand in het werkgebied Implementeren en controleer of de `SEARCH_CONFIGURATION` -variabele is geconfigureerd. Voorbeeld:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Is de variabele `SEARCH_CONFIGURATION` aanwezig? Als dit niet het geval is, is de configuratie van de zoekmachine standaard vergrendeld op [!DNL OpenSearch] . Als u de configuratie wilt wijzigen, moet u de variabele aan het `.magento.env.yaml` -bestand toevoegen met de juiste waarde voor de zoekfunctie. Als de variabele `SEARCH_CONFIGURATION` aanwezig is en u de engine wilt wijzigen, vervangt u de bestaande waarde voor de engine in `.magento.env.yaml` . Mogelijke/bekende waarden: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] en [!DNL amasty_elastic_opensearch] .
1. Implementeer de instantie opnieuw.
1. Het veld Zoekmachine in Beheer blijft vergrendeld, maar wordt bijgewerkt met de waarde die u hebt opgegeven.

## Gerelateerde lezing

* [ Vergrendelde (grijs uit) gebieden in Commerce Admin ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26879) in Commerce op de Gids van de Infrastructuur van de Wolk.
