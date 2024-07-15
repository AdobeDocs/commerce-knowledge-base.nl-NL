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

Het artikel verstrekt een oplossing voor wanneer u `robots.txt` correct hebt gevormd, bijvoorbeeld per [ Beste praktijken voor Adobe Commerce robots.txt ](https://support.magento.com/hc/en-us/articles/360048754931) maar `robots.txt` wordt niet bijgewerkt of toont de standaardmontages.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur 2.3.x, 2.4.x

## Probleem

Kan de standaardinstelling `robots.txt` niet wijzigen.

<u> Stappen om te reproduceren:</u>

1. Open het deelvenster Beheer.
1. Voeg inhoud aan **Inhoud** toe > Ontwerp > **Configuratie** > **geeft de instructie van de Douane van`robots.txt`** dossier zoals de tekst &quot;hello&quot;en sparen de veranderingen uit.
1. Ga naar de `robots.txt` url.

<u> Verwacht resultaat:</u>
`robots.txt` heeft de opgeslagen tekst.

<u> Ware resultaat:</u>

`robots.txt` verandert niet.

## Oorzaak

Indexeren door zoekmachines is uitgeschakeld.

## Oplossing

Indexeren door zoekmachines inschakelen. Zie [ indexeren door onderzoeksmotor ](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) in onze ontwikkelaarsdocumentatie vormen.

## Gerelateerde lezing

* [ voeg plaatstoewijzing en onderzoekmachine robots ](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) in onze ontwikkelaarsdocumentatie toe.
