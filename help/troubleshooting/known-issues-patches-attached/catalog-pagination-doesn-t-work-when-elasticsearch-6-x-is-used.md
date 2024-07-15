---
title: Paginering van catalogus werkt niet met Elasticsearch 6.x
description: Dit artikel bevat een patch voor het Adobe Commerce-probleem waarbij de paginering van catalogi niet werkt op Elasticsearch 6.x.
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Paginering van catalogus werkt niet met Elasticsearch 6.x

Dit artikel bevat een patch voor het Adobe Commerce-probleem waarbij de paginering van catalogi niet werkt op Elasticsearch 6.x.

De patch hieronder verhelpt problemen die gebruikers van Adobe Commerce 2.3.3 ervaren bij implementaties waarbij Elasticsearch 6.x wordt gebruikt als zoekprogramma voor catalogi. Gebruikers zien een foutbericht wanneer ze voorbij de eerste pagina met zoekresultaten proberen te navigeren.

Nadat deze patch is geïnstalleerd, kunnen gebruikers door alle zoekresultaten bladeren.

## Betrokken producten en versies

* Adobe Commerce over wolkeninfrastructuur 2.3.3
* Adobe Commerce op locatie 2.3.3
* Magento Open Source 2.3.3
* Elasticsearch 6.x

## Probleem

Er is een probleem ontdekt in Magento Open Source, Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur waar de paginering van de resultatenpagina Zoeken niet werkt als u van pagina verandert.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren.
1. Schakel Elasticseach 6 in als zoekengine voor catalogi.
1. Voeg een aantal producten aan Categorie toe die voorbij de 1 paginalimiet in Admin gaat. **Nota**: 12 is het standaardaantal producten die per pagina in Adobe Commerce 2.3.3 worden getoond.
1. Open Categorie op winkel (zoekresultaten of rubriekpagina) en ga naar pagina 2.

<u> Verwacht resultaat </u>:

Producten moeten op de tweede pagina worden weergegeven.

<u> Werkelijk resultaat </u>:

**&quot;***wij kunnen geen producten vinden die de selectie*** aanpassen&quot;** bericht wordt getoond op de tweede pagina.

## Oplossing

Als u het probleem wilt verhelpen, past u de patch toe die aan dit artikel is gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[ de pagineringskwestie van de Catalogus van de Download op Elasticsearch 6.x flard ](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) - het flard is compatibel met alle beïnvloede versies en versies.

>[!WARNING]
>
>Adobe raadt ten zeerste aan de pleister zo snel mogelijk aan te brengen, zelfs als u geen symptomen hebt ondervonden.

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) voor instructies wordt verstrekt.

## Bijgevoegde bestanden
