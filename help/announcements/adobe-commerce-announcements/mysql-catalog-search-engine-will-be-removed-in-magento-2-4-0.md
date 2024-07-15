---
title: De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0
description: Adobe Commerce op locatie, Adobe Commerce op cloudinfrastructuur en Magento Open Source 2.4.0 worden de komende maanden vrijgegeven. Voor Adobe Commerce on-premisse en Magento Open Source versie 2.4.0 zal de Elasticsearch 6.x of 7.x een vereiste component zijn, en MySQL onderzoeksmotor zal worden verwijderd. In Adobe Commerce op cloudinfrastructuur is Elasticsearch al vereist.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# De zoekfunctie voor MySQL-catalogus wordt verwijderd uit Adobe Commerce 2.4.0

Adobe Commerce op locatie, Adobe Commerce op cloudinfrastructuur en Magento Open Source 2.4.0 worden de komende maanden vrijgegeven. Voor Adobe Commerce on-premisse en Magento Open Source versie 2.4.0 zal de Elasticsearch 6.x of 7.x een vereiste component zijn, en MySQL onderzoeksmotor zal worden verwijderd. In Adobe Commerce op cloudinfrastructuur is Elasticsearch al vereist.

>[!WARNING]
>
>Als u Elasticsearch 6/7 niet installeert/configureert voordat u probeert een upgrade uit te voeren, kunnen er ernstige problemen optreden met Adobe Commerce. Houd er rekening mee dat serviceupgrades op Adobe Commerce op cloudinfrastructuur niet naar de productieomgeving kunnen worden verplaatst zonder dat het infrastructuurteam hiervan 48 kantooruren op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen detailend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

De reden voor het verwijderen van MySQL zoekmachine is dat Elasticsearch betere zoekmogelijkheden biedt en optimaliseert de catalogusprestaties.

## Betrokken producten en versies:

* Adobe Commerce op locatie v2.4.0
* Magento Open Source v2.4.0

## Upgrade uitvoeren:

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Zoekmachine</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Handeling</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">U moet Elasticsearch installeren. Zie <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html"> Elasticsearch </a> in onze ontwikkelaarsdocumentatie installeren en vormen.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (zonder vermelde versie)</td>
<td style="width: 478.2px;">U gebruikt Elasticsearch 2 en moet bijwerken naar Elasticsearch 7 (voorkeur) of 6. Zie <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html#es-upgrade6"> Bevorderend Elasticsearch </a> en <a href="https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html"> vormen Commerce om Elasticsearch </a> in onze ontwikkelaarsdocumentatie voor details te gebruiken.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 heeft zijn <a href="https://www.elastic.co/support/eol"> Eind van het Leven </a> bereikt en is afgekeurd in Adobe Commerce 2.4.0. Bijwerken naar Elasticsearch 7 (voorkeur) of 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 of 7</td>
<td style="width: 478.2px;">U hoeft geen aanvullende stappen uit te voeren voordat u de upgrade naar Adobe Commerce 2.4.0 uitvoert.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Extensie door derden</td>
<td style="width: 478.2px;">U hoeft Elasticsearch niet te installeren. Adobe Commerce raadt u aan contact op te nemen met de leverancier van het zoekprogramma om te bepalen of uw extensie volledig compatibel is met Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Installatie:

Wanneer Adobe Commerce op-gebouw en Magento Open Source 2.4.0 wordt vrijgegeven, zal de Elasticsearch een vereiste component zijn, zodat moet u een de gastheeropstelling hebben van de Elasticsearch en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Zie [ installeer en vorm Elasticsearch ](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html) in onze ontwikkelaarsdocumentatie.

Standaard gebruikt Adobe Commerce search Elasticsearch 7 als zoekengine en probeert het verbinding te maken met een server op localhost:9200. Elasticsearch 6.x wordt ook ondersteund. Als uw configuratie niet de gebreken aanpast, kunt u deze montages vormen gebruikend argumenten die tot `setup:install` worden overgegaan, op ongeveer de zelfde manier de gegevensbestandverbinding wordt gevormd.

Bijvoorbeeld: `setup:install --elasticsearch-host=es.mystore.com`

Tijdens de installatie wordt de verbinding met de Elasticsearch gecontroleerd en mislukt de installatie als Adobe Commerce geen verbinding kan maken met een Elasticsearch-host. Als dit voorkomt, controleer dat uw Elasticsearch in gebruik is, en dat u de correcte verbindingsparameters hebt verstrekt.
