---
title: Prestaties oplossen met New Relic op Adobe Commerce
description: 'Dit artikel bevat stappen voor het oplossen van problemen met Adobe Commerce over de prestaties van cloudinfrastructuur met behulp van New Relic. Het biedt ook middelen voor verdere informatie. Hier volgt een lijst met problemen. Klik om het oplossen van problemenstappen in onze steun kennisbank te zien:'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
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
<p>Je New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex score</a> meet de tevredenheid van gebruikers met de reactietijd van uw Webtoepassingen en de diensten.</p>
</td>
<td>
<p>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Overzicht. Rechts op de pagina Overzicht ziet u de grafiek van de Apdex-score. Een score van de Index van 0.5 of minder is een punt van zorg en rechtvaardigt onderzoek: Web-transactie tijden (serververzoeken):</p>
<ol>
<ol>
<li>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Selecteer een app) &gt; Overzicht. Zorg ervoor de filter aan de transactietijd van het Web op de belangrijkste grafiek drop-down filter wordt geplaatst. Zoek hieronder in de tabel Transacties naar de tijd van de App-server. Controleer of u langdurige of verdachte transacties hebt.</li>
<li>Onderzoek hen individueel door naar Controle &gt; Transacties te gaan en zorg ervoor om de filters voor Web en het Meest tijdrovend te plaatsen<em>.</em>
</li>
<li>Zoek vervolgens naar modules van derden die middelen verbruiken: betalingsproviders, ERP, enz.</li>
<li>In het onderdeel Controle van APM:<ol>
<li>Klik op Transacties.</li>
<li>Schuif omlaag en klik op Alle transacties tonen.</li>
<li>U kunt transacties sorteren op <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">diverse parameters</a> en ga naar degenen die verdacht zijn.</li>
<li>Controleer de transacties met een lage Apdex-score, een ongewoon hoge telling of een hoge Gem-tijd, of Verspreid %.</li>
<li>Klik op elke afzonderlijke transactie. Als u het probleem niet kunt oplossen, <a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">een ondersteuningsticket indienen.</a>
</li>
<li>Als u verder moet onderzoeken, overweeg het controleren van niet-Webtransacties.</li>
</ol>
</li>
</ol>
</ol>
<p>Tijd niet-webtransactie (bewerkingen en achtergrondtaken):</p>
<ol>
<ol>
<li>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; (Selecteer een app) &gt; Overzicht. Zorg ervoor dat u Tijd voor niet-webtransacties selecteert in het vervolgkeuzefilter voor de hoofdgrafiek. Klik op afzonderlijke transacties in de tabel Transacties. Zoek naar langdurige of verdachte transacties. Hieronder vallen back-endtaken, snijtaken of import-/exporttaken, waaronder taken van derden.</li>
</ol>
</ol>
</td>
<td>
<p>Voor meer informatie over de New Relic Apdex score raadpleegt u <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic Documentation &gt; APM Apdex &gt; Measurement user atisation</a>. U kunt ook verwijzen naar <a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Beheerde waarschuwingen voor Adobe Commerce: waarschuwing van Apdex</a> in onze kennisbasis voor ondersteuning.</p>
</td>
</tr>
<tr>
<td>
<p>Hoog CPU-gebruik:</p>
<p>Het hoge gebruik van cpu kan erop wijzen dat er een bijzonder drukke dienst, zoals MySQL, Redis, enz. is.</p>
</td>
<td>
<ol>
<li>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructuur &gt; Processen.</li>
<li>Bekijk CPU-grafieken om te zien of er een vast of duur proces is dat meer dan 100% CPU-tijd gebruikt en vergelijk dit met processortelling op de instantie. Let op pieken in het gebruik van bronnen. Het wordt niet aanbevolen een proces te doden tenzij het een geplakt kruin is.</li>
</ol>
</td>
<td>
<p>Meer informatie over prestatiesmetriek, in het bijzonder het percentage van cpu, I/O bytes, en geheugengebruik voor individueel of groepen processen, verwijs naar <a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic Documentation &gt; Infrastructure UI page &gt; Infrastructure Host page &gt; Processes tab</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Hoge I/O-activiteiten: voor elke klant zou dit aantal afzonderlijk zijn, maar aanzienlijk anders dan het gemiddelde.</p>
</td>
<td>
<p>Er is een ongewone piek in vergelijking met eerdere gemiddelde I/O-bewerkingen:</p>
<ol>
<li>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; Infrastructuur &gt; Processen.</li>
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
<li>Aanmelden bij <a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; Overzicht. Controleer of het filter is ingesteld op de tijd van webtransacties bij het vervolgkeuzelijstfilter.</li>
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

Opmerking: <code>BIJWERKEN</code> of <code>INSERT</code>query&#39;s zijn de meest CPU-verbruikende query&#39;s.</li>
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
<p>Voor meer informatie over het onderzoeken van specifieke prestatiesproblemen, verwijs naar <a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic Documentation &gt; APM UI pages &gt; Transactions page &gt; Use boor-down functions</a>.</p>
</td>
</tr>
</tbody>
</table>
