---
title: 'E-mail met de mededeling dat de exportopslag bijna vol is'
description: Dit artikel biedt een oplossing voor het probleem waarbij u een e-mail ontvangt met de mededeling dat de exportopslag bijna vol is.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# E-mail met de mededeling dat de exportopslag bijna vol is

Dit artikel biedt een oplossing voor het probleem waarbij u een e-mail ontvangt met de mededeling dat de exportopslag bijna vol is.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur (alle versies)

## Probleem

U ontvangt een e-mailbericht met de volgende inhoud, maar u kunt het bericht niet vinden *uitvoer* map:

*Onze controle heeft ontdekt dat de &#39;export&#39;-opslag in uw cluster XXX ongeveer &#39;85%&#39; vol is.*
*Controleer indien nodig het gebruik, maak een opschoonbewerking of vraag om een upgrade.*
*Ook, merk op dat wij automatisch proberen omhoog wanneer de opslag het kritieke-drempelniveau bereikt.*

## Oorzaak

Het e-mailbericht verwijst naar de **uitvoer** opslag, de hoeveelheid schijf die aan de bestanden/media wordt toegewezen en niet een specifieke map met de naam *uitvoer*.

## Oplossing

U moet het bestandsgebruik in de omgeving controleren. Voer deze opdracht uit om het bestaande gebruik te verkrijgen:

`df -h |grep data`

De typische locaties waar de bestandsopslag waarschijnlijk zal worden gevuld zijn de *pub/media/catalogus/product/cache* of *var/log* mappen. Voer deze opdracht met het juiste pad uit om te bepalen welke schijfruimte wordt gebruikt door de bestanden */path/to/folder*:

`du -shc` */path/to/folder*

Als het gebruik van de mediaschijf een groot deel van de totale schijfruimte uitmaakt, kunt u overwegen om [Snellere optimalisatie van afbeeldingen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)en verwijdert u vervolgens de bestanden in het dialoogvenster *pub/media/catalogus/product/cache* map handmatig op de server.

## Verwante lezing

[Specifieke clusters controleren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) in onze kennisbasis voor ondersteuning.