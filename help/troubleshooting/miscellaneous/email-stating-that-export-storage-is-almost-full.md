---
title: E-mail met de mededeling dat de exportopslag bijna vol is
description: Dit artikel biedt een oplossing voor het probleem waarbij u een e-mail ontvangt met de mededeling dat de exportopslag bijna vol is.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-mail met de mededeling dat de exportopslag bijna vol is

Dit artikel biedt een oplossing voor het probleem waarbij u een e-mail ontvangt met de mededeling dat de exportopslag bijna vol is.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

U ontvangt een e-mail met de volgende inhoud maar kan van de *uitvoer* omslag niet de plaats bepalen:

*onze controle heeft ontdekt dat de &quot;uitvoer&quot;opslag op uw cluster XXX rond &quot;85%&quot;volledig is.*
*Indien nodig, herzie gelieve het gebruik, doe een schoonmaakbeurt, of verzoek om te verhogen.*
*ook, merk op dat wij automatisch zullen proberen omhoog wanneer de opslag het kritiek-drempelniveau bereikt.*

## Oorzaak

E-mail verwijst naar de **uitvoer** opslag, die de hoeveelheid schijf is die aan de dossiers/media wordt toegewezen, en niet een specifieke genoemde omslag *voert* uit.

## Oplossing

U moet het bestandsgebruik in de omgeving controleren. Voer deze opdracht uit om het bestaande gebruik te verkrijgen:

`df -h |grep data`

De typische plaatsen waar de dossieropslag waarschijnlijk zal worden gevuld zijn *pub/media/catalogus/product/cache* of *var/log* omslagen. Om de schijfruimte te bepalen die door de dossiers wordt gebruikt, stel dit bevel met de aangewezen weg *in werking/path/to/folder*:

`du -shc` */path/to/folder*

Als het gebruik van de media schijf een groot deel van de totale schijfruimte uitmaakt, kunt u overwegen toelatend [ Vast Deep Optimalisering van het Beeld ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization), en dan de dossiers in de *pub/media/catalogus/product/geheime voorgeheugen* omslag op de server manueel schrappen.

## Verwante lezing

[ Controle specifieke clusters ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) in onze basis van steunkennis.
