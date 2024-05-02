---
title: Een gegevensdiscrepantie diagnosticeren
description: Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties tussen een Magento Business Intelligence (MBI) rapport en een vraag of derderapport.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Een gegevensdiscrepantie diagnosticeren

Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties tussen een Magento Business Intelligence (MBI) rapport en een vraag of derderapport.

Afhankelijk van de complexiteit van uw analyse kan het genereren van het corresponderende MBI-rapport vereisen dat u vertrouwd bent met een aantal verschillende facetten van het platform. Deze controlelijst en de verwante verbindingen zullen u helpen de logica achter uw rapport begrijpen, toestaand u om de bron van om het even welke discrepanties te identificeren.

1. Als een ander lid van uw team het rapport creeerde, begin door de doelstelling en de parameters van hun analyse te bevestigen.
1. Genereer de verwachte gegevenspunten die u wilt vergelijken met het MBI-rapport op basis van een query, een rapportagetool van derden of een formule.
1. De [metrisch](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html) definitie(s), hetzij van de metrische verbinding in Report Builder, hetzij door het bezoeken van [Systeemoverzicht](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) tab:
   * Gegevenstabel
   * Bewerking
   * Operand kolom, met inbegrip van zijn berekening als het (via de Samenvatting van het Systeem) wordt afgeleid
   * Tijdstempel
   * Voor abonnementsmetriek: begin- en einddatum
   * Filters, daaronder begrepen die welke in alle [filtersets](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html) toegepast
1. Andere gegevensmanipulatie in het rapport controleren en bevestigen:
   * Berekende formules
   * [Groepen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [Perspectieven](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [Tijdopties](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * Voor [cohortanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Cohortdatum
   * Voor [cohortanalyse](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Cohortperspectief
1. Als de discrepantie betrekking heeft op recente gegevens, bevestigt u het meest recente beschikbare gegevenspunt door de **Details bijwerken** op de pagina Verbindingen.
1. Als metrisch die in de analyse wordt gebruikt op een lijst van uw gegevensbestand wordt voortgebouwd waar de rijen ooit uit die lijst worden geschrapt, bevestig met het Team van de Steun MBI dat de lijst op geschrapte rijen, evenals de frequentie van recheck en wordt gecontroleerd [replicatiemethode](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) voor de tabel.
1. Op dezelfde manier als de kolommen die in de analyse worden gebruikt kunnen worden gewijzigd nadat een rij wordt toegevoegd, bevestig met steun dat deze kolommen worden gebruikt [gecontroleerd op wijzigingen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html)en de frequentie van de hercontrole.

**Nog steeds gestompt?** Maak je geen zorgen - we zijn hier om te helpen. Stuur ons een aanvraag met [deze instructies](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).
