---
title: Fout bij wissen van cache in Commerce Admin
description: 'In dit artikel wordt uitgelegd hoe u de oorzaak kunt achterhalen van een foutbericht dat optreedt bij het leegmaken van de cache in Commerce Admin. Wanneer u de cache probeert te wissen via de beheerfunctie, ontvangt u het volgende bericht:'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Fout bij wissen van cache in Commerce Admin

In dit artikel wordt uitgelegd hoe u de oorzaak kunt achterhalen van een foutbericht dat optreedt bij het leegmaken van de cache in Commerce Admin. Wanneer u de cache probeert te wissen via de beheerfunctie, ontvangt u het volgende bericht:
Het bestand */app/project-id/pub/media/catalog/product/cache/directory/filename&quot; kan niet worden verwijderd. Waarschuwing!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): dergelijk bestand of deze map ontbreekt*

## Betrokken producten en versies

Adobe Commerce (alle implementatiemethoden) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Probleem

Wanneer u de cache probeert te wissen via de beheerfunctie, ontvangt u een foutbericht.

<u> Stappen om te reproduceren:</u>

1. In Admin, ga naar **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**.
1. Selecteer een van de opties voor het wissen van de cache.

<u> Verwacht resultaat:</u>

U kunt de Adobe Commerce-cache zonder fouten leegmaken.

<u> Ware resultaat:</u>

De fout &#39;&#39;Bestand kan niet worden verwijderd&#39;&#39; wordt weergegeven.

## Oorzaak

De fout houdt verband met een vertraging tussen de tijd dat de cachemschoonmaakbewerking is gestart en het tijdstip waarop deze werd gerapporteerd als voltooid.

## Oplossing

1. Bevestig dat de bestanden die in de fout worden vermeld, niet aanwezig zijn op de server (controleren of het leegmaken van de cache is gelukt):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Als u de volgende uitvoer ziet:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

er is geprobeerd de bestanden te wissen toen de bewerking al was voltooid. Dit is geen insect; het is een kwestie van de overseinensgelijktijdig die naar verwachting soms zal gebeuren. Er is geen probleem om problemen op te lossen.
Nochtans, als de output toont dat de dossiers nog in het geheime voorgeheugen zijn, moet u [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen.

## Verwante lezing

* [ Beheer van het Geheime voorgeheugen ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) in onze ontwikkelaarsdocumentatie.
