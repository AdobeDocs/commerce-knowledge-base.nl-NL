---
title: Composer-insteekmodule tegen aanvallen van Dependency Confusion
description: Dit artikel bevat informatie over de componentplug-in die wordt vrijgegeven voor de aanvallen van Dependency Confusion en aanbevelingen over het voorkomen van de fout. De Composer-insteekmodule is naast de release van Adobe Commerce 2.4.3 geïntroduceerd om Adobe Commerce-handelaren te beschermen tegen aanvallen van Dependency Confusion.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Composer-insteekmodule tegen aanvallen van Dependency Confusion

Dit artikel bevat informatie over de componentplug-in die wordt vrijgegeven voor de aanvallen van Dependency Confusion en aanbevelingen over het voorkomen van de fout. De Composer-insteekmodule is naast de release van Adobe Commerce 2.4.3 geïntroduceerd om Adobe Commerce-handelaren te beschermen tegen aanvallen van Dependency Confusion.

## Betrokken producten en versies

* Adobe Commerce 2.4.3 en toekomstige versies (alle implementatiemethoden)

## Probleem

Een mogelijk geval van een actieve Aanval van de Verwardheid van de Afhankelijkheid wordt ontdekt door minstens één van de directe of indirecte gebiedsdelen die in `composer.json` door de componentplug-in `magento/composer-dependency-version-audit-plugin` tijdens installatie/update van composer.

<u>Stappen om te reproduceren</u>:

Wanneer u composer installeert/bijwerkt, zal de composer stop het proces als het een potentiële aanval van de Verwaring van de Afhankelijkheid ontdekt. In dat geval mislukt de installatie/update van de composer met een foutbericht zoals:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Oorzaak

De aanval van de Verwaring van de afhankelijkheid staat toe om willekeurige code op een server ver uit te voeren door een gebiedsdeelmanager (bijvoorbeeld, Composer van PHP) in het downloaden van een kwaadwillig pakket van een openbare bron in plaats van het originele pakket van een privé bewaarplaats te slepen.

Een dergelijke aanval kan zelfs onopgemerkt blijven als een aanvaller de functionaliteit van het originele pakket kan handhaven.

Aanvallers kunnen deze kwetsbaarheid misbruiken als een pakket alleen beschikbaar is via privéopslagplaatsen, maar niet is geregistreerd in het openbare depot. De aanvaller uploadt dan een pakket met dezelfde naam naar de openbare opslagplaats en geeft deze een hogere versie dan de versie die persoonlijk beschikbaar is. De afhankelijkheidsmanager zal dan versies van zowel privé als openbaar beschikbare pakketten vergelijken en zal hoogste kiezen van de openbare bewaarplaats. De kwaadaardige code die door de afhankelijkheidsmanager wordt gedownload, wordt vervolgens uitgevoerd met dezelfde bevoegdheden als de code van de toepassing.

## Oplossing

### Recommendations voor handelaren

* Neem het foutbericht dat wordt weergegeven wanneer de plug-in de installatie/update van de composer stopt, en neem contact op met de extensieontwikkelaar als u het mogelijk gecompromitteerde pakket herkent.
* U kunt Adobe Commerce nog steeds installeren met de veilige versie van het pakket van de Marketplace of een andere vertrouwde privéopslagplaats.
* Wijzig de vereiste pakketversie in uw composer.json in de exacte versie die u in de Marketplace vindt om door te gaan met de installatie/update van de composer.

### Verwachtingen van ontwikkelaars van extensies

* Er is geen enkele manier om vast te stellen of het pakket voor een insteekmodule, als dit afkomstig is van een publieke repo, al dan niet in gevaar is gebracht. De insteekmodule detecteert wanneer een openbare versie van een pakket op packagist.org een hogere versie heeft dan de versie die beschikbaar is in een privérepo [repo.magento.com](https://repo.magento.com). We raden ontwikkelaars van extensies aan dergelijke situaties te vermijden en geen nieuwere versies openbaar te publiceren die beschikbaar zijn via [repo.magento.com](https://repo.magento.com).
* Adobe Commerce begrijpt dat het marktweerhalingsproces de beschikbaarheid van de release van extensies kan vertragen, maar dat het proces er is om handelaren veilig te houden en om ontwikkelaars te helpen onbedoelde fouten te vinden die ze wellicht hebben gemist.
