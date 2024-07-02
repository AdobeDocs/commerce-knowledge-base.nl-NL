---
title: Kan de zoekmachine niet wijzigen met Commerce Admin (menu Zoekmachine is niet toegankelijk)
description: Dit artikel biedt een oplossing voor het wijzigen van de zoekengine van Adobe Commerce met behulp van Commerce Admin als het veld Zoekengine niet wordt weergegeven of als het selectievakje Systeemwaarde gebruiken grijs en niet toegankelijk is.
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: e9f009cf4e072dcd9784693c10a4c16746af3cc5
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Kan de zoekmachine niet wijzigen met Commerce Admin (menu Zoekmachine is niet toegankelijk)

>[!WARNING]
>
> [De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md). U moet de Elasticsearch gastheeropstelling hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd.
> 
> Zie:
> [Elasticsearch installeren en configureren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch).
> [Openssearch installeren en configureren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [Live zoeken installeren en configureren](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

Dit artikel biedt een oplossing voor het wijzigen van de Adobe Commerce Search Engine met behulp van Commerce Admin als de **Zoekmachine** wordt niet weergegeven of **Systeemwaarde gebruiken** het selectievakje is grijs weergegeven en is niet toegankelijk.

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

1. Meld u als beheerder aan bij de beheerder.
1. Klik in de linkerzijbalk van de Admin-beheerder op **Winkels**. Vervolgens, onder **Instellingen**, kiest u **Configuratie**.
1. In het linkerdeelvenster onder **Catalogus,** kiezen **Catalogus**.
1. Breid uit **Catalogus zoeken** sectie.    ![catalog_menu.png](assets/catalog_menu.png)
1. Ga naar de **Zoekmachine** veld en selectie verwijderen uit **Systeemwaarde gebruiken** selectievakje.
1. Klik op de knop **Zoekmachine** en selecteert u een van de beschikbare opties.    ![search_engine_menu.png](assets/search_engine_menu.png)
1. Klikken **Config opslaan** rechtsboven op de pagina.

## Problemen met Adobe Commerce op locatie

### Probleem 1: het veld Zoekmachine wordt niet weergegeven

Wanneer u toegang hebt tot **Catalogus zoeken** de **Zoekmachine** wordt helemaal niet weergegeven.

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### Oorzaak: Winkelweergave is geen standaardconfiguratie

De winkelweergave voor de beheerder is ingesteld op een andere waarde dan *Standaardconfiguratie*.

De zoekmachine is een algemene configuratie die is ingesteld op toepassingsniveau, niet op het winkelbereik. Winkels in een Adobe Commerce-toepassing kunnen geen andere zoekmachines gebruiken.

### Oplossing: de mening van de Opslag plaatsen aan Standaard Config

1. Meld u als beheerder aan bij de beheerder.
1. Klik in de linkerzijbalk van de Admin-beheerder op **Winkels**. Vervolgens, onder **Instellingen**, kiest u **Configuratie**.
1. Klik in de linkerbovenhoek op de knop **Winkelweergave** selector en kies *Standaardconfiguratie*.
1. Klikken **OK** in het bevestigingsdialoogvenster om wijziging in de winkelweergave goed te keuren.

![change_store_view.png](assets/change_store_view.png)

**Verwante documentatie:** [Bereik wijzigen](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope) in onze gebruikershandleiding.

### Uitgave 2: Kan &quot;Systeemwaarde gebruiken&quot; niet uitschakelen

Wanneer u toegang hebt tot **Catalogus zoeken** van de Admin, de **Systeemwaarde gebruiken** het selectievakje is grijs weergegeven, zodat u de selectie van het selectievakje niet kunt verwijderen en de zoekfunctie later kunt wijzigen.

### Oorzaak

De standaardzoekmachine is geconfigureerd op het niveau van de toepassingsconfiguratie in de `app/etc/env.php` of `app/etc/config.php` en kan dus niet worden gewijzigd met de beheerfunctie.

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

Verwijder de sectie met de standaardconfiguratie van de zoekmachine uit de `app/etc/env.php` of de `app/etc/config.php` configuratiebestanden.

### Verwante artikelen in onze ontwikkelaarsdocumentatie

[Adobe Commerce-configuratiebestanden](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html) in Adobe Commerce-configuratiegids

## Adobe Commerce over cloudinfrastructuur

Wisselende zoekprogramma&#39;s met de Admin zijn niet beschikbaar in Adobe Commerce op cloudinfrastructuur vanwege de manier waarop de cloudinfrastructuur is georganiseerd.

Tijdens het implementatieproces controleert de Adobe Commerce op implementatiescripts van de cloudinfrastructuur of Elasticsearch is gedeclareerd in de `MAGENTO_CLOUD_RELATIONSHIPS` variabele. Indien gedeclareerd, wordt Elasticsearch geselecteerd als de actieve zoekmachine en automatisch geconfigureerd; de [MySQL-zoekprogramma](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md) ontoegankelijk wordt in de Admin. Als de relatie van de Elasticsearch niet is verklaard, wordt MySQL geplaatst aan actief, en de Elasticsearch wordt ontoegankelijk.

Het wordt niet aanbevolen om de `app/etc/env.php` of de `app/etc/config.php` configuratiebestanden rechtstreeks in uw cloud-omgeving te configureren; daarom is het niet van toepassing op uw cloud-project om de Elasticsearch-engine in Admin weer te geven (de oplossing die we in de vorige sectie aanbevelen).

### Zoekmachine wijzigen in een testomgeving en productieomgeving

Voordat u van MySQL naar Elasticsearch overschakelt op uw Staging- en Productomgevingen, moet u ervoor zorgen dat u eerder [een ondersteuningsticket hebben ingediend](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het verzoek om Elasticsearch op het milieu toe te staan en het ticket is met succes opgelost .

Als u de zoekfunctie wilt wijzigen die wordt gebruikt in uw staging- en productieomgeving, wijzigt u de instelling `SEARCH_CONFIGURATION` omgevingsvariabele in uw `.magento.env.yaml` bestand in uw lokale omgeving en druk vervolgens op de wijzigingen in de omgevingen Integratie en Staging/Production om van kracht te worden.

Als u overschakelt naar Elasticsearch 7, de variabele SEARCH\_CONFIGURATION in het resulterende `.magento.env.yaml` Het bestand kan er als volgt uitzien:

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

Als u overschakelt naar [Openssearch (in 2.4.6 en hoger)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search) de variabele SEARCH\_CONFIGURATION in het resulterende `.magento.env.yaml` Het bestand kan er als volgt uitzien:

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

Als u [schakelen naar Live zoeken](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch), de variabele SEARCH\_CONFIGURATION in het resultaat `.magento.env.yaml` Het bestand kan er als volgt uitzien:

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

* [Service Elasticsearch instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [Samenstellen en implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) (documentatie over de `.magento.env.yaml` configuratiebestand)
* [Variabelen implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) ([Sectie ZOEKEN\_CONFIGURATIE](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration))
* [Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) (documentatie over de `.magento/services.yaml` configuratiebestand)
* [Live zoeken](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
