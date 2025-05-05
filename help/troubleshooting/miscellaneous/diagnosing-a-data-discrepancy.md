---
title: Een gegevensdiscrepantie diagnosticeren
description: Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties tussen een Magento Business Intelligence (MBI) rapport en een vraag of derderapport.
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Een gegevensdiscrepantie diagnosticeren

Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties tussen een Magento Business Intelligence (MBI) rapport en een vraag of derderapport.

Afhankelijk van de complexiteit van uw analyse kan het genereren van het corresponderende MBI-rapport vereisen dat u vertrouwd bent met een aantal verschillende facetten van het platform. Deze controlelijst en de verwante verbindingen zullen u helpen de logica achter uw rapport begrijpen, toestaand u om de bron van om het even welke discrepanties te identificeren.

1. Als een ander lid van uw team het rapport creeerde, begin door de doelstelling en de parameters van hun analyse te bevestigen.
1. Genereer de verwachte gegevenspunten die u wilt vergelijken met het MBI-rapport op basis van een query, een rapportagetool van derden of een formule.
1. Herzie en bevestig de [ metrische ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html?lang=nl-NL) definitie(s), of van de metrische verbinding in Report Builder of door het [ Samenvatting van het Systeem ](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary) tabel te bezoeken:
   * Gegevenstabel
   * Bewerking
   * Operand kolom, met inbegrip van zijn berekening als het (via de Samenvatting van het Systeem) wordt afgeleid
   * Tijdstempel
   * Voor abonnementsmetriek: begin- en einddatum
   * Filters, met inbegrip van die bevat in om het even welke [ toegepaste filterreeksen ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html?lang=nl-NL)
1. Andere gegevensmanipulatie in het rapport controleren en bevestigen:
   * Berekende formules
   * [ Groepen ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=nl-NL#groupby)
   * [ Perspectieven ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=nl-NL)
   * [ de opties van de Tijd ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html?lang=nl-NL)
   * Voor [ cohortanalyse ](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): De datum van de Cohort
   * Voor [ cohortanalyse ](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis): Het perspectief van de Cohort
1. Als de discrepantie recente gegevens impliceert, bevestig het recentste beschikbare gegevenspunt door de **sectie van de Details van de Update** op de pagina van Verbindingen te raadplegen.
1. Als metrisch in de analyse wordt gebruikt op een lijst van uw gegevensbestand wordt voortgebouwd waar de rijen ooit van die lijst worden geschrapt, bevestig met het MBI Team van de Steun dat de lijst voor geschrapte rijen, evenals de frequentie van recheck en de [ replicatiemethode ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html?lang=nl-NL) voor de lijst wordt gecontroleerd.
1. Op dezelfde manier als de kolommen die in de analyse worden gebruikt kunnen worden gewijzigd nadat een rij wordt toegevoegd, bevestig met steun dat deze kolommen [ voor wijzigingen ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html?lang=nl-NL) worden gecontroleerd, evenals de frequentie van recheck.

**nog gestompt?** Maak je geen zorgen - we zijn hier om te helpen. Verzend ons een verzoek gebruikend [ deze instructies ](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md).

## Gerelateerde lezing

[ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
