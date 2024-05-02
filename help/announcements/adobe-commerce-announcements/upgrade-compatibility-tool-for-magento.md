---
title: Upgrade Compatibility Tool 1.1.0 voor Adobe Commerce
description: Het hulpmiddel van de Verenigbaarheid van de Verbetering 1.1.0 is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules en kerncode te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke fouten, problemen en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Upgrade Compatibility Tool 1.1.0 voor Adobe Commerce

Het hulpmiddel van de Verenigbaarheid van de Verbetering 1.1.0 is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules en kerncode te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke fouten, problemen en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Wat is nieuw op UCT 1.1.0?

Het gereedschap Compatibiliteit upgraden 1.1.0 introduceert belangrijke verbeteringen, zoals:

* **Belangrijkste bestandswijzigingen valideren**: Adobe raadt sterk aan de basisproductcode niet aan te passen. Met deze versie, hebben wij een controlepunt voor klanten en partners toegevoegd om het even welke wijzigingen in de kerncode te identificeren om het effect van de wijzigingen vroeg en snel te begrijpen. Als u dit gereedschap toevoegt aan het ontwikkelingsproces, helpen partners en handelaren om problemen proactief op te sporen, problemen tijdens toekomstige upgrades te voorkomen en de totale eigendomskosten te verlagen.
* **Rapport exporteren naar een JSON-bestand**: Deze verbetering werd doorgevoerd na feedback van de community. Wanneer u het gereedschap nu uitvoert, worden de details van alle geïdentificeerde problemen geëxporteerd naar een JSON-bestand, zodat gebruikers de resultaten kunnen lezen, delen en beheren zonder het gereedschap opnieuw uit te voeren.
* **Verbeterde VBE-validaties**: VBE&#39;s (Bundled-extensies van leveranciers) maken geen deel uit van de Adobe Commerce-kerncode, maar worden getest en ondersteund door Adobe. Met deze update valideren we nu VBE&#39;s op dezelfde manier als voor kerncode. Deze verbetering zal gebruikers helpen kwesties met betrekking tot aanpassingen en kerncode/VBEs duidelijk begrijpen.
* **Foutcodes opgeven**: We hebben foutcodes geïntroduceerd waarmee gebruikers problemen tijdens een upgrade kunnen identificeren, begrijpen en oplossen. Fout- en waarschuwingsberichten bieden een duidelijke beschrijving en een voorgestelde oplossing.
* **Mogelijkheid om alleen kritieke kwesties weer te geven**: hiermee kunnen gebruikers zich alleen richten op die problemen die van essentieel belang zijn en tijdens de upgrade problemen veroorzaken.
* **Problemen met Delta tussen twee versies**: met deze door onze leden voorgestelde verbetering zullen UCT-gebruikers een delta van de problemen tussen twee versies kunnen krijgen, waardoor zij zich alleen kunnen richten op de nieuwe kwesties die zijn geïntroduceerd voor de doelversie die zij zullen upgraden.

## Welke versies kan het hulpmiddel vergelijken?

Met dit gereedschap kunt u elke 2.x-versie vergelijken.

## Wie kan het Hulpmiddel 1.1.0 van de Verenigbaarheid van de Verbetering gebruiken?

Adobe Commerce-klanten.

## Upgrade Compatibility Tool 1.1.0 installeren

Raadpleeg Adobe Commerce voor installatiestappen: [Upgrade Compatibility Tool > Install](https://devdocs.magento.com/upgrade-compatibility-tool/install.html) in onze ontwikkelaarsdocumentatie. Raadpleeg Adobe Commerce voor de voorwaarden voor het gebruik van het gereedschap: [Compatibiliteit upgraden](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html) in onze ontwikkelaarsdocumentatie.

## Wat is het aantal naast elke kwestie?

Dit is de naslaggids met foutberichten die informatie bevat over fouten die kunnen optreden tijdens het uitvoeren van het gereedschap Compatibiliteit bijwerken.

De foutberichten van het gereedschap Compatibiliteit bijwerken zijn gecategoriseerd op niveau (kritieke problemen, fouten en waarschuwingen) en type (kerncode, aangepaste code en GraphQL-schema&#39;s). Elk type bevat de volgende informatie:

* Foutcode: de door Adobe Commerce toegewezen id voor het foutbericht.
* Foutbeschrijving: een beschrijving die de oorzaak van de fout samenvat.
* Fout gesuggereerde actie: Indien van toepassing, verstrekt raad om de fout problemen op te lossen en op te lossen.
* De codes worden vermeld en beschreven op de [Referentiepagina van foutbericht](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html).

## Waar kan ik feedback over het gereedschap delen?

U kunt contact opnemen met het UCT-team op onze [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) slack channel. We kijken uit naar uw feedback en suggesties om het gereedschap te verbeteren.

## Verwante lezing

* Adobe Commerce-blog: [Introductie van het gereedschap Compatibiliteit upgraden (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Compatibiliteit upgraden](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html) in onze ontwikkelaarsdocumentatie.
