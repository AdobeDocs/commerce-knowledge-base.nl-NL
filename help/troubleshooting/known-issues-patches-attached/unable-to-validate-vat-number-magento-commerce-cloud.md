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

<u>Stappen om te reproduceren:</u>

1. Ga naar **Winkels** > **Configuratie** > **Klanten** > **Klantconfiguratie** > **Nieuwe accountopties maken** en instellen **Automatische toewijzing inschakelen** tot **Klantengroep** tot *Ja*.
1. Ga naar **Algemeen** > **Opslaggegevens** > en geef een geldig land- en BTW-nummer op.
1. Klikken op **BTW-nummer valideren**.

<u>Verwacht resultaat:</u>

Validatie is gelukt.

<u>Werkelijk resultaat:</u>

De volgende fout wordt weergegeven: &quot;*Fout tijdens verificatie van BTW-nummer.*&quot;

## Oplossing

Pas de [pleister](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) in dit artikel.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Hoe de pleister aanbrengen

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies.

## Bijgevoegde bestanden
