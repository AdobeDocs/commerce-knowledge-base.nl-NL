---
title: Elasticsearch-service wordt niet uitgevoerd
description: Dit artikel biedt oplossingen voor fouten die u kunt ervaren wanneer de service Elasticsearch (ES) niet wordt uitgevoerd (meestal als gevolg van vastlopen). Symptomen kunnen fouten bevatten bij het uitvoeren van gezondheidscontroles met krullen, opnieuw indexeren met behulp van de opdrachtregel, Uitzondering en PHP-fouten en fouten op productpagina's. De tabel bevat fouten en koppelingen naar bronnen die moeten worden opgelost. Eén symptoom kan verschillende oorzaken hebben.
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch-service wordt niet uitgevoerd

Dit artikel biedt oplossingen voor fouten die u kunt ervaren wanneer de service Elasticsearch (ES) niet wordt uitgevoerd (meestal als gevolg van vastlopen). Symptomen kunnen fouten bevatten bij het uitvoeren van gezondheidscontroles met krullen, opnieuw indexeren met behulp van de opdrachtregel, Uitzondering en PHP-fouten en fouten op productpagina&#39;s. De tabel bevat fouten en koppelingen naar bronnen die moeten worden opgelost. Eén symptoom kan verschillende oorzaken hebben.

## Elasticsearch versiecompatibiliteit met Adobe Commerce

* Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur:

   * v2.2.3+ ondersteunt ES 5.x
   * v2.2.8+ en v2.3.1+ ondersteunen ES 6.x
   * ES v2.x en v5.x worden niet geadviseerd wegens [ Eind van Leven ](https://www.elastic.co/support/eol). Nochtans, als u Adobe Commerce v2.3.1 hebt en ES 2.x of ES 5.x wilt gebruiken, moet u [ de Elasticsearch veranderen php Cliënt ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/search/overview-search).

* Magento Open Source v2.3.0+ ondersteunt ES 5.x en 6.x (maar 6.x wordt aanbevolen).

<table>
<tr>
<th>Symptomen wanneer de dienst ES niet loopt</th>
<th>Details</th>
<th>Bronnen</th>
</tr>
<tr>
<td rowspan="3">Uitzonderingsfouten</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html?lang=nl-NL"> Elasticsearch 5 wordt gevormd, maar de onderzoekspagina laadt niet met "de gegevens van het Gebied is gehandicapt..."fout </a> in onze basis van de steunkennis.
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
Elasticsuite-indices worden niet verwijderd.  Zie <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=nl-NL"> ElasticSuite die indexen volgen veroorzaakt problemen met Elasticsearch </a> in onze basis van de steunkennis.
 </td>
</tr>
<tr>
<td>PHP-fout</td>
<td>
<i> Geen levende knopen die in uw cluster"worden gevonden,"1":"#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>Bronnen voor onvoldoende schijfruimte:<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">8 tips voor het oplossen van problemen met Linux- en Unix-systemen op de vaste schijf, zoals de schijf vol of kan niet naar de schijf schrijven</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfout: df zegt dat de schijf vol is, maar niet</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com: Waar is de schijfruimte gebleven voor Linux?</a></li>
<li>Logbestanden worden niet regelmatig genoeg gearchiveerd. Zie <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/action-logs/action-log-archive"> het Archief van het Logboek </a> in onze ontwikkelaardocumentatie vormen.</li>
<li>Bestandssysteemmappen zijn niet geoptimaliseerd. Zie <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization"> Optimalisering van het Dossier </a> in onze ontwikkelaarsdocumentatie.</li>
<li>Als de oplossingen in de bovenstaande documentatie het probleem niet oplossen, kunt u contact opnemen met het accountteam van de Adobe om extra opslagruimte aan te vragen.</li>
</ul>
</li>
<li>Als uw schijf niet uit opslag maar u nog de foutenmeldingen in de linkerkolom heeft gekregen, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket"> een steunkaartje </a> voorleggen.</li>
</ul>
<ul>
<li>Zie <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=nl-NL"> ElasticSuite die indexen volgen veroorzaakt problemen met Elasticsearch </a> in onze basis van de steunkennis.
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> fout</td>
<td>Het in werking stellen van het <code>curl</code> bevel om de gezondheid van de Elasticsearch te controleren:<code>curl -m1 localhost:9200/_cluster/health?pretty</code> (of <code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code> voor de rekeningen van de Aanzet) veroorzaakt deze fout: <i> Fout: krulling: (7) Kon er niet in om met localhost haven 9200 te verbinden: De verbinding weigerde </i> </td>
</tr>
<tr>
<td>Opdrachtregelfout</td>
<td>Het lopen <code>$ bin/magento indexer:reindex catalogsearch_fulltext</code> veroorzaakt deze fout <i> het proces van de indexeerder van het Onderzoek van de Catalogus onbekende fout:
        Geen levende knopen die in uw cluster worden gevonden </i>
</td>
</tr>
<tr>
<td>Fout op productpagina's
</td>
<td><i>Er is een fout opgetreden bij het verwerken van uw verzoek.
      Afdrukken met uitzondering is om beveiligingsredenen standaard uitgeschakeld</code></i>
</tr>
</table>
