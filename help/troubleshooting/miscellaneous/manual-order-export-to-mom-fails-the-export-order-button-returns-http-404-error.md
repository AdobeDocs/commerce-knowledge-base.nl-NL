---
title: Het handmatig exporteren van bestellingen naar MOM mislukt. De knop Exportvolgorde retourneert de HTTP 404-fout
description: In dit artikel wordt besproken hoe u een probleem kunt oplossen. Wanneer u een bestelling naar Magento Order Management probeert te exporteren door op de knop **Exportopdracht** in de ordeweergave in Commerce Admin te klikken, wordt de fout " *404 Pagina niet gevonden*" geretourneerd.
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Het handmatig exporteren van bestellingen naar MOM mislukt. De knop Exportvolgorde retourneert de HTTP 404-fout

Dit artikel bespreekt hoe te om een kwestie te bevestigen, waar het proberen om een orde naar Magento Order Management (MOM) uit te voeren door de **knoop van de Orde van de Uitvoer** op de ordemening in Commerce Admin keert a &quot; *terug 404 Pagina niet gevonden* &quot; fout.

## Betrokken producten en versies

* Adobe Commerce 2.2.x, 2.3.x
* MOM-aansluiting 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Probleem

<u> Stappen om te reproduceren:</u>:

1. In Commerce Admin, klik **Verkoop > Orden**.
1. Klik **creëren Nieuwe Orde** knoop.
1. Selecteer een gebruiker, voeg een of meer punten toe, selecteer betaling en verschepende methodes, en klik dan de **Verzendorde** knoop.
1. Klik de **knoop van de Orde van de Uitvoer** en dan **O.K.**.

<u> Verwacht resultaat </u>:

De orde wordt verzonden naar MOM.

<u> Werkelijk resultaat </u>:

A &quot; *404 Fout: Pagina niet gevonden* &quot; pagina wordt getoond.

## Oplossing

* Upgrade de MOM-aansluiting naar 3.4.0 voor Adobe Commerce 2.3.x of MOM-aansluiting 2.5 voor Adobe Commerce 2.2.x.
* Als het bevorderen van de Schakelaar van het MOM geen optie is, kunt u de orde naar Magento Order Management uitvoeren gebruikend het CLI bevel:

```bash
$bin/magento oms:orders:sync
```

## Gerelateerde lezing

[ Magento Order Management technische documentatie ](https://commerce-docs.github.io/oms-documentation-archive/)
