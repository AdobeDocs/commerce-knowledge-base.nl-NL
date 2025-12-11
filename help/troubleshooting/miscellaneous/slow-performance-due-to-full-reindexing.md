---
title: Trage prestaties als gevolg van volledige re-indexering
description: Dit artikel biedt een oplossing voor slechte prestaties als gevolg van volledige herindexering (waarbij gegevens in de indexerende databasetabellen worden bijgewerkt).
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 0786763a1db386fbea7f809eba9bc7f202cdd27a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Trage prestaties als gevolg van volledige re-indexering

Dit artikel biedt een oplossing voor slechte prestaties als gevolg van volledige herindexering (waarbij gegevens in de indexerende databasetabellen worden bijgewerkt).

## Betrokken versies en producten

* Adobe Commerce op cloudinfrastructuur 2.x.x
* Adobe Commerce op locatie 2.x.x

### Probleem

Constante doorspoeling en het opnieuw samenstellen van de index zijn enkele redenen voor prestatievermindering. Daarnaast worden met voortdurend volledig opnieuw indexeren vergrendelingen toegevoegd aan tabellen, waardoor de website veel langzamer werkt dan u had verwacht.

### Oorzaak

Acties die volledige herindexering kunnen produceren, zijn uitgevoerd vanuit de beheerder, waaronder:

* Opslaan van productkenmerk
* Opslaan van website-/winkel-weergave
* Winkelconfiguratie

>[!NOTE]
>
>Deze acties moeten buiten de kantooruren worden uitgevoerd om ervoor te zorgen dat deze acties geen invloed hebben op de prestaties tijdens de kantooruren.

[ derdeuitbreidingen ](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento) kunnen volledige herindex ook veroorzaken. Volledige herindex kan ook handmatig worden uitgevoerd vanaf CLI. Om te weten te komen als u indexen hebt die en potentieel prestatiesondergraving worden opnieuw bepaald veroorzaken:

1. Voer deze vraag uit om de indexeerders te vinden die volledig in de laatste 15 minuten opnieuw werden gedexeerd:

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   Een indexernaam in de uitvoer betekent dat de indexeerder ten minste één keer opnieuw is gedexeerd gedurende de laatste 15 minuten.

1. Als u veelvuldig volledige redexatie hebt gevonden, onderzoek het volgende:
   * Wie zou dit manueel van CLI kunnen doen
   * Welke module van derden voert de herindexatie uit
   * Welke derde module indexeerders als *ongeldig* markeert

### Oplossing

Voer alleen indien nodig opnieuw indexeren uit. Voor stappen, herzie [ Indexers ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) in onze ontwikkelaarsdocumentatie vormen. Een algemene aanbeveling en beste praktijk is om het partiële herindexeringsmechanisme in staat te stellen om te zorgen voor herindexering van gegevens zonder dat een handelaar hiervoor handmatig iets hoeft te doen. Alle re-dexatie zou moeten worden gedaan gebruikend inheemse functionaliteit van Adobe Commerce (Mview). Mview voert gedeeltelijke herindexatie uit, wat de meest efficiënte manier is om gegevens opnieuw te indexeren. Om over Mview te leren, verwijs naar [ Indexerend overzicht: Mview ](https://developer.adobe.com/commerce/php/development/components/indexing/#mview) in onze ontwikkelaarsdocumentatie.

## Verwante lezing

* [ Indexerend Overzicht: Hoe te om ](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex) in onze ontwikkelaarsdocumentatie opnieuw te indexeren.


