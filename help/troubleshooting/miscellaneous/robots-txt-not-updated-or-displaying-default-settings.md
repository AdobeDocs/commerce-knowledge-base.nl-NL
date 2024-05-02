---
title: robots.txt niet bijgewerkt of standaardinstellingen weergeven
description: Het artikel biedt een oplossing voor wanneer u ` robots.txt ` correct hebt gevormd, bijvoorbeeld per [Beste praktijken voor Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) maar ` robots.txt ` wordt niet bijgewerkt of toont de standaardinstellingen.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt niet bijgewerkt of standaardinstellingen weergeven

Het artikel verstrekt een oplossing voor wanneer u hebt gevormd `robots.txt` correct, bijvoorbeeld per [Aanbevolen procedures voor Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931) maar de `robots.txt` wordt niet bijgewerkt of geeft de standaardinstellingen weer.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Probleem

Kan de standaardwaarde niet wijzigen `robots.txt` instellen.

<u>Stappen om te reproduceren:</u>

1. Open het deelvenster Beheer.
1. Inhoud toevoegen aan **Inhoud** > Ontwerp > **Configuratie** > **Aangepaste instructies bewerken van`robots.txt`** en sla de wijzigingen op.
1. Ga naar `robots.txt` url.

<u>Verwacht resultaat:</u>
`robots.txt` bevat de opgeslagen tekst.

<u>Werkelijk resultaat:</u>

`robots.txt` bestand wordt niet gewijzigd.

## Oorzaak

Indexeren door zoekmachines is uitgeschakeld.

## Oplossing

Indexeren door zoekmachines inschakelen. Zie [Indexeren via zoekprogramma configureren](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

* [Robots voor site-toewijzing en zoekprogramma&#39;s toevoegen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in onze ontwikkelaarsdocumentatie.
