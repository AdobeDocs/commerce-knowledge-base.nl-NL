---
title: Adobe Commerce 2.4.1 en 2.3.6 maken een accountknop met uitgeschakelde hotfix
description: Dit artikel bevat een hotfix voor het probleem wanneer u moeite hebt om een nieuw account te maken nadat u een onjuiste waarde hebt ingevoerd in een veld op het formulier. Als u bijvoorbeeld een e-mailadres in de verkeerde notatie invoert of de velden voor de voornaam of achternaam leeg laat of geen waarde invoert die aan de wachtwoordvereisten voldoet. Een permanente oplossing wordt opgenomen in de Q1-releases (2.4.2, 2.4.1-p1 en 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 en 2.3.6 maken een accountknop met uitgeschakelde hotfix

Dit artikel bevat een hotfix voor het probleem wanneer u moeite hebt om een nieuw account te maken nadat u een onjuiste waarde hebt ingevoerd in een veld op het formulier. Als u bijvoorbeeld een e-mailadres in de verkeerde notatie invoert of de velden voor de voornaam of achternaam leeg laat of geen waarde invoert die aan de wachtwoordvereisten voldoet. Een permanente oplossing wordt opgenomen in de Q1-releases (2.4.2, 2.4.1-p1 en 2.3.6-p1).

## Probleem

**creeer een knoop van de Rekening** op **creeer Nieuwe pagina van de Rekening** gehandicapt blijft als een verkoopster ongeldige gegevens heeft ingegaan. Zo voorkomt u dat kopers opnieuw proberen een account te maken nadat ze een fout hebben gemaakt.

<u> Stappen om </u> te reproduceren:

1. Ga naar **creëren Nieuwe Rekening van de Klant**.
1. Vul de formuliervelden in. Op het **gebied van het Wachtwoord**, inputwaarden die niet de wachtwoordvereisten voldoen. Bijvoorbeeld:
   * De wachtwoorden in het **Wachtwoord** en **bevestigen de gebieden van het Wachtwoord** passen niet aan.
   * De wachtwoorden in het **Wachtwoord** en **bevestigen de gebieden van het Wachtwoord** zijn niet lang genoeg.
1. Klik **creeer een knoop van de Rekening**.

<u> Verwachte resultaten </u>:

* **creeer een knoop van de Rekening** actief/toegelaten zou moeten blijven.
* De gebruiker moet een nieuwe account kunnen maken.

<u> Ware resultaten </u>:

* **creeer een de knoopverblijven van de Rekening** gehandicapt, zelfs na het invullen van alle vereiste gebieden met geldige/correcte gegevens.
* De klant kan geen nieuwe account maken.

## Reparatie

De patch is aan dit artikel gekoppeld. Om het te downloaden, scrol neer aan het eind van het artikel en klik het dossier - noem of klik de volgende verbinding: [ Download MC-38509-composer.patch ](assets/MC-38509-composer.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op wolkeninfrastructuur 2.3.6 en 2.4.1.
* Adobe Commerce op locatie 2.3.6 en 2.4.1.

De patch is niet compatibel met andere Adobe Commerce-versies en -versies.

## Hoe de pleister moet worden aangebracht

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Gerelateerde lezing

* [ GitHub Adobe Commerce > het Voorleggen van ongeldig leidt rekeningsvorm tot verlaten de voorgelegde knoop ](https://github.com/magento/magento2/issues/30513)
* [ de Gids van de Gebruiker van Adobe Commerce > Begonnen het worden > Creërend een Rekening ](https://docs.magento.com/user-guide/magento/magento-account-create.html)
