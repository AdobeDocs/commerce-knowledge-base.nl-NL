---
title: Probleem met een leeg winkelwagentje als u meerdere klikken hebt op afhandeling vanaf een minikaart
description: Dit artikel bevat een patch voor een bekend Adobe Commerce 2.2.3-probleem dat verband houdt met het leegmaken van een winkelwagentje nadat klanten op **Ga naar Afhandeling** meerdere keren in het mini-winkelwagentje klikken.
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Probleem met een leeg winkelwagentje als u meerdere klikken hebt op afhandeling vanaf een minikaart

Dit artikel biedt een patch voor een bekend Adobe Commerce 2.2.3-probleem met betrekking tot een winkelwagentje dat leeg is nadat klanten op **Ga naar Afhandeling** meerdere keren in het mini-winkelwagentje.

## Probleem

Klanten voegen producten toe aan het winkelwagentje, probeer het uit te checken door op de knop **Ga naar Afhandeling** meerdere keren , maar als ze naar de wagen gaan , is de wagen leeg . De mini-kar kan nog steeds producten tonen.

<u>Stappen om te reproduceren</u> :

1. Open een productpagina op de winkelvoorzijde.
1. Voeg producten toe aan winkelwagentje.
1. Klik in het miniwinkelwagentje op **Ga naar Afhandeling** meerdere keren.

<u>Verwacht resultaat</u> :

De winkelwagen bevat alle producten die u hebt toegevoegd.

<u>Werkelijk resultaat</u> :

Je hebt geen objecten in je winkelwagentje.

## Reparatie

De patches zijn aan dit artikel gekoppeld. Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de gewenste bestandsnaam of op een van de volgende koppelingen:

[Download MDVA-10441\_EE\_2.2.3\_v3.composer.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[Download MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### Compatibele Adobe Commerce-versies

De patches zijn gemaakt voor:

* Adobe Commerce op locatie 2.2.3 (de `MDVA-10441_EE_2.2.3_v3.composer.patch` bestand)
* Adobe Commerce over wolkeninfrastructuur 2.2.5 (`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` bestand)

De `MDVA-10441_EE_2.2.3_v3.composer.patch` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuurversies van 2.2.1 tot 2.2.5
* Adobe Commerce-versies ter plaatse van 2.2.1 tot 2.2.5

De `MDVA-17078_EE_2.2.5_COMPOSER_v1.patch` patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce 2.2.5

## Hoe een pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Bijgevoegde bestanden
