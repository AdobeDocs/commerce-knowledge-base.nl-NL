---
title: Prestaties oplossen met New Relic op Adobe Commerce
description: 'In dit artikel worden stappen beschreven voor het oplossen van problemen met Adobe Commerce over de prestaties van cloudinfrastructuren met New Relic. Het biedt ook middelen voor verdere informatie. Hier volgt een lijst met problemen. Klik om het oplossen van problemenstappen in onze steun kennisbank te zien:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Prestaties oplossen met New Relic op Adobe Commerce

In dit artikel worden stappen beschreven voor het oplossen van problemen met Adobe Commerce over de prestaties van cloudinfrastructuren met New Relic. Het biedt ook middelen voor verdere informatie. De volgende kwesties die in de onderstaande tabel met aanbevolen bronnen worden behandeld, zijn:

* Low Apdex score
* Hoog CPU-gebruik
* Hoge I/O-bewerkingen
* Uitval

<table>
<tbody>
<tr>
<td>Probleem</td>
<td>Problemen oplossen</td>
<td>Bronnen</td>
</tr>
<tr>
<td>
<p>Low Apdex score:</p>
<p>Uw New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction"> score van de Index </a> meet de tevredenheid van gebruikers met de reactietijd van uw Webtoepassingen en de diensten.</p>
</td>
<td>
<p>U login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; APM &gt; Overzicht. Rechts op de pagina Overzicht ziet u de grafiek van de Apdex-score. Een score van de Index van 0.5 of minder is een punt van zorg en rechtvaardigt onderzoek: Web-transactie tijden (serververzoeken):</p>
<ol>
<ol>
<li>Login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; APM &gt; (Selecteer een app) &gt; Overzicht. Zorg ervoor de filter aan de transactietijd van het Web op de belangrijkste grafiek drop-down filter wordt geplaatst. Zoek hieronder in de tabel Transacties naar de tijd van de App-server. Controleer of u langdurige of verdachte transacties hebt.</li>
<li>Onderzoek hen individueel door te gaan aan Controle &gt; Transacties en zorg ervoor om de filters voor Web en Meest tijdrovend <em> te plaatsen.</em>
</li>
<li>Zoek vervolgens naar modules van derden die middelen verbruiken: betalingsproviders, ERP, enz.</li>
<li>In het onderdeel Controle van APM:<ol>
<li>Klik op Transacties.</li>
<li>Schuif omlaag en klik op Alle transacties tonen.</li>
<li>U kunt transacties door <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view"> diverse parameters </a> sorteren en aan die springen die verdenking veroorzaken.</li>
<li>Controleer de transacties met een lage Apdex-score, een ongewoon hoge telling of een hoge Gem-tijd, of Verspreid %.</li>
<li>Klik op elke afzonderlijke transactie. Als u niet de kwestie kunt oplossen, <a href="https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket"> voorlegt een steunkaartje.</a>
</li>
<li>Als u verder moet onderzoeken, overweeg het controleren van niet-Webtransacties.</li>
</ol>
</li>
</ol>
</ol>
<p>Tijd niet-webtransactie (bewerkingen en achtergrondtaken):</p>
<ol>
<ol>
<li>Login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; APM &gt; (Selecteer een app) &gt; Overzicht. Zorg ervoor dat u Tijd voor niet-webtransacties selecteert in het vervolgkeuzefilter voor de hoofdgrafiek. Klik op afzonderlijke transacties in de tabel Transacties. Zoek naar langdurige of verdachte transacties. Hieronder vallen back-endtaken, snijtaken of import-/exporttaken, waaronder taken van derden.</li>
</ol>
</ol>
</td>
<td>
<p>Meer over de score van de Apdex van New Relic leren, verwijs naar <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction"> Documentatie van New Relic &gt; de Apdex van APM &gt; de gebruikerstevredenheid van de Meetlat </a>. U kunt ook naar <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert"> Beheerde alarm voor Adobe Commerce verwijzen: De waarschuwingsalarm van de Index </a> in onze basis van de steunkennis.</p>
</td>
</tr>
<tr>
<td>
<p>Hoog CPU-gebruik:</p>
<p>Het hoge gebruik van CPU kan erop wijzen dat er een bijzonder drukke dienst, zoals MySQL, Redis, enz. is.</p>
</td>
<td>
<ol>
<li>Login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; Infrastructuur &gt; Processen.</li>
<li>Bekijk CPU-grafieken om te zien of er een vast of duur proces is dat meer dan 100% CPU-tijd gebruikt en vergelijk dit met processortelling op de instantie. Let op pieken in het gebruik van bronnen. Het wordt niet aanbevolen een proces te doden tenzij het een geplakt kruin is.</li>
</ol>
</td>
<td>
<p>Meer over prestatiesmetriek, in het bijzonder CPU percentage, I/O bytes, en geheugengebruik voor individu of groepen processen leren, verwijs naar <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes"> Documentatie van New Relic &gt; de pagina van UI van de Infrastructuur &gt; de pagina van de Gastheer van de Infrastructuur &gt; het lusje van Processen </a>.</p>
</td>
</tr>
<tr>
<td>
<p>Hoge I/O-activiteiten: voor elke klant zou dit aantal afzonderlijk zijn, maar aanzienlijk anders dan het gemiddelde.</p>
</td>
<td>
<p>Er is een ongewone piek in vergelijking met eerdere gemiddelde I/O-bewerkingen:</p>
<ol>
<li>Login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; Infrastructuur &gt; Processen.</li>
<li>Bekijk I/O-leesbytes per tweede grafiek.</li>
<li>Registreer de tijd van de piek.</li>
<li>Klik op APM.</li>
<li>Zorg ervoor dat u de tijd van webtransacties selecteert op het hoofdgrafiekvervolgkeuzefilter.</li>
<li>Stel de tijd in voor de tijd van de opgenomen piek.</li>
<li>Zoek naar transacties die hoge I/O verrichtingen hebben veroorzaakt.</li>
<li>Boor neer in elk Spoor van de Transactie &gt; de details van het Spoor om te vinden wat kwesties zou kunnen veroorzaken.</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>Uitval: New Relic bepaalt uitvallen door Apdex. Er wordt een rode lijn weergegeven in de grafiek van de Apdex-score, die Apdex &lt; 0,4 aangeeft. Dit wordt beschouwd als een stroomstoring.</p>
</td>
<td>
<p>Het onderzoeken van een stroomstoring kan verschillende stappen ondernemen, waarbij web- en niet-webtransacties, databases en transacties van derden worden onderzocht. Webtransacties:</p>
<ol>
<li>Login aan <a href="https://login.newrelic.com/login"> New Relic </a> &gt; APM &gt; Overzicht. Controleer of het filter is ingesteld op de tijd van webtransacties bij het vervolgkeuzelijstfilter.</li>
<li>Verkort handmatig het tijdvenster.</li>
<li>Klik op Transacties. Zorg ervoor dat de filters zijn ingesteld op Web en Meest tijdrovend. Onderzoek de langst lopende transactie.</li>
<li>Als u verder moet onderzoeken, overweeg het controleren van niet-Webtransacties.</li>
</ol>
<p>Transacties buiten het web:</p>
<ol>
<li>Ga terug naar de pagina van het Overzicht en schakel naar Niet-Webtransacties op de drop-down filter.</li>
<li>Transactietransacties bekijken helemaal onder aan de pagina, een voor een.</li>
<li>Afhankelijk van het probleem kan het nodig zijn om een hulpprogramma van derden te gebruiken, zoals een PHP-analyse, om een knelpunt te vinden.</li>
<li>Als u verder moet onderzoeken, overweeg het onderzoeken van gegevensbestandprocessen.</li>
</ol>
<p>Databaseprocessen:</p>
<ol>
<li>Ga op de APM-pagina naar Bewaking &gt; Databases.</li>
<li>Sorteren op Meest tijdrovend.</li>
<li>Bekijk TOP-vragen.

Nota: <code> UPDATE</code> of <code> INSERT</code>query&#39;s zijn de meest CPU-verbruikende query&#39;s.</li>
<li>De schakelaar aan Productie van de Soort door selecteur en zoekt processen die de gegevensbestandproductie aan drop-down hebben veroorzaakt.</li>
<li>Als u verder moet onderzoeken, overweeg de derdediensten.</li>
</ol>
<p>Services van derden:</p>
<ol>
<li>Ga op de APM-pagina naar Bewaking &gt; Externe services.</li>
<li>Selecteer de langzaamste gemiddelde reactietijd van Soort door drop-down lijst.</li>
<li>Zoek naar processen die vlak voor de stroomonderbreking voorkwamen.</li>
</ol>
</td>
<td>
<p>Meer over het onderzoeken van specifieke prestatiesproblemen leren, verwijs naar <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions"> Documentatie van New Relic &gt; de pagina's van APM UI &gt; de pagina van Transacties &gt; boor-benedenfuncties van het Gebruik </a>.</p>
</td>
</tr>
</tbody>
</table>
