---
title: '"500 fout" na het dubbelklikken op Koppeling verwijderen in winkelwagentje'
description: Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.0 dat te maken heeft met een fout bij klanten die proberen tweemaal een winkelwagentje te verwijderen (door te dubbelklikken op de koppeling *Verwijderen* of door erop te klikken op verschillende tabbladen).
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# &quot;500 fout&quot; na het dubbelklikken op Koppeling verwijderen in winkelwagentje

Dit artikel bevat een patch voor het bekende Adobe Commerce-probleem met cloudinfrastructuur 2.2.0 dat betrekking heeft op een fout die klanten ondervinden wanneer ze twee keer een winkelwagentje proberen te verwijderen (door te dubbelklikken op de knop *Verwijderen* (of door erop te klikken op verschillende tabbladen).

## Probleem

Wanneer klanten dubbelklikken op *Verwijderen* een link in het winkelwagentje , die probeert een product uit het winkelwagentje te verwijderen , krijgt een lege pagina met het volgende foutbericht : *&quot;Deze pagina werkt niet. HTTP-FOUT 500&quot;.* Hetzelfde probleem doet zich voor als een klant twee browsertabbladen met de winkelwagentje opent en het product eerst op één tabblad verwijdert, daarna op de tweede.

<u>Stappen om te reproduceren</u> :

1. Voeg een product toe aan winkelwagentje op de winkel.
1. Navigeer naar de winkelwagenpagina.
1. Klik de Remove verbinding tweemaal.

OF

1. Voeg een product toe aan winkelwagentje op de winkel.
1. Navigeer naar de winkelwagenpagina.
1. Open een nieuw browsertabblad en navigeer naar de winkelwagenpagina (hetzelfde product).
1. Verwijder het product uit het karretje.
1. Open het tweede tabblad en verwijder het product opnieuw.

<u>Verwacht resultaat</u> : Het product wordt zonder fouten uit het winkelwagentje verwijderd.

<u>Werkelijk resultaat</u> : Het product wordt verwijderd met de fout: *&quot;Deze pagina werkt niet. HTTP-FOUT 500&quot;* foutbericht.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[Download MDVA-8623\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce over cloudinfrastructuur 2.2.0

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce over cloudinfrastructuur 2.2.1 - 2.2.5
* Adobe Commerce op locatie 2.2.0 - 2.2.5

## Hoe de pleister aanbrengen

Zie voor instructies [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

## Bijgevoegde bestanden
