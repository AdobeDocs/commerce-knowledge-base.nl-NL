---
title: Adobe Commerce Support Knowledge Base begint met het accepteren van bijdragen
description: Vanaf 15 juni begint het Adobe Commerce Support Knowledge Base-team directe bewerkingen en nieuwe artikelbijdragen van de externe Adobe Commerce-gemeenschap te accepteren via de [magento/knowledge-base](https://github.com/magento/knowledge-base) GitHub repo!
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base begint met het accepteren van bijdragen

Vanaf 15 juni begint het Adobe Commerce Support Knowledge Base-team directe bewerkingen en nieuwe artikelbijdragen van de externe Adobe Commerce-gemeenschap te accepteren via de [magento/kennisbasis](https://github.com/magento/knowledge-base) GitHub repo!

Hebt u een typefout gezien in een van onze artikelen of onvolledige stappen voor het oplossen van problemen?
U kunt dit nu zelf oplossen en bijdragepunten ophalen!

## Contribute

Wij verwelkomen alle soorten bijdragen, van minder belangrijke typeverbeteringen tot volledige het oplossen van problemenartikelen. Als u een bijdrage levert aan deze repo, krijgt u bonuspunten, vergelijkbaar met een bijdrage aan de Adobe Commerce-code en onze documentatie voor ontwikkelaars. Zie [Betaalpunten voor bijdragen](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) voor meer informatie.

### Algemene bijdragestroom

1. vork deze repo.
1. Breng wijzigingen aan in de gesmeerde repo.
1. Verzend een aanvraag tot volledige verwijdering (PR) naar dit antwoord.
1. Tests worden uitgevoerd:
   * Adobe CLA - zorg ervoor de Adobe Open Source Contributor Licentieovereenkomst wordt ondertekend.
   * Markering Linting test - zorg ervoor de markeringssyntaxis correct is.
   * Validatietest van bestandsstructuur - controleren of de bewerking is uitgevoerd volgens de methode [vereiste bestandsstructuur](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. stroom PR-goedkeuringen:
   1. De steunkennisbasis (KB) schrijvers herzien PR binnen verscheidene dagenkader en voegen etiketten toe.
   1. KB-schrijver kan wijzigingen goedkeuren/weigeren/aanvragen.
   1. Indien goedgekeurd voegt de KB-schrijver etiketten toe die overeenkomen met het invoerniveau dat is opgegeven in de PR en interne onderwerpdeskundige (SME) toetst de PR.
   1. KMO&#39;s kunnen wijzigingen goedkeuren/weigeren/aanvragen.
1. Zodra alle correcties zijn uitgevoerd (indien gevraagd) en zowel de KB-schrijver als het MKB de PR goedkeuren, importeert de KB-schrijver inhoud naar het interne repo en voegt hij deze intern samen.
1. De [magento/kennisbasis](https://github.com/magento/knowledge-base) repo wordt over 20 minuten gesynchroniseerd met de interne.
1. Zodra de repos worden gesynchroniseerd, wordt uw PR gesloten en krijgt u [bijdragepunten](#contribution-points).

Voor meer informatie over de bijdragestroom raadpleegt u de [Handleiding voor contribuanten](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Voor sjablonen, stijlhulplijnen en opmaakrichtlijnen raadpleegt u [Documentatie](https://github.com/magento/knowledge-base/tree/main/docs).

### Zoek het KB-artikelbestand voor ondersteuning op Github

In de Support Knowledge Base (KB) worden artikelen geordend in secties, die worden genest in categorieën.

Bijvoorbeeld de [Hoe te om aan de statusupdates van het Magento van de Adobe in te schrijven](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) artikel behoort tot de algemene sectie in de categorie Procedure.

De sectie- en categorienaam worden weergegeven in het pad voor de broodkruimels op de artikelpagina. Zie de onderstaande afbeelding:

![categorie en afdeling broodkruimels](assets/breadcrumbs.png)

Artikelbestanden zijn op dezelfde manier geordend in de [magento/kennisbasis](https://github.com/magento/knowledge-base) repo.
Alle inhoud wordt opgeslagen in het dialoogvenster `src` met mappen voor categorieën en geneste mappen voor secties; bestandsnamen komen overeen met artikeltitels of zijn vergelijkbaar.

U zou onderzoek binnen de repo ook kunnen gebruiken gebruikend een stuk van tekst van het Steun KB artikel als onderzoekstekenreeks. Wanneer de zoekopdracht bestanden retourneert die deze tekenreeks bevatten, moet u het bestand kiezen dat tot de rechtersectie en categorie behoort.

### Bijdragingspunten

De [magento/kennisbasis](https://github.com/magento/knowledge-base) repo in combinatie met Community Engineering van Magento voor bijdragepunten en ondersteuning.

Zie [Bijdragingspunten](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) om te zien hoe punten worden beloond.
