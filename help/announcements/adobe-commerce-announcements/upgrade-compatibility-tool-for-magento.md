---
title: Upgrade Compatibility Tool 1.1.0 voor Adobe Commerce
description: Het hulpmiddel van de Verenigbaarheid van de Verbetering 1.1.0 is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules en kerncode te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke fouten, problemen en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade Compatibility Tool 1.1.0 voor Adobe Commerce

Het hulpmiddel van de Verenigbaarheid van de Verbetering 1.1.0 is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules en kerncode te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke fouten, problemen en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Wat is nieuw op UCT 1.1.0?

Het gereedschap Compatibiliteit upgraden 1.1.0 introduceert belangrijke verbeteringen, zoals:

* **bevestigt de veranderingen van het kerndossier**: De Adobe adviseert sterk tegen het aanpassen van kernproductcode. Met deze versie, hebben wij een controlepunt voor klanten en partners toegevoegd om het even welke wijzigingen in de kerncode te identificeren om het effect van de wijzigingen vroeg en snel te begrijpen. Als u dit gereedschap toevoegt aan het ontwikkelingsproces, helpen partners en handelaren om problemen proactief op te sporen, problemen tijdens toekomstige upgrades te voorkomen en de totale eigendomskosten te verlagen.
* **Uitvoer het rapport naar een JSON- dossier**: Deze verbetering werd uitgevoerd na terugkoppelen van de gemeenschap. Wanneer u het gereedschap nu uitvoert, worden de details van alle geïdentificeerde problemen geëxporteerd naar een JSON-bestand, zodat gebruikers de resultaten kunnen lezen, delen en beheren zonder het gereedschap opnieuw uit te voeren.
* **Verbeterde VBE bevestigingen**: VBEs (Verkoper Gebundelde Uitbreidingen) maakt geen deel uit van de kerncode van Adobe Commerce maar wordt getest en door Adobe gesteund. Met deze update valideren we nu VBE&#39;s op dezelfde manier als voor kerncode. Deze verbetering zal gebruikers helpen kwesties met betrekking tot aanpassingen en kerncode/VBEs duidelijk begrijpen.
* **verstrek foutencodes**: Wij introduceerden foutencodes om gebruikers te helpen, kwesties tijdens een verbetering identificeren begrijpen en oplossen. Fout- en waarschuwingsberichten bieden een duidelijke beschrijving en een voorgestelde oplossing.
* **Mogelijkheid om van slechts kritieke kwesties** een lijst te maken: met dit, zullen de gebruikers zich slechts op die kwesties kunnen concentreren die kritiek zijn en problemen tijdens de bevordering zullen produceren.
* **de kwesties van de Delta tussen twee versies**: met deze verbetering die door onze communautaire leden wordt voorgesteld, zullen de gebruikers UCT een delta van de kwesties tussen twee versies kunnen krijgen, die hen zullen toestaan om zich slechts op de nieuwe kwesties te concentreren die voor de doelversie worden geïntroduceerd zij zullen bevorderen.

## Welke versies kan het hulpmiddel vergelijken?

Met dit gereedschap kunt u elke 2.x-versie vergelijken.

## Wie kan het Hulpmiddel 1.1.0 van de Verenigbaarheid van de Verbetering gebruiken?

Adobe Commerce-klanten.

## Upgrade Compatibility Tool 1.1.0 installeren

Voor installatiestappen, verwijs naar Adobe Commerce: [ het Hulpmiddel van de Verenigbaarheid van de Verbetering > installeert ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run) in onze ontwikkelaarsdocumentatie. Voor eerste vereisten om het hulpmiddel te gebruiken, verwijs naar Adobe Commerce: [ het Hulpmiddel van de Verenigbaarheid van de Verbetering ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/prerequisites) in onze ontwikkelaarsdocumentatie.

## Wat is het aantal naast elke kwestie?

Dit is de naslaggids met foutberichten die informatie bevat over fouten die kunnen optreden tijdens het uitvoeren van het gereedschap Compatibiliteit bijwerken.

De foutberichten van het gereedschap Compatibiliteit bijwerken zijn gecategoriseerd op niveau (kritieke problemen, fouten en waarschuwingen) en type (kerncode, aangepaste code en GraphQL-schema&#39;s). Elk type bevat de volgende informatie:

* Foutcode: de door Adobe Commerce toegewezen id voor het foutbericht.
* Foutbeschrijving: een beschrijving die de oorzaak van de fout samenvat.
* Fout gesuggereerde actie: Indien van toepassing, verstrekt raad om de fout problemen op te lossen en op te lossen.
* De codes zijn vermeld en beschreven op de [ pagina van de het berichtverwijzing van de Fout ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/reporting/error-messages).

## Waar kan ik feedback over het gereedschap delen?

U kunt het UCT team op ons [ #upgrade-verenigbaarheid-hulpmiddel ](https://magentocommeng.slack.com/archives/C019Y143U9F) plakkanaal contacteren. We kijken uit naar uw feedback en suggesties om het gereedschap te verbeteren.

## Verwante lezing

* Adobe Commerce Blog: [ Introducerend het Hulpmiddel van de Verenigbaarheid van de Verbetering (Alpha) ](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [ het Hulpmiddel van de Verenigbaarheid van de Verbetering ](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview) in onze ontwikkelaarsdocumentatie.
