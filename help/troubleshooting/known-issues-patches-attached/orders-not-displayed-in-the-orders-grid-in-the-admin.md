---
title: Orders worden niet weergegeven in het raster Orders in Beheer
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.1-probleem met betrekking tot de orders die niet worden weergegeven in het raster voor bestellingen in Commerce Admin.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Orders worden niet weergegeven in het raster Orders in Beheer

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.1-probleem met betrekking tot de orders die niet worden weergegeven in het raster voor bestellingen in Commerce Admin.

## Probleem

In Adobe Commerce 2.2.1 met B2B-extensie geïnstalleerd, worden bestellingen die door een geregistreerde klant in de winkel zijn gemaakt, niet weergegeven in de lijst met bestellingen in de account van de klant in Commerce Admin. In het logbestand voor foutopsporing (`./var/log/debug.log`), wordt de volgende fout geregistreerd:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Vereisten</u>:

Uw winkelcatalogus bevat producten, geen Adobe Commerce-voorbeeldgegevens en de B2B-extensie is geïnstalleerd.

<u>Stappen om te reproduceren</u>:

1. Navigeer naar de winkel en maak een klantenaccount.
1. Voeg een product toe aan het winkelwagentje, voltooi de afhandeling en verzend een bestelling.
1. Meld u aan bij de beheerder.
1. Navigeren naar **Klanten** kies vervolgens **Alle klanten**.
1. Voor de nieuwe klant klikt u op **Bewerken**.
1. Klikken **Orders** in het deelvenster aan de linkerkant.

<u>Verwacht resultaat</u>:

De onlangs verzonden volgorde wordt vermeld in het raster.

<u>Werkelijk resultaat</u>:

Het raster Orden wordt niet weergegeven. In plaats daarvan wordt een lege pagina weergegeven.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-7868\_EE\_2.2.1\_v1\_composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op locatie 2.2.1

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur van 2.2.0 tot 2.2.3
* Adobe Commerce op locatie 2.2.0 en 2.2.2 tot 2.2.3

## Hoe de pleister aanbrengen

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning, voor instructies.

## Bijgevoegde bestanden
