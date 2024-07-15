---
title: Verzendadres niet opgeslagen pagina Vernieuwen na afhandeling
description: Dit artikel bevat een patch voor de bekende Adobe Commerce 2.2.3-uitgave waarbij het reeds gevulde verzendadresformulier van de klant opnieuw leeg was nadat de browserpagina op de uitcheckpagina voor gasten was vernieuwd. Het probleem was toen het hardnekkige winkelwagentje werd ingeschakeld.
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Verzendadres niet opgeslagen pagina Vernieuwen na afhandeling

Dit artikel bevat een patch voor de bekende Adobe Commerce 2.2.3-uitgave waarbij het reeds gevulde verzendadresformulier van de klant opnieuw leeg was nadat de browserpagina op de uitcheckpagina voor gasten was vernieuwd. Het probleem was toen het hardnekkige winkelwagentje werd ingeschakeld.

## Probleem

Klanten gaan door de uitcheckprocedure voor gasten en vullen alle formulieren in, inclusief het verzendadres. Ze gaan naar de sectie Controleren en betalen en laden de pagina opnieuw. Het formulier is leeg en ze moeten het verzendadres opnieuw invoeren. De functie voor het permanent winkelwagentje is ingeschakeld.

<u> Stappen om </u> te reproduceren:

**Eerste vereisten**: De blijvende het winkelen functionaliteit van het karretje wordt toegelaten. Controle als het in Admin, onder **Opslag** wordt toegelaten > **Configuratie** > **Klanten** of **Opslag** > **Configuratie** > **Verkoop,** afhankelijk van uw versie van Adobe Commerce.

1. Ga naar de winkel.
1. Voeg producten toe aan het winkelwagentje.
1. Ga verder met uitchecken als gast.
1. Vul je verzendadres in, kies verzendopties en blijf de betaling beveiligen.
1. Doorgestuurd naar het gedeelte Controleren en betalen van de afhandeling.
1. Controleer of je het verzendadres ziet in de sectie Verzenden naar.
1. Vernieuw de pagina.

<u> Verwacht resultaat </u>:

U kunt doorgaan met het uitchecken en alle gegevens worden opgeslagen.

<u> Werkelijk resultaat </u>:

Het verzendadres is leeg. Je moet het opnieuw invoeren.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch downloaden](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies

**het flard werd gecreeerd voor:**

* Adobe Commerce 2.2.3

**het flard is ook compatibel (maar zou de kwestie niet kunnen oplossen) met de volgende versies en de uitgaven van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.1.13 - 2.1.18
* Adobe Commerce over cloudinfrastructuur 2.2.0 - 2.2.5
* Adobe Commerce op locatie 2.0.X
* Adobe Commerce op locatie 2.1.X
* Adobe Commerce op locatie 2.2.0 - 2.2.2 en 2.2.4 - 2.2.5

## Hoe de pleister aanbrengen

Voor instructies, zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.

## Bijgevoegde bestanden
