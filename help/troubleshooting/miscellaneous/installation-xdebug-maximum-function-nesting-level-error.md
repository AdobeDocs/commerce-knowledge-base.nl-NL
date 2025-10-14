---
title: Fout bij installatie xdebug van maximumnestniveau van functie
description: Dit artikel bevat een oplossing voor de fout met het nestniveau van de functie Xdebug tijdens de installatie.
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# Fout bij installatie xdebug van maximumnestniveau van functie

Dit artikel bevat een oplossing voor de fout met het nestniveau van de functie Xdebug tijdens de installatie.

## Details

Tijdens de installatie van Adobe Commerce wordt een bericht weergegeven dat lijkt op het volgende:

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

U wordt ten zeerste aangeraden `xdebug` NIET TE GEBRUIKEN in een productieomgeving.

## Oplossing

Er is een bekend probleem met `xdebug` dat invloed kan hebben op Adobe Commerce-installaties of op de toegang tot de winkel of Commerce Admin na de installatie.

Voor details, zie [&#x200B; Bekende kwestie met xdebug &#x200B;](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) in onze basis van de steunkennis.
