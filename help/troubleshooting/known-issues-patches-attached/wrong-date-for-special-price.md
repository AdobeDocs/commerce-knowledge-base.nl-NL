---
title: Onjuiste datum voor speciale prijs
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.2-probleem met betrekking tot de speciale prijs van het product 'vanaf'-datum die onjuist is als de waarde ervan wordt gewijzigd door de beheerder wiens interface-landinstelling afwijkt.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Onjuiste datum voor speciale prijs

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.2-probleem met betrekking tot de speciale prijs van het product &#39;vanaf&#39;-datum die onjuist is als de waarde ervan wordt gewijzigd door de beheerder wiens interface-landinstelling afwijkt.

## Probleem

Wanneer u de speciale prijs voor een product instelt/wijzigt, worden de huidige datum en tijd in de database opgeslagen als een waarde voor het kenmerk `special_from_date` (niet zichtbaar bij het bewerken van een product). Als u de speciale prijs bewerkt en uw beheergebruikersaccount is ingesteld op een andere interfacetaal, is het mogelijk dat een verkeerde waarde is ingesteld op `special_from_date` vanwege de problemen in de notatie voor de parseerdatum voor verschillende landinstellingen.

<u> Stappen om </u> te reproduceren:

Vereisten: de landinstelling van de gebruiker voor het beheer is Engels (Verenigde Staten).

1. Meld u aan bij de Commerce-beheerder.
1. Ga naar de instellingen voor de gebruikersaccount van de beheerder.
1. Stel interfacelocatie in op Oekraïens.
1. Klik **sparen Rekening**.
1. Ga naar **Catalogus** > **Product**.
1. Selecteer een product.
1. Voor de productpagina, klik **Geavanceerde Prijsbepaling**.
1. Voeg een speciale prijs toe.
1. Sla het product op.
1. Herhaal stap 7-9.
1. Ga naar **Systeem** > **Logboeken van de Actie**.
1. Controleer het logboek op productupdate.

<u> Verwachte resultaten </u>:

De begindatum voor de speciale prijs moet de huidige datum zijn.

<u> Ware resultaten </u>:

De begindatum voor de speciale prijs is een datum die enkele jaren in de toekomst ligt, zodat de speciale prijs niet actief kan zijn.

## Oplossing

Als u de pleister toepast, voorkomt u dat het probleem opnieuw optreedt. U corrigeert de gegevens voor de producten waarvoor de datum onjuist is ingesteld door de speciale prijs opnieuw in te stellen nadat u de pleister hebt aangebracht.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-11605\_EE\_2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce (alle implementatiemethoden) 2.2.2

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce op cloudinfrastructuur 2.1.11-2.1.18, 2.2.0-2.2.5

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
