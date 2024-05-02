---
title: Adobe Commerce 2.4.6-fout bij het plaatsen van de volgorde in het deelvenster Beheer
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.4.6 wanneer u vastzit aan de keuze van de winkel nadat u een bestelling hebt geplaatst in het deelvenster Commerce Admin.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-fout bij het plaatsen van de volgorde in het deelvenster Beheer

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.4.6 wanneer u vastzit aan de keuze van de winkel nadat u een bestelling hebt geplaatst in het deelvenster Commerce Admin.

## Probleem

Wanneer u een bestelling plaatst in het deelvenster Beheer, blijft de selectie van de winkel ongewijzigd.

<u>Stappen om te reproduceren</u>

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en selecteer een klant om een bestelling te maken.
2. Selecteer de winkel om de volgorde in het selectiescherm van de winkel te plaatsen.

<u>Verwacht resultaat</u>

Nadat u de winkel hebt geselecteerd, kunt u de bestelling voltooien.

<u>Werkelijk resultaat:</u>

Nadat u de winkel hebt geselecteerd, gaat u terug naar de pagina met winkelkiezers en kunt u geen bestelling maken.

## Reparatie

Klik op de volgende koppeling om de patch te downloaden.

[ACSD-52277_2.4.6.patch downloaden](assets/ACSD-52277_2.4.6.patch.zip)

### Compatibele Adobe Commerce-versies

De patch is gemaakt voor en compatibel met Adobe Commerce op cloudinfrastructuur en Adobe Commerce op locatie 2.4.6 en 2.4.6-p1.

## Hoe de pleister aanbrengen

* Voor instructies over het toepassen van patches voor Adobe Commerce op cloudinfrastructuur raadpleegt u [Patches toepassen](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in onze Commerce on Cloud Infrastructure Guide.
* Voor instructies over het aanbrengen van pleisters voor Adobe Commerce op locatie raadpleegt u [Patches toepassen](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer) in onze Commerce Upgrade Guide.
