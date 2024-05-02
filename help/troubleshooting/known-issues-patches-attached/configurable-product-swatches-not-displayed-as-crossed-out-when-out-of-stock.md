---
title: Configureerbare productstalen die niet worden weergegeven, worden doorgehaald als de voorraad ophoudt
description: Dit artikel biedt een patch voor het bekende Adobe Commerce 2.2.2-probleem met betrekking tot de configureerbare productstalen die uit voorraad zijn en niet worden weergegeven zoals in de winkel wordt doorgestreept.
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Configureerbare productstalen die niet worden weergegeven, worden doorgehaald als de voorraad ophoudt

Dit artikel biedt een patch voor het bekende Adobe Commerce 2.2.2-probleem met betrekking tot de configureerbare productstalen die uit voorraad zijn en niet worden weergegeven zoals in de winkel wordt doorgestreept.

## Probleem

Wanneer u een configureerbaar product hebt en voor een bepaalde combinatie van opties, is het verwante eenvoudige product uit voorraad, is het staal nog steeds beschikbaar en kan het op de winkel worden geselecteerd.

<u>Stappen om te reproduceren</u>:

1. Maak in Commerce Admin een configureerbaar product met opties voor twee kenmerken: kleur (rood, zwart) en grootte (S, M, L).
1. Stel Hoeveelheid in op &quot;1&quot; voor elk overeenkomend eenvoudig product.
1. Voeg in de winkel rood M-product toe aan kar en kassa.
1. Verwerk de volgorde in Beheer zodat het aantal items wordt bijgewerkt naar &quot;0&quot;.
1. Zorg ervoor dat de backorders niet worden toegestaan.
1. Navigeer in de winkel naar dezelfde productpagina en selecteer dezelfde opties: rood, M.

<u>Verwachte resultaten</u>:

Het rode, M-staal heeft een rode schuine streep en kan niet worden geselecteerd.

<u>Werkelijke resultaten</u>:

Het rode M-staal kan worden geselecteerd.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-8215\_EE\_2.2\_v1.composer.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce (alle implementatiemethoden) 2.2.2

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.2.0-2.2.3

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
