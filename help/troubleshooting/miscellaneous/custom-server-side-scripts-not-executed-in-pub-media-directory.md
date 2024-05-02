---
title: Aangepaste serverscripts worden niet uitgevoerd in de mediamap van de publicatie
description: Dit artikel biedt een oplossing voor het geval aangepaste serverscripts niet worden uitgevoerd als ze in de ` worden geplaatst./pub/media/` directory van uw Adobe Commerce-toepassing op cloudinfrastructuur. Dit is een verwachte veiligheidsbeperking, sinds `.De map /pub/media/` kan worden geschreven. Als u scripts uitvoerbaar wilt maken, plaatst u ze in niet-schrijfbare mappen, zoals './app/code/` of `./pub/".
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Aangepaste serverscripts worden niet uitgevoerd in de mediamap van de publicatie

Dit artikel biedt een oplossing voor het feit dat aangepaste serverscripts niet worden uitgevoerd als deze in het dialoogvenster `./pub/media/` directory van uw Adobe Commerce-toepassing op cloudinfrastructuur. Dit is een verwachte veiligheidsbeperking, aangezien `./pub/media/` directory is schrijfbaar. Als u scripts uitvoerbaar wilt maken, plaatst u ze in niet-schrijfbare mappen, zoals `./app/code/` of `./pub/`.

## Betrokken versies

* Adobe Commerce op cloudinfrastructuur: 2.1.x en hoger, Starter en Pro plannen architectuur, Wings en verouderde architecturen

## Probleem: scripts zijn niet uitgevoerd

Aangepaste serverscripts kunnen niet worden uitgevoerd wanneer ze worden gestart.

Wanneer de eindgebruiker (Adobe Commerce-gebruiker) bijvoorbeeld op de koppeling klikt die leidt naar de `\*.php` bestand met het script (zoals *domain.com/media/directory/script.php* ), wordt het script gedownload in plaats van uitgevoerd.

## Oorzaak: onjuiste locatie van scriptbestand

De kwestie komt voor wanneer de manuscriptdossiers in worden gevestigd `./pub/media/` directory van Adobe Commerce-toepassing op cloudinfrastructuur. Dit is een verwacht gedrag: vanwege beveiligingsbeperkingen, bestanden van de beschrijfbare mappen (`./pub/media/`) nooit worden uitgevoerd.

## Oplossing: plaats scripts in niet-schrijfbare mappen

Sla de serverscripts op in niet-schrijfbare mappen, zoals `./app/code/` of `./pub/`  &quot;

## Gerelateerde documentatie

* [Cloud voor Adobe Commerce > Projectstructuur > Schrijfbare directory&#39;s](https://devdocs.magento.com/guides/v2.3/cloud/project/project-start.html#write-dir) in onze ontwikkelaarsdocumentatie.
