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

Dit artikel bevat een patch voor het bekende Adobe Commerce 2.2.3-probleem met betrekking tot het krijgen van fouten tijdens het importeren van een `.csv` met productinformatie in te dienen als er producten met dezelfde naam zijn.

## Probleem

Wanneer een `.csv` Er wordt een bestand met productinformatie geïmporteerd en er zijn producten met dezelfde naam. In de stap Gegevens controleren wordt de volgende fout gegenereerd: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. De kwestie wordt veroorzaakt door het herschrijven van de producten URLs tijdens de invoer, zelfs wanneer er geen kolom voor producten&#39; URLs in de ingevoerde `.csv` bestand.

<u>Stappen om te reproduceren</u>:

1. Maak twee configureerbare producten met dezelfde naam in Commerce Admin.
1. Een `.csv` bestand voor de invoer van gegevens voor deze producten, die bijvoorbeeld de volgende kolommen bevatten: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Ga naar **Systeem** > **Gegevensoverdracht** > **Importeren** en selecteert u de `.csv` bestand.
1. Klikken **Gegevens controleren**.

<u>Verwacht resultaat</u>:

Geen problemen gevonden; u kunt de `.csv` bestand is gelukt.

<u>Werkelijk resultaat</u>:

Het volgende foutbericht wordt weergegeven: *&quot;URL-sleutel XYZ is al gegenereerd voor een item met de SKU %sku%&quot;*, kan het bestand niet worden geïmporteerd.

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

Zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning voor instructies.

## Nuttige koppelingen

[Aangepaste patches op Adobe Commerce toepassen op cloudinfrastructuur](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## Bijgevoegde bestanden
