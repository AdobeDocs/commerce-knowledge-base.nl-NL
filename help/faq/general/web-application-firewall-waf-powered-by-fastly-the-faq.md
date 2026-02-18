---
title: 'Web Application Firewall (WAF) met snelwerkende kracht: veelgestelde vragen'
description: De Vuurmuren van de Toepassing van het Web (WAFs) verhinderen kwaadwillig verkeer plaatsen en netwerken in te gaan door verkeer tegen een reeks veiligheidsregels te filtreren. Het verkeer dat om het even welke regels teweegbrengt wordt geblokkeerd alvorens het uw plaatsen of netwerk kan beschadigen.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 0%

---

# Web Application Firewall (WAF) met snelwerkende kracht: veelgestelde vragen

## Hoe werkt Adobe Commerce managed cloud WAF (aangedreven door Fastly)?

De Vuurmuren van de Toepassing van het Web (WAFs) verhinderen [&#x200B; kwaadwillig verkeer &#x200B;](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) plaatsen en netwerken in te gaan door verkeer tegen een reeks veiligheidsregels te filtreren. Het verkeer dat om het even welke regels teweegbrengt wordt geblokkeerd alvorens het uw plaatsen of netwerk kan beschadigen.

Adobe Commerce cloud WAF biedt een WAF-beleid met een regel die is ontworpen om uw Adobe Commerce-webtoepassingen te beschermen tegen een groot aantal aanvallen.

WAF onderzoekt het web- en beheerverkeer om verdachte activiteiten te identificeren. Het evalueert GET en het verkeer POST (de vraag van HTTP API) en past de regel toe die wordt geplaatst om te bepalen welk verkeer aan blok. WAF kan een grote verscheidenheid van aanvallen, met inbegrip van SQL injectieaanvallen, dwars-plaats scripting aanvallen, de aanvallen van de gegevensexfiltratie, en de protocolschendingen van HTTP blokkeren.

Als cloudservice vereist de WAF geen hardware of software om te installeren of te onderhouden. Ten slotte, een bestaande technologiepartner, verstrekt de software en de deskundigheid. Hun krachtige, altijd-op WAF verblijft in elk geheim voorgeheugenknoop over het globale leveringsnetwerk van Fastly.

## Is de WAF beschikbaar voor alle cloudklanten?

Ja, de cloudservice van WAF is inbegrepen in uw Adobe Commerce op een abonnement voor cloudinfrastructuur voor zowel Adobe Commerce op de Starter-planarchitectuur van de cloudinfrastructuur als Adobe Commerce op de architectuurplannen van de cloud Infrastructure Pro zonder extra kosten. De WAF-service is beschikbaar in productie- en testomgevingen.

## Voldoet WAF aan de vereisten voor PCI DSS 6.6?

Ja.

## Als mijn Adobe Commerce on cloud Infrastructure-account sites beheert op meerdere domeinen, is het WAF-profiel dan afgestemd voor elk domein of voor alle domeinen samen?

De WAF wordt collectief afgestemd voor alle domeinen onder één cloud-account.

## Welke regels worden er voor de WAF gehanteerd?

De regel in het WAF-profiel dat op uw Adobe Commerce wordt toegepast voor de productieomgeving van de cloudinfrastructuur, is gebaseerd op de OWASP Top 10 Threat Protection-regel, die veelvoorkomende misbruiken voor webservices omvat. Het bevat ook Adobe Commerce-specifieke regels die door TrustWave SpiderLabs zijn ontwikkeld. Het team van het Onderzoek van de Veiligheid van Fastly heeft ook regels toegevoegd die uw plaats en netwerk tegen algemeen bekende aanvallen beschermen: slechte IP adressen, slechte gebruikersagenten, en bekende botnetbevel en controleknopen. We maken regels mogelijk op OWASP Paranoia Level 3 of minder, wat een hoge mate van beveiliging biedt.

## Hoe heb ik toegang tot logboeken?

Om de logboeken te hebben die naar uw registrerenhulpmiddel worden verzonden, te werken gelieve met uw Technische Manager van de Rekening (TAM) om een registrereneindpunt in Fastly toe te voegen.

## Hoe ziet een blokverzoek eruit?

Een geblokkeerde aanvraag retourneert een pagina van 403 met een aanvraag-id.

U kunt deze pagina aanpassen zolang de aanpassing de aanvraag-id bevat. Neem contact op met uw technische accountmanager voor meer informatie.

## Hoe kunnen we WAF-regelsets bijwerken? Hoe snel kan een WAF-regel in productie worden gewijzigd of bijgewerkt en wereldwijd worden toegepast?

Als onderdeel van de cloud WAF service beheert Fastly regelupdates van commerciële derden, Fastly research en open bronnen. Zij werken gepubliceerde regels zo nodig bij in een beleid of wanneer wijzigingen in de regels beschikbaar zijn uit hun respectieve bronnen. De nieuwe regels die de gepubliceerde klassen van regels aanpassen worden ook opgenomen in de instantie van WAF van om het even welke dienst zodra het wordt toegelaten. Dit helpt onmiddellijke dekking voor nieuwe of evoluerende explosies verzekeren. U kunt informatie [&#x200B; over regelupdates en onderhoud &#x200B;](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) op de Fastly documentatieplaats herzien.

## Hoe verschilt Adobe Commerce cloud WAF van de WAF-oplossing die snel aan haar directe klanten wordt aangeboden?

De WAF-oplossing die direct door Fastly wordt verkocht, is een betaalbaar aanbod dat bredere regelsets en extra functies zoals regelaanpassing en bescherming tegen malware omvat. De Adobe Commerce cloud WAF-oplossing bevat een aantal regels die zijn gericht op de Adobe Commerce-toepassing en bevat slechts één regel die is ingesteld voor de productieomgeving van elke klant.

## Welke soorten veiligheidsbedreigingen beschermt WAF tegen?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Threat</th>
<th style="width: 497.5px; text-align: left;">WAF-bescherming</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL-injectieaanvallen</td>
<td style="width: 497.5px;">Zowel bevatten de OWASP ModSecurity Core-regelset als de TrustWave-handelregel specifieke filters voor SQL-injectieaanvallen en de bijbehorende varianten.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injectie op andere plaatsen</p>
</td>
<td style="width: 497.5px;">De OWASP-regel beschermt tegen aanvallen van injectie naar andere plaatsen. Maakt snel gebruik van een scoremechanisme voor elke aanvraag die op zoek is naar locatieoverschrijdende injectie en andere bedreigingen voor de oorsprong. Wij scoren elk verzoek tegen de volledige vastgestelde kernregel en bevestigen dat de verzoekscore onder een configureerbare drempel is om het te kunnen overgaan.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Aanvallen op brute troepen</td>
<td style="width: 497.5px;">Wordt gedekt door de OWASP-regelset. Blokkeert snel ook brute krachtactiviteit door code te gebruiken VCL die specifieke bronnen, verzoeken, of pogingen erkent om geweld te beteugelen of veiligheidscontroles te overweldigen voorafgaand aan om het even welk verkeer die het oorspronkelijke datacenter bereiken.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Netwerkaanvallen</td>
<td style="width: 497.5px;">De aanvallen van het netwerk, of de aanvallen die netwerkinfrastructuur richten, worden automatisch geleid door Fastly. Snelheid geeft DNS niet door aan oorsprong en verkeer dat niet overeenkomt met een smal HTTP-, HTTPS- of DNS-profiel wordt aan de rand van het netwerk genegeerd. De aanvallen richten controleprotocollen worden verdedigd tegen door authentificatie van eindpunten door het netwerk. Bovendien, worden de netwerkprotocollen die binnen het Fastly netwerk worden gebruikt gehard om ervoor te zorgen dat zij niet als middel van versterking of bezinning kunnen worden leveraged. De klanten zijn verantwoordelijk voor het beschermen tegen aanvallen die het Fastly netwerk door de Fastly het adresruimte van het Geheime voorgeheugen IP van het Geheime voorgeheugen te bedienen, dat aan onze klanten als component van onze dienst CDN wordt gepubliceerd. Het is geadviseerd dat de oorsprongIP adresruimte niet in openbare DNS wordt gepubliceerd om bypassaanvallen te verzekeren kan deze adressen niet als doelstellingen gebruiken.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript injectie aanvallen</td>
<td style="width: 497.5px;">WAF-regels beschermen zich tegen het invoegen van kwaadaardige JavaScript-code in clientcommunicatie met webservices. Veelvoorkomende exploitatiepatronen of -scores worden door de WAF gefilterd om de integriteit van de oorspronkelijke service te waarborgen.</td>
</tr>
</tbody>
</table>

## Worden extra functies en functionaliteit aangeboden?

Het Adobe Commerce WAF-aanbod biedt bescherming tegen OWASP Top-10-bedreigingen als onderdeel van PCI-vereisten, 24x7 ondersteuning, inclusief triage voor valse positieven en versieupgrades. De volgende functies worden niet ondersteund in de standaardaanbieding:

* snelheidsbeperking
* regelaanpassingen
* botbeperking
* bescherming tegen malware

## Hoe worden de prestaties van mijn site beïnvloed door de WAF?

Er wordt naar schatting 1,5 milliseconden (ms) tot 20 ms latentie toegevoegd aan elk verzoek dat niet in de cache is opgeslagen.

## Kunnen de klanten IP zwarte lijsten tot stand brengen en wijzigen om verkeer te blokkeren?

Ja, klanten kunnen het blokkeren door land en toegangsbeheerlijst (ACL) van Adobe Commerce op Admin UI van de cloudinfrastructuur toelaten. Gebruik deze eigenschappen in gevallen waar u toegang voor bezoekers wilt blokkeren die uit specifieke landen of bepaalde IPs of IP waaiers komen. Als u wilt dat geblokkeerde bezoekers een aangepaste pagina zien in plaats van een foutcode, kunt u een aangepaste foutpagina maken door HTML te uploaden in het menu Snelconfiguratie. Zie [&#x200B; een douane fout/onderhoudspagina &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in onze ontwikkelaarsdocumentatie creëren.

## Waar kan ik de operationele status van mijn WAF-dienst controleren?

De algemene de dienstbeschikbaarheid van WAF wordt gemeld op de [&#x200B; Snelle pagina van de Status &#x200B;](https://status.fastly.com/). De beschikbaarheidsrapportage voor de WAF van individuele klanten wordt niet verstrekt.

## Biedt Adobe Commerce incidentbeheer voor de WAF-service?

Op dit moment wordt geen incidentbeheer aangeboden.

## Heeft Adobe Commerce een Security Operations Center?

Hoewel Adobe Commerce geen Centrum van de Verrichtingen van de Veiligheid heeft, hebben wij een proces van de veiligheidsverrichtingen dat ons toestaat om de juiste middelen in dienst te nemen om op veiligheidsincidenten in real time te antwoorden. We bieden ook 24-7-365 follow-up aan.

U kunt op Adobe Commerce betrekking hebbende veiligheidsnieuws en updates van het [&#x200B; Centrum van de Veiligheid &#x200B;](https://helpx.adobe.com/security.html) ook krijgen.

## Welke ondersteuning is beschikbaar?

De Steun van WAF biedt de volgende middelen aan om u bij het verlichten van de de dienstgevolgen van ongewenste of kwaadwillige verzoeken te helpen:

* Aan boord: inschakelen, initiële installatie en beperkte bewaking van de snelste service(s) die ondersteuning bieden voor de door Adobe Commerce beheerde cloud WAF
* Voortdurende fout-positieve tribune om gevallen aan te pakken waar de WAF legitiem verkeer blokkeert
* Configuratie van eventuele nieuwe standaardregels die zijn geïntroduceerd als onderdeel van WAF-upgrades

Zie de [&#x200B; termijnen van SLA van 0&rbrace; Cloud voor extra steuninformatie met inbegrip van strengheidsdefinities, reactietijden, kanalen, en beschikbaarheid.](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf)

## Als de WAF het legale verkeer blokkeert of andere problemen veroorzaakt, hoe kan ik dan hulp krijgen?

[&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) bij het [&#x200B; Centrum van de Hulp van Adobe Commerce &#x200B;](https://support.magento.com) voor. Gelieve te omvatten erop wijst dat het kaartje met de dienst van WAF verwant is en het geblokkeerde verzoekherkenningsteken (identiteitskaart) omvat.

Het Adobe Commerce-systeem voor kaartverkoop volgt de communicatie tussen onze supporttechnici en het personeel van een klant. Dit systeem verstrekt een tijd-gestempelde transcriptie van mededelingen, en verzendt e-mail naar klant en het personeel van Adobe Commerce aangezien de kaartjes worden bijgewerkt.

Voor alle incidenten die online zijn verzonden, wordt het bewijs van een incident bevestigd via het kaartsysteem van het Adobe Commerce Customer Help Center. Na ontvangst van een naar behoren ingediend incident wordt prioriteit gegeven aan de ondersteuningsdiensten overeenkomstig de hierboven vermelde prioriteitsniveaus.

De volgende tabel geeft een overzicht van de ondersteuningskanalen en de beschikbaarheid voor WAF Support:

<table class="table-basic">
<tbody>
<tr>
<th>Ondersteuningsaanbod</th>
<th>Details</th>
</tr>
<tr>
<td>Online zelfbedieningshulp</td>
<td>Onbeperkte toegang</td>
</tr>
<tr>
<td>Beschikbaarheid voor incidentrapporten</td>
<td>07-24</td>
</tr>
<tr>
<td>Webportal</td>
<td>Beschikbaar via Zendesk</td>
</tr>
<tr>
<td>Noodescalatie*</td>
<td>Verwijs naar <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html"> P1 van Adobe Commerce bericht hotline </a> artikel voor de aantallen van de V.S. en van de internationale.</td>
</tr>
</tbody>
</table>

*\* De telefoonlijn van de Steun van de gratis Adobe Commerce is gereserveerd voor Prioriteit 1 Incidenten slechts. Niet-Prioriteit 1 vraag zal algemene reactie op kwesties vertragen*

## Hoe worden valse positieven getild?

We hebben een fout-positief triageproces (24x7 beschikbaar) om instanties snel te behandelen en op te lossen waar legitieme verzoeken een WAF-regel hebben geactiveerd. Onjuiste positieve gebeurtenissen worden behandeld als prioriteitsproblemen 1. Als standaardactie, kan ons ondersteuningsteam het beleid van WAF onmiddellijk bijwerken om de regel onbruikbaar te maken die de blokkerende gebeurtenis teweegbracht en het wettige verzoek toe te staan om door WAF over te gaan.

## Wat gebeurt er als het verkeer naar de beheersectie van Adobe Commerce op de website van de cloudinfrastructuur WAF-regels activeert? Zal de Steun van Adobe Commerce kwesties met geblokkeerd adminverkeer oplossen?

Ja, geblokkeerd beheerverkeer wordt behandeld als een Prioriteit 1 kwestie.
