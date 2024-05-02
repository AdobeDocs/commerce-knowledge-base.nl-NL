---
title: laminas/laminas-escaper 2.7.1 veroorzaakt een fout Adobe Commerce frontend en Admin pages
description: Dit artikel biedt een oplossing voor het probleem waarbij de release van laminas/laminas-escaper:2.7.1 de functionaliteit van Adobe Commerce in productbeheer, categorieën en productpagina's verbreekt. Dit probleem wordt opgelost in Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1 veroorzaakt een fout Adobe Commerce frontend en Admin pages


## Betrokken producten en versies

* Adobe Commerce op onze Cloud Architecture 2.3.5+
* Adobe Commerce 2.3.5+

## Probleem

Na de update naar laminas/laminas-escape:2.7.1 wordt een foutbericht weergegeven op de pagina.

<u>Stappen om te reproduceren</u>:

Werk laminas/laminas-escaper bij naar 2.7.1.

<u>Verwacht resultaat</u>:

Geen fout.

<u>Werkelijk resultaat</u>:

Na update naar laminas/laminas-escaper:2.7.1 wordt een foutbericht weergegeven op een pagina voor productbewerking (of productbeheer): *TypeError: rawurlencode() verwacht dat parameter 1 een tekenreeks is, int in /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Deze fout treedt op op de pagina&#39;s frontend en Admin, waardoor de inhoud van de pagina wordt vervormd.

## Oorzaak

laminas/laminas-escaper 2.7.1 begon strikte typedetectie te gebruiken voor de klasse Escaper.

## Oplossing

Uitvoeren `composer require laminas/laminas-escaper:2.7.0` in de wortelfolder van elk project.

## Gerelateerde lezing

Documentatie laminas: [laminas-escaper](https://docs.laminas.dev/laminas-escaper/)
