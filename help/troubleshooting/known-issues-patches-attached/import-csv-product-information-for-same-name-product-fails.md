---
title: CSV-productinformatie importeren voor product met dezelfde naam is mislukt
description: Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.3-probleem met betrekking tot het verkrijgen van fouten bij het importeren van een `.csv'-bestand met productinformatie als er producten met dezelfde naam zijn.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# CSV-productinformatie importeren voor product met dezelfde naam is mislukt

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.3-probleem met betrekking tot het verkrijgen van fouten bij het importeren van een `.csv` -bestand met productinformatie als er producten met dezelfde naam zijn.

## Probleem

Wanneer een `.csv` dossier met productinformatie wordt ingevoerd, en er producten met de zelfde naam zijn, krijgt u de volgende fout op de stap van de Gegevens van de Controle: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. De kwestie wordt veroorzaakt door het herschrijven van de producten URLs tijdens de invoer, zelfs wanneer er geen kolom voor producten&#39; URLs in het ingevoerde `.csv` dossier is.

<u> Stappen om </u> te reproduceren:

1. Maak twee configureerbare producten met dezelfde naam in Commerce Admin.
1. Maak een `.csv` -bestand om gegevens voor die producten te importeren, dat bijvoorbeeld de volgende kolommen bevat: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Ga naar **Systeem** > **Overdracht van Gegevens** > **de Invoer** en selecteer het `.csv` dossier.
1. Klik **Gegevens van de Controle**.

<u> Verwacht resultaat </u>:

Geen problemen gevonden; u kunt het `.csv` -bestand importeren.

<u> Werkelijk resultaat </u>:

Het volgende foutenbericht wordt getoond: *&quot;Sleutel XYZ URL werd reeds geproduceerd voor een punt met SKU %sku%&quot;*, is het niet mogelijk om het dossier in te voeren.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch downloaden](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce op locatie 2.2.3

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce op cloudinfrastructuur van 2.2.0 tot 2.2.7 en 2.3.0
* Adobe Commerce op locatie van 2.2.0 tot en met 2.2.2, van 2.2.4 tot en met 2.2.7 en 2.3.0

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis voor instructies wordt verstrekt.

## Nuttige koppelingen

[ pas douaneflarden op Adobe Commerce op wolkeninfrastructuur toe ](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Bijgevoegde bestanden
