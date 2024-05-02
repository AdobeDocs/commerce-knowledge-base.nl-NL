---
title: Problemen met New Relic op Adobe Commerce op cloudinfrastructuur oplossen
description: Dit artikel bevat bronnen voor het oplossen van problemen met New Relic op Adobe Commerce op cloudinfrastructuur.
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Problemen met New Relic op Adobe Commerce op cloudinfrastructuur oplossen

Dit artikel bevat bronnen voor het oplossen van problemen met New Relic op Adobe Commerce op cloudinfrastructuur.

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>Probleem</strong></td>
<td class="wysiwyg-text-align-center"><strong>Oorzaak</strong></td>
<td class="wysiwyg-text-align-center"><strong>Bronnen</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Toegangsproblemen</td>
</tr>
<tr>
<td>
<p><u>Kan geen projecten zien in New Relic.</u></p>
<p>Aanmelden bij <em>New Relic</em> maar u kunt geen projecten zien die u recht zouden moeten hebben op weergave/toegang.</p>
</td>
<td>
<p>In die gevallen, moet een admin gebruiker u aan het project toevoegen.</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">Toegang tot New Relic-services</a> in onze kennisbasis voor ondersteuning.</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">Gegevensproblemen</td>
</tr>
<tr>
<td>
<p><u>Ontbrekende gegevens na installatie.</u></p>
<p>Gebruik de <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic Diagnostics-hulpprogramma</a> proberen de oorzaak te achterhalen. Als dit niet helpt, kijk agentenspecifieke oplossingen. De koppelingen naar artikelen met deze oplossingen staan in de rechterkolom.</p>
</td>
<td>
<p>Ontbrekende gegevens kunnen verschillende oorzaken hebben. Mogelijk moet u:</p>
<ul>
<li>Controleer of de agent is geïnstalleerd.</li>
<li>Controleer uw toepassingsnaam en licentiecode.</li>
<li>Start de webserver opnieuw.</li>
<li>Controleer of uw systeem voldoet aan de compatibiliteitsvereisten.</li>
<li>INI-instellingen.</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic Documentation &gt; APM Agents &gt; Not Seing Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic Documentation &gt; New Relic Browser &gt; Not Seing Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic Documentation &gt; New Relic Infrastructure &gt; Not Seing Data</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic Documentation &gt; New Relic Mobile &gt; Not Seing Data</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>Transactietijdstempelafwijking.</u> U kunt moeite hebben om lange transacties (meer dan 5 minuten) te vinden met de gebruikersinterface van New Relic. Het is ook mogelijk dat transacties buiten het verwachte tijdkader worden weergegeven.</p>
</td>
<td>
<p>De gebruikersinterface van New Relic geeft de tijd van het einde van de transactie weer, niet de tijd waarop de transactie is gestart.</p>
</td>
<td>
<p>Als u het begin van de transactie wilt berekenen met de gebruikersinterface van New Relic, controleert u de duur van de transactie. Trek het bedrag voor de duur af van het tijdstempel (einde van de transactie) dat door de gebruikersinterface van New Relic is opgegeven.</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> vragen met speciale tekens zoals <code>|</code> en <code>%</code> werken niet</u>.</p>
</td>
<td>
<p>De functie 'copy to curl' van New Relic in NerdGraph biedt momenteel geen manier om speciale tekens zoals <code>|</code> en <code>%</code>.</p>
</td>
<td>
<p>Gebruik een andere API-bibliotheek om het probleem op te lossen met speciale tekens. Bijvoorbeeld GraphQLClient Library for Graphql API on Python, of Apache.commons door Java Language-aanroepen. Clientbibliotheken controleren op <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>Problemen met de weergave van grafieken en dashboard.</u></p>
</td>
<td>
<p>Los ontbrekende grafieken op door New Relic-domeinen aan de lijst van gewenste personen toe te voegen of verwijder de browserextensie die de problemen veroorzaakt.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic Documentation &gt; Charts missing or not render</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">PHP Agent Issues</td>
</tr>
<tr>
<td>
<p><u>PHP agent geeft niet het juiste aantal exemplaren weer.</u></p>
</td>
<td>
<p>Het aantal instanties kan afhankelijk van back-end processen en doorvoer toenemen. Verschillen tussen serverwaarden kunnen het gevolg zijn van processen die op de ene server worden uitgevoerd, maar niet op de andere server.</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic Documentation &gt; Troubleshoot the PHP agent instance count</a> </p>
</td>
</tr>
</tbody>
</table>
