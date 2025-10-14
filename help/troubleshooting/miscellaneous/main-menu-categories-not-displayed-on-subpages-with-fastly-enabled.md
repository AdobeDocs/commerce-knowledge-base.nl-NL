---
title: Hoofdmenu (Categorieën) wordt niet weergegeven op subpagina's waarvoor Snelheid is ingeschakeld
description: Dit artikel biedt een oplossing voor het feit dat het hoofdmenu (of het [menu Navigatie boven aan categorie] (https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html?lang=nl-NL) in de gebruikershandleiding) niet wordt weergegeven in de winkel voor subpagina's (bijvoorbeeld *blog/pagina*) wanneer Fastly of Varnish is ingeschakeld.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Hoofdmenu (Categorieën) wordt niet weergegeven op subpagina&#39;s waarvoor Snelheid is ingeschakeld

Dit artikel verstrekt een moeilijke situatie voor wanneer het Belangrijkste Menu (of het [&#x200B; menu van de Navigatie van de Categorie Hoogste &#x200B;](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in onze gebruikersgids) niet op opslag voor subpagina&#39;s (bijvoorbeeld, *blog/pagina*) wordt getoond wanneer de Fastly of Varnish wordt toegelaten.

**Oorzaak:** het niet-toegelaten `/` karakter (schuine streep) in de *Zeer belangrijke URL* parameter van de pagina (de montages van de Optimalisering van de Motor van het Onderzoek). Het karakter wordt gewoonlijk toegevoegd wanneer *Weg URL* (met volledige paginalocatie) incorrect in plaats van *Sleutel URL* wordt gespecificeerd: bijvoorbeeld, *blog/pagina\_name* in plaats van enkel *pagina\_name*.

**Oplossing:** verwijder het `/` karakter (schuine streep); voor de *Zeer belangrijke URL* parameter, specificeer slechts de paginanaam.

## Betrokken versies

* Adobe Commerce op locatie 2.X.X
* Adobe Commerce op cloudinfrastructuur 2.X.X
* Fastly of Varnish

## Probleem

Het Belangrijkste Menu (die ook als het [&#x200B; Belangrijkste menu van de Navigatie van de Categorie &#x200B;](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in onze gebruikersgids wordt bedoeld) wordt niet getoond op opslag voor subpages wanneer de Fastly of andere op varens-Gebaseerde diensten worden toegelaten.

## Oorzaak

De kwestie wordt veroorzaakt door het niet-toegelaten `/` karakter (schuine streep), dat aan de *wordt toegevoegd Sleutel URL* parameter (de montages van de Optimalisering van de Motor van het Onderzoek).

Het karakter wordt gewoonlijk toegevoegd wanneer *Weg URL* (met volledige paginalocatie, met inbegrip van het oudermiddel/de folder van de pagina) incorrect in plaats van *Sleutel URL* wordt gespecificeerd: bijvoorbeeld, *blog/pagina\_name* in plaats van enkel *pagina \_name*.

![&#x200B; Zeer belangrijke parameter URL voor montages SEO &#x200B;](assets/seo_url_key.png)

## Oplossing

Verwijder het `/` karakter (schuine streep) uit de *Zeer belangrijke URL* parameter voor alle pagina&#39;s van uw opslag.

Met andere woorden, gebruik *Sleutel URL* in plaats van *Weg URL*: vermeld enkel de paginanaam zonder oudermiddel/folder.

### Recommendations op paginahiërarchie en SEO

Om de paginahiërarchie te plaatsen, gebruik de **sectie van de Hiërarchie** van het Edit menu van de Pagina.

![&#x200B; de montages van de Hiërarchie &#x200B;](assets/hierarchy_hr.png)

U kunt ook de **Inhoud** > **Elementen** > **Hiërarchie** menu - voor complexere hiërarchieoplossingen gebruiken.

Voor SEO doeleinden op productpagina&#39;s, herschrijft het gebruik URL (**Marketing** > **SEO &amp; Onderzoek** > **URL herschrijft**).

## Meer informatie in onze gebruikershandleiding

De *Zeer belangrijke URL* parameter voor SEO:

* [Optimalisatie zoekmachine](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Een nieuwe pagina toevoegen](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Paginahiërarchie:

* [Overzicht](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Een knooppunt toevoegen](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
