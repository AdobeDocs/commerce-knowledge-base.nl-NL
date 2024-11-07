---
title: De verlening van machtigingen voor var-/exportmappen geeft Adobe Commerce in de cloud weer
description: Dit artikel biedt een oplossing voor een probleem waarbij u geen productgegevens kunt exporteren vanwege een probleem met bestandsmachtigingen op de server in de map 'var/export/email'. Symptomen omvatten de uitvoer van het Product en van de Catalogus niet beschikbaar in het gebruikersinterface, maar zijn zichtbaar wanneer het gebruiken van SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# De verlening van machtigingen voor var-/exportmappen geeft Adobe Commerce in de cloud weer

Dit artikel biedt een oplossing voor een probleem waarbij u geen productgegevens kunt exporteren vanwege een probleem met bestandsmachtigingen op de server in de map `var/export/email` . Symptomen omvatten de uitvoer van het Product en van de Catalogus niet beschikbaar in het gebruikersinterface, maar zijn zichtbaar wanneer het gebruiken van SSH.

## Betrokken producten en versies

Adobe Commerce on cloud Infrastructure, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Probleem

U kunt geen bestanden exporteren in de map `var/export/email` of `var/export/archive` .
Deze versie is niet geïmplementeerd vanwege machtigingen op `var/export/email` of `var/export/email/archive` omdat die archiefmap onder e-mail wordt gemaakt en als ik alleen exporteer/e-mail doe, is er soms nog een probleem) anders dan iets aan de account voor de submap toevoegen `var/export/email/archive` .

<u> Stappen om </u> te reproduceren:

In Admin, ga naar **Systeem** > *Overdracht van Gegevens* > **Uitvoer**.
Selecteer de CSV-bestanden die u wilt opslaan in de map `var/export/` .

<u> Verwacht resultaat </u>:

CSV-bestanden zijn zichtbaar en kunnen worden geëxporteerd.

<u> Werkelijk resultaat </u>:

CSV-bestanden zijn niet zichtbaar. U ziet ook een toestemmingsontkend bericht: *RecursiveDirectoryIterator::__construct (/app/project id>/var/export/email): ontbroken om dir te openen: Vergunning ontzegd*

U ontvangt hetzelfde bericht voor alle exporttypen: Geavanceerde prijzen, Klantenfinanciën, Hoofdbestand van klant en Adres van klant.

## Oorzaak

Dit wordt veroorzaakt door een map die in `/var` is gemaakt en waarvoor imperfecte machtigingen gelden: `d-wxrwsr-T` . Met de plakbit T kunnen gebruikers alleen de bestanden verwijderen die ze bezitten, maar met het ontbrekende uitvoerbare bestand kunnen ze geen bestanden in de map maken.

Dit wordt vaak opgemerkt wanneer het systeem een map met de naam `export` maakt die een map met de naam `email` bevat die een map met de naam `archive` bevat.

Om te controleren als de folder deze misconfigured toestemmingen heeft, stel het volgende bevel in CLI/Terminal in werking:

`ls -ld var/export/`

De uitvoer als de toestemmingen verkeerd worden gevormd zal zijn:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Oplossing

Als u dit wilt verhelpen, werkt u de machtigingen van de mappen bij tot 777 en alle bestanden recursief, door de volgende opdrachten uit te voeren:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Gerelateerde lezing

* [ Uitvoer ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-export) in onze gebruikersgids.
