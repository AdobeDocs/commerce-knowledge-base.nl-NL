---
title: Kan btw-nummer niet valideren - Adobe Commerce op cloudinfrastructuur
description: Dit artikel bevat een patch voor het probleem waarbij een fout optreedt tijdens de verificatie van BTW-nummers.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Kan btw-nummer niet valideren - Adobe Commerce op cloudinfrastructuur

Dit artikel bevat een patch voor het probleem waarbij een fout optreedt tijdens de verificatie van BTW-nummers.

## Betrokken producten en versies

Alle Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuurversies tot en met 2.3.6 (inclusief 2.3.5-p1) werden beïnvloed, inclusief de reeds uitgebrachte p1- en p2-versies. Dit omvat:

* 2.3.5-p1
* 2.3.5.
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## Probleem

<u> Stappen om te reproduceren:</u>

1. Ga naar **Opslag** > **Configuratie** > **Klanten** > **de Configuratie van de Klant** > **creeer Nieuwe Opties van de Rekening** en plaats **automatische Taak** aan **de Groep van de Klant 13} aan *ja*.**
1. Ga naar **Algemeen** > **de Informatie van de Opslag** > en plaats een geldig Land en een Aantal van de BTW.
1. Klik op **Valideren het Aantal van BTW**.

<u> Verwacht resultaat:</u>

Validatie is gelukt.

<u> Ware resultaat:</u>

De volgende fout wordt getoond: &quot;*Fout tijdens de controle van het Aantal van BTW.*&quot;

## Oplossing

Pas het [ flard ](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) toe dat in dit artikel wordt verstrekt.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
