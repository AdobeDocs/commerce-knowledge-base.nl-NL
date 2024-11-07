---
title: Aangepaste serverscripts worden niet uitgevoerd in de mediamap van de publicatie
description: Dit artikel biedt een oplossing voor het geval aangepaste serverscripts niet worden uitgevoerd als ze in de ` worden geplaatst./pub/media/` directory van uw Adobe Commerce-toepassing op cloudinfrastructuur. Dit is een verwachte veiligheidsbeperking, sinds `.De map /pub/media/` kan worden geschreven. Als u scripts uitvoerbaar wilt maken, plaatst u ze in niet-schrijfbare mappen, zoals './app/code/` of `./pub/".
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Aangepaste serverscripts worden niet uitgevoerd in de mediamap van de publicatie

Dit artikel biedt een oplossing voor het geval aangepaste serverscripts niet worden uitgevoerd als deze in de map `./pub/media/` van uw Adobe Commerce-toepassing op de cloudinfrastructuur worden geplaatst. Dit is een verwachte beveiligingsbeperking, aangezien de map `./pub/media/` beschrijfbaar is. Als u scripts uitvoerbaar wilt maken, plaatst u ze in niet-schrijfbare mappen, zoals `./app/code/` of `./pub/` .

## Betrokken versies

* Adobe Commerce op cloudinfrastructuur: 2.1.x en hoger, Starter en Pro plannen architectuur, Wings en verouderde architecturen

## Probleem: scripts zijn niet uitgevoerd

Aangepaste serverscripts kunnen niet worden uitgevoerd wanneer ze worden gestart.

Bijvoorbeeld, wanneer het eind - gebruiker (Adobe Commerce verkoopster) de verbinding klikt die tot het `\*.php` dossier met het manuscript (als *domain.com/media/directory/script.php*) leidt, wordt het manuscript gedownload in plaats van het uitvoeren.

## Oorzaak: onjuiste locatie van scriptbestand

De kwestie komt voor wanneer de manuscriptdossiers in de `./pub/media/` folder van de toepassing van Adobe Commerce op wolkeninfrastructuur worden gevestigd. Dit is een verwacht gedrag: wegens veiligheidsbeperkingen, worden de dossiers van de beschrijfbare folders (`./pub/media/`) nooit uitgevoerd.

## Oplossing: plaats scripts in niet-schrijfbare mappen

Sla de serverscripts op in niet-schrijfbare mappen, zoals `./app/code/` of `./pub/` &quot;

## Gerelateerde documentatie

* [ Wolk voor Adobe Commerce > de structuur van het Project > Schrijfbare folders ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories) in onze ontwikkelaarsdocumentatie.
