---
title: Ingevalideerde cache veroorzaakt vertraging van responstijd
description: Dit artikel biedt een oplossing voor het voorkomen van cachevalidatie, wat de trage prestaties van een Adobe Commerce-winkel kan veroorzaken.
exl-id: 7cb6a39f-923b-4acc-965d-23cf7b52c25a
feature: Cache, Catalog Management, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Ingevalideerde cache veroorzaakt vertraging van responstijd

Dit artikel biedt een oplossing voor het voorkomen van cachevalidatie, wat de trage prestaties van een Adobe Commerce-winkel kan veroorzaken.

BETROKKEN PRODUCTEN EN VERSIES:

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Adobe Commerce op cloud-infrastructuur 2.2.x, 2.3.x

## Probleem

Langzame reactie van de site.

## Oorzaak

De lange reactietijd kan worden veroorzaakt door het geheime voorgeheugen dat wordt ongeldig gemaakt (leeggemaakt).

De cache wordt gebruikt om snelle reacties te genereren op de verzoeken van de sitebezoekers. Als er geen geschikte cachegegevens beschikbaar zijn, haalt de Adobe Commerce-toepassing de gegevens op van de database, berekent en aggregeert de gegevens en slaat deze op in de cacheopslag. Het cacheproductieproces vereist extra systeembronnen die een totale vertraging van de responstijd veroorzaken.

Er zijn twee soorten cache in Adobe Commerce:

1. Intern:
   * slaat gegevens op de server op
   * specifieke gegevens opslaan (configuratie, productdetails, categoriedetails, enz.)
1. Extern:
   * CDN of Varnish (in het geval van Adobe Commerce op cloudinfrastructuur - Fastly CDN)
   * slaat reeds geproduceerde volledige pagina&#39;s op. Bijvoorbeeld catalogus/categorie, catalogus/productpagina&#39;s, enzovoort.

### Controleren of de cache ongeldig is

U vindt informatie over de ongeldig gemaakte cachetypen in het `<install_directory>/var/log/debug.log` -bestand.

Dit doet u als volgt:

1. Openen `<install_directory>/var/log/debug.log`
1. Zoek naar &quot; *cache \_invalidate* &quot;- bericht.
1. Controleer vervolgens het opgegeven label. Dit geeft aan welke cache is leeggemaakt. Er kunnen problemen optreden vanwege de ongeldig gemaakte cache als u bijvoorbeeld een tag ziet waarvoor geen bepaalde id is opgegeven, zoals:
   * `cat_p` - staat voor cache van catalogusproduct.
   * `cat_c` - cachegeheugen voor cataloguscategorieën.
   * `FPC` - cache van volledige pagina.
   * `CONFIG` - configuratiecache.

   Als zelfs een van deze landen zou worden weggespoeld, zou de reactie van de website afnemen. Als de tag een id voor tekeneenheden bevat, bijvoorbeeld `category_product_1258` , geeft dit de cache voor een bepaald product of een bepaalde categorie aan, enzovoort. Cachegeheugen voor spoelen voor een bepaald product of een bepaalde categorie zou er niet toe leiden dat de responstijd aanzienlijk daalt.

Hier volgt een voorbeeld van een `debug.log` met records waarin de cache `cat_p` en `category_product_15044` is verwijderd:

![ steekproef van de inhoud debug.log ](assets/debug_log_sample.png)

Gewoonlijk wordt de cache ongeldig vanwege het volgende:

* Volledige herindex.
* Het knipperen geheime voorgeheugen van CLI, of manueel of gebruikend kruin.

## Aanbeveling

1. Vermijd het leegmaken van de cache van de Commerce CLI.
1. Vorm indexeerders aan **Update door programma** in plaats van **Update op sparen wijze** omdat laatstgenoemde volledige het opnieuw indexeren teweegbrengt. Voor verwijzing, zie [ de indexen beheren > indexen ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers) in onze ontwikkelaarsdocumentatie vormen.
