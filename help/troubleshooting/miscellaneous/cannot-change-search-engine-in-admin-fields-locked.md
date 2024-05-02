---
title: Kan zoekmachine niet wijzigen in "app/etc/env.php"
description: Dit artikel biedt een oplossing voor het probleem waarbij u het zoekprogramma probeert te wijzigen in Commerce Admin, maar de velden zijn vergrendeld.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Kan zoekengine niet wijzigen in `app/etc/env.php`

Dit artikel biedt een oplossing voor het probleem waarbij u de configuratie van de zoekmachine probeert te verwijderen uit de `app/etc/env.php` bestand, maar na opnieuw implementeren, wordt de configuratie teruggezet naar de vorige instelling of wordt de configuratie gewijzigd in [!DNL OpenSearch] standaard.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Probleem

U probeert het zoekprogramma te wijzigen in Commerce Admin, maar de velden zijn vergrendeld.

## Oorzaak

De configuratie van de zoekmachine is vergrendeld in het dialoogvenster `app/etc/env.php` of het zoekprogramma expliciet wordt gedefinieerd in het dialoogvenster `.magento.env.yaml` bestand.

## Oplossing

1. Controleer de `.magento.env.yaml` bestand onder het werkgebied implementeren en controleren of de `SEARCH_CONFIGURATION` variable is gevormd. Voorbeeld:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. Is de  `SEARCH_CONFIGURATION` variabele aanwezig? Indien niet aanwezig is, is de configuratie van de zoekmachine vergrendeld op [!DNL OpenSearch] standaard. Als u de configuratie wilt wijzigen, moet u de variabele aan de `.magento.env.yaml` bestand met de juiste waarde voor het zoekprogramma. Als de `SEARCH_CONFIGURATION` variabele aanwezig is en u wilt de motor wijzigen, de bestaande waarde voor de motor vervangen `.magento.env.yaml`. Mogelijke/bekende waarden: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], en [!DNL amasty_elastic_opensearch].
1. Implementeer de instantie opnieuw.
1. Het veld Zoekmachine in Beheer blijft vergrendeld, maar wordt bijgewerkt met de waarde die u hebt opgegeven.

## Gerelateerde lezing

* [Vergrendelde velden in Commerce Admin](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) in Commerce on Cloud Infrastructure Guide.
