---
title: Kan de zoekmachine niet wijzigen met Commerce Admin (menu Zoekmachine is niet toegankelijk)
description: Dit artikel biedt een oplossing voor het wijzigen van de zoekengine van Adobe Commerce met behulp van Commerce Admin als het veld Zoekengine niet wordt weergegeven of als het selectievakje Systeemwaarde gebruiken grijs en niet toegankelijk is.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ea7bbef7fec556f9a90151be9cf1077f5cfac45
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Kan de zoekmachine niet wijzigen met Commerce Admin (menu Zoekmachine is niet toegankelijk)

>[!WARNING]
>
> [ MySQL de motor van het catalogusonderzoek zal in Adobe Commerce 2.4.0 ](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) worden verwijderd. U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd.
> 
> Zie:
> [Installeer en vorm Elasticsearch ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Openssearch installeren en configureren ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Live zoeken installeren en configureren ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Dit artikel verstrekt een oplossing om de Motor van het Onderzoek van Adobe Commerce te veranderen gebruikend Commerce Admin als het **gebied van de Motor van het Onderzoek** niet wordt getoond of het **het systeemwaarde** checkbox van het Gebruik uit grayed en niet toegankelijk is.

In dit artikel:

* [Betrokken versies](#affected-versions)
* [Zoekmachine wijzigen met Commerce Admin (stappen)](#change-search-engine-using-magento-admin-steps)
* [Problemen met Adobe Commerce op locatie](#magento-commerce-on-premise)
* [Adobe Commerce over cloudinfrastructuur](#magento-commerce-cloud)

## Betrokken versies

* Adobe Commerce ter plaatse: 2.4.X
* Adobe Commerce op cloudinfrastructuur:
   * Versie: 2.4.X
   * Starter- en Pro-planarchitectuur
* MySQL, Elasticsearch, Openssearch, Live Search: alle ondersteunde versies

## Zoekmachine wijzigen met de beheerfunctie (stappen)

1. Meld u als beheerder aan bij de **[!UICONTROL Admin]** .
1. Klik links in de zijbalk van **[!UICONTROL Admin]** op **[!UICONTROL Stores]** .
1. Kies onder **[!UICONTROL Settings]** de optie **[!UICONTROL Configuration]** .
1. Navigeer naar het deelvenster links onder **[!UICONTROL Catalog]en kies** . **[!UICONTROL Catalog]**
1. Vouw de sectie **[!UICONTROL Catalog Search]** uit.    ![ catalog_menu.png ](assets/catalog_menu.png)
1. Ga naar het veld **[!UICONTROL Search Engine]** en verwijder de selectie uit het selectievakje **[!UICONTROL Use system value]** .
1. Klik op het menu **[!UICONTROL Search Engine]** en selecteer een van de beschikbare opties zoals hieronder wordt weergegeven.    ![ search_engine_menu.png ](assets/search_engine_menu.png)
1. Klik op **[!UICONTROL Save Config]** rechtsboven op de pagina.

## Problemen met Adobe Commerce op locatie

### Probleem 1: het veld Zoekmachine wordt niet weergegeven

Wanneer u tot het **sectie van het Onderzoek van de Catalogus toegang hebt**, wordt het **menu van de Motor van het Onderzoek** niet getoond bij allen.

![ search_engine_not_displayed.png ](assets/search_engine_not_displayed.png)

### Oorzaak: Winkelweergave is geen standaardconfiguratie

De Mening van de Opslag voor Admin is geplaatst aan om het even welke waarde buiten *StandaardConfig*.

De zoekmachine is een algemene configuratie die is ingesteld op toepassingsniveau, niet op het winkelbereik. Winkels in een Adobe Commerce-toepassing kunnen geen andere zoekmachines gebruiken.

### Oplossing: de mening van de Opslag plaatsen aan Standaard Config

1. Meld u als beheerder aan bij de **[!UICONTROL Admin]** .
1. Klik links in de zijbalk van **[!UICONTROL Admin]** op **[!UICONTROL Stores]** .
1. Navigeer naar **[!UICONTROL Settings]** en kies **[!UICONTROL Configuration]** .
1. In de upper-left hoek, klik de **[!UICONTROL Store View]** selecteur en kies **[!UICONTROL *Standaard Config *]**.
1. Klik op **[!UICONTROL OK]** in het bevestigingsdialoogvenster om de wijzigingen in de winkelweergave goed te keuren.

![ change_store_view.png ](assets/change_store_view.png)

**Verwante documentatie:** [ Veranderend Toepassingsgebied ](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) in onze gebruikersgids.

### Uitgave 2: Kan &quot;Systeemwaarde gebruiken&quot; niet uitschakelen

Wanneer u tot het **gedeelte van het Onderzoek van de Catalogus** van Admin toegang hebt, wordt het **systeemwaarde van het Gebruik** checkbox grijs zodat kunt u geen selectie uit checkbox verwijderen om de onderzoeksmotor later te veranderen.

### Oorzaak

De standaardzoekmachine is geconfigureerd op het niveau van de toepassingsconfiguratie in de `app/etc/env.php` - of `app/etc/config.php` -bestanden en kan daarom niet worden gewijzigd met de beheerfunctie.

Voorbeeld van de sectie met standaardconfiguratie van zoekprogramma&#39;s:

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### Oplossing

Verwijder de sectie met de standaardconfiguratie van de zoekmachine uit de `app/etc/env.php` - of `app/etc/config.php` -configuratiebestanden.

### Verwante artikelen in onze ontwikkelaarsdocumentatie

[ de configuratiedossiers van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) in de Gids van de Configuratie van Adobe Commerce

## Adobe Commerce over cloudinfrastructuur

Wisselende zoekprogramma&#39;s met de Admin zijn niet beschikbaar in Adobe Commerce op cloudinfrastructuur vanwege de manier waarop de cloudinfrastructuur is georganiseerd.

Tijdens het implementatieproces controleert de Adobe Commerce op implementatiescripts van de cloud-infrastructuur of Elasticsearch is gedeclareerd in de variabele `MAGENTO_CLOUD_RELATIONSHIPS` . Als verklaard, wordt de Elasticsearch geselecteerd als actieve onderzoeksmotor en automatisch gevormd; de [ MySQL onderzoeksmotor ](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) wordt ontoegankelijk in Admin. Als de relatie van de Elasticsearch niet is verklaard, wordt MySQL geplaatst aan actief, en de Elasticsearch wordt ontoegankelijk.

Het wordt afgeraden de `app/etc/env.php` - of `app/etc/config.php` -configuratiebestanden rechtstreeks in uw cloud-omgeving te bewerken. Daarom is het niet van toepassing om deze bestanden te wijzigen zodat de Elasticsearch-engine in Admin wordt weergegeven (de oplossing die we in de vorige sectie aanbevelen).

### Zoekmachine wijzigen in een testomgeving en productieomgeving

Alvorens de onderzoeksmotor van MySQL aan Elasticsearch op uw het Opvoeren en milieu&#39;s van de Productie te schakelen, zorg ervoor u eerder [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) verzoekend hebt voorgelegd om Elasticsearch op het milieu toe te laten en het kaartje met succes is opgelost.

Als u het zoekprogramma wilt wijzigen dat wordt gebruikt in uw staging- en productieomgeving, wijzigt u de omgevingsvariabele `SEARCH_CONFIGURATION` in het `.magento.env.yaml` -bestand in uw lokale omgeving en duwt u vervolgens de wijzigingen in de omgevingen Integratie en Staging/Productie om van kracht te worden.

Als u overschakelt naar Elasticsearch 7, ziet de variabele SEARCH\_CONFIGURATION in het resulterende `.magento.env.yaml` -bestand er mogelijk als volgt uit:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Als u aan [ OpenSearch (in 2.4.6 en later,) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) schakelt zou de variabele ZOEKEN \_CONFIGURATION in het resulterende `.magento.env.yaml` dossier als volgt kunnen kijken:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

Als u [ overschakelt naar Levend Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), zou de variabele ZOEKEN \_CONFIGURATION in het resulterende `.magento.env.yaml` dossier als volgt kunnen kijken:

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### Gerelateerde documentatie

#### Kennisbank voor ondersteuning

* [Elasticsearch inschakelen in cloud](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### Documentatie voor ontwikkelaars

* [ de dienst van de Elasticsearch van de opstelling ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [ bouwt en stelt ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentatie over het `.magento.env.yaml` configuratiedossier op)
* [ stelt variabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) op ([ ZOEKEN \_CONFIGURATION sectie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [ de Diensten ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentatie over het `.magento/services.yaml` configuratiedossier)
* [ Levend Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
