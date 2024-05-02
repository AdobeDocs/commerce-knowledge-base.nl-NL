---
title: Hoofdmenu (Categorieën) wordt niet weergegeven op subpagina's waarvoor Snelheid is ingeschakeld
description: Dit artikel biedt een oplossing voor het feit dat het hoofdmenu (of het [menu Navigatie boven aan categorie] (https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in de gebruikershandleiding) niet wordt weergegeven in de winkel voor subpagina's (bijvoorbeeld *blog/pagina*) wanneer Fastly of Varnish is ingeschakeld.
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Hoofdmenu (Categorieën) wordt niet weergegeven op subpagina&#39;s waarvoor Snelheid is ingeschakeld

Dit artikel bevat een oplossing voor het gebruik van het hoofdmenu (of het dialoogvenster [Menu Navigatie boven categorie](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in onze gebruikershandleiding) niet wordt weergegeven in de winkel voor subpagina&#39;s (bijvoorbeeld *blog/pagina*) als Fastly of Varnish is ingeschakeld.

**Oorzaak:** niet-toegelaten `/` teken (schuine streep) in de *URL-sleutel* parameter van de pagina (Optimalisatie-instellingen voor zoekprogramma). Het teken wordt meestal toegevoegd wanneer *URL-pad* (met volledige paginalocatie) wordt per ongeluk opgegeven in plaats van *URL-sleutel*: bijvoorbeeld *blog/pagina\_naam* in plaats van *page\_name*.

**Oplossing:** verwijderen `/` teken (schuine streep); voor de *URL-sleutel* alleen de paginanaam op.

## Betrokken versies

* Adobe Commerce op locatie 2.X.X
* Adobe Commerce op cloudinfrastructuur 2.X.X
* Fastly of Varnish

## Probleem

Het hoofdmenu (ook wel het [Menu Navigatie boven categorie](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) in onze gebruikershandleiding) wordt niet weergegeven op de winkel voor subpagina&#39;s wanneer de services Snelst of andere op vernis gebaseerde services zijn ingeschakeld.

## Oorzaak

Het probleem wordt veroorzaakt door het niet-toegestane `/` teken (schuine streep), toegevoegd aan de *URL-sleutel* parameter (Optimalisatie-instellingen voor zoekprogramma).

Het teken wordt meestal toegevoegd wanneer *URL-pad* (met volledige paginalocatie, inclusief de bovenliggende bron/directory van de pagina) wordt per ongeluk opgegeven in plaats van *URL-sleutel*: bijvoorbeeld *blog/pagina\_naam* in plaats van *page\_name*.

![URL-sleutelparameter voor SEO-instellingen](assets/seo_url_key.png)

## Oplossing

Verwijder de `/` teken (schuine streep) uit de *URL-sleutel* parameter voor alle pagina&#39;s van uw opslag.

Met andere woorden, gebruik *URL-sleutel* in plaats van *URL-pad*: vermeld alleen de paginanaam zonder bovenliggende bron/map.

### Recommendations op paginahiërarchie en SEO

Als u de paginahiërarchie wilt instellen, gebruikt u de opdracht **Hiërarchie** in het menu Pagina bewerken.

![Hiërarchie-instellingen](assets/hierarchy_hr.png)

U kunt ook de opdracht **Inhoud** > **Elementen** > **Hiërarchie** -menu - voor complexere hiërarchieoplossingen.

Voor SEO-doeleinden op productpagina&#39;s gebruikt u URL Rewrites (**Marketing** > **SEO &amp; Search** > **URL herschrijft**).

## Meer informatie in onze gebruikershandleiding

De *URL-sleutel* parameter voor SEO:

* [Optimalisatie zoekmachine](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [Een nieuwe pagina toevoegen](/docs/commerce-admin/content-design/elements/pages/page-add.html)

Paginahiërarchie:

* [Overzicht](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [Een knooppunt toevoegen](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
