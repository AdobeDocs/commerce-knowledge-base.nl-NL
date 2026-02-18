---
title: SSL-certificaten (TLS) voor Adobe Commerce op cloudinfrastructuur
description: Dit artikel biedt snelle antwoorden op vragen over het verkrijgen van SSL (TLS)-certificaten voor uw Adobe Commerce-site in onze cloudinfrastructuur.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# SSL-certificaten (TLS) voor Adobe Commerce op cloudinfrastructuur

Dit artikel biedt snelle antwoorden op vragen over het verkrijgen van SSL (TLS)-certificaten voor uw Adobe Commerce-site in onze cloudinfrastructuur.

## Welk SSL/TLS-certificaat verschaft Adobe?

Adobe verstrekt een domein-Gevalideerd [&#x200B; laat SSL/TLS certificaat &#x200B;](https://letsencrypt.org/) coderen om veilig verkeer HTTPS van [!DNL Fastly] te dienen. Adobe biedt één certificaat voor elke Adobe Commerce op het gebied van de architectuur van de cloudinfrastructuur Pro, Staging en Adobe Commerce op de Starter-planarchitectuuromgeving van de cloud-infrastructuur om alle domeinen in die omgeving te beveiligen.

## Wat dekt een certificaat?

Voor de Pro-planarchitectuur, zowel zullen de Staging als van de Productie specifieke milieu&#39;s een SSL certificaat hebben gecreeerd. Elke specifieke omgeving buiten de Platform-as-a-Service (PaaS) Integratieomgevingen zal dit certificaat hebben voor de URL&#39;s die aan die omgeving zijn toegewezen.

Voor de het planarchitectuur van de Starter en milieu&#39;s van de Integratie van PaaS, zal er een standaard technisch domein zijn dat van het milieu wordt voorzien en door een afzonderlijk certificaat wordt beveiligd.

## Hoe te om een nieuw domein voor het bestaande certificaat toe te voegen?

Het domein toevoegen aan de service in [!DNL Fastly] :

1. Wijs uw domein in DNS aan prod.magentocloud.map.fastly.net en wacht tot 6 uren.
1. [&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) verzoekend om dit domein in de configuratie van Nginx toe te voegen (als u het niet vroeger hebt gedaan).

## Hoe kan ik een certificaat aanvragen?

Geval 1

Als u nog geen website hebt gestart, hebt u wellicht ACME Challenge CNAME van uw Customer Technical Advisor (CTA) ontvangen. U hebt alleen een ACME-uitdaging nodig als u niet direct uw DNS naar de productie-URL kunt richten en de SSL-certificaten die vooraf zijn gemaakt, moet ophalen.

Zaak 2

Als uw site al live is en/of u kunt verwijzen naar de URL&#39;s die meteen voor uw livesite worden gebruikt, hoeft u geen ACME-NAAM aan te vragen. Zodra u de URL&#39;s naar wens toevoegt aan uw Adobe Commerce op de cloudinframesite en uw DNS op [!DNL Fastly] plaatst, werkt de HTTP-validatie en wordt het SSL-certificaat voor het eerst gemaakt of wordt het certificaat bijgewerkt met extra URL&#39;s.

## Kan ik mijn eigen SSL/TLS-certificaat gebruiken?

U kunt uw eigen SSL/TLS- certificaat in plaats van het gebruiken van [&#x200B; verstrekken van de Versleuteling van certificaat &#x200B;](https://letsencrypt.org/) door Adobe.

Dit proces vereist echter extra werk om op te zetten en te onderhouden. U moet eerst een CSR (Certificate Signing Request) voor de domeinnaam van de website (of algemene naam) genereren en deze aan uw SSL-leverancier doorgeven om een SSL-certificaat op te geven.

Zodra u het SSL certificaat hebt, leg een [&#x200B; kaartje van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) voor of werk met uw CTA om douane-ontvangen certificaten aan uw wolkenmilieu&#39;s toe te voegen.

* Als de domeinen niet meer in gebruik zijn, zullen zij automatisch van ons systeem worden leeggemaakt, en geen verdere actie wordt vereist.
* Als u reeds een certificaat bezit, upload het gebruikend een cliënt SFTP (het Protocol van de Overdracht van het Dossier van SSH) aan een web-ontoegankelijke dossierplaats op uw server en [&#x200B; voorlegt een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) latend hen het dossierweg kennen.

>[!WARNING]
>
>Het is belangrijk dat u de certificaatbestanden niet rechtstreeks uploadt naar het ticket. Anders worden de certificaten als gecompromitteerd beschouwd en moet Adobe een nieuw certificaat aanvragen.
>De bestanden moeten via SFTP naar de server worden geüpload naar een map van uw keuze, bijvoorbeeld `var/ssl` , `/tmp/ssl` , enz. - gebruik geen andere methoden zoals het toewijzen van bestanden aan uw opslagplaats (die alleen moeten worden uitgevoerd voor onveranderlijke bestanden die geen gevoelige gegevens bevatten).

## De naam van uw certificaat

De naam van het SSL-certificaat is alleen van belang voor de primaire URL en het is de primaire hostnaam die door de eerste URL wordt genoemd en moet overeenkomen om te worden gevalideerd en gemaakt. Als u een paar URL&#39;s hebt, worden deze als alternatieve naamitems voor het onderwerp aan het certificaat toegevoegd. Als meerdere URL&#39;s verwijzen naar één Adobe Commerce op de cloudinframesite, hebt u slechts één algemene naam-URL-certificering die alternatieve onderwerpnamen heeft toegevoegd om uw site te beveiligen met SSL.

## Welk domein zal op het Gemeenschappelijke gebied van de Naam van het certificaat worden getoond?

Het domein dat op het certificaat wordt getoond is enkel het eerste domein dat aan het certificaat TLS wordt toegevoegd, bevolkt het **Gemeenschappelijke Naam** (**CN**) gebied, en browsers tonen eerst deze naam. Het **Onderwerp Alternatieve Naam** (**San**) gebied bevat alle DNS namen voor het certificaat TLS. Er is geen manier om de getoonde Gemeenschappelijke Naam te veranderen of te verzoeken.

## Kan ik wildcard-TLS-certificaten gebruiken?

Jokerteken-TLS-certificaten kunnen alleen worden gebruikt met uw aangepaste certificaat en niet met Adobe Commerce Let&#39;s Encrypt-certificaten. Als onderdeel van onze TLS-optimalisatie beëindigt Adobe de ondersteuning voor TLS-certificaten met jokertekens. We identificeren en nemen contact op met handelaren die een jokertekencertificaat gebruiken met de certificaten van Adobe Let&#39;s Encrypt en die zijn geconfigureerd in de [!DNL Fastly] -console voor Adobe Commerce. Wij vragen dat deze vervangingscertificaten met nauwkeurige domeinen worden vervangen om TLS dekking te verzekeren. Om een vervangingscertificaat te vervangen TLS, gelieve de [&#x200B; domeinsectie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) van de [!DNL Fastly] stop te bezoeken. Van hieruit kunnen exacte domeinen worden toegevoegd en kan het jokerteken worden verwijderd. DNS moet naar [!DNL Fastly] verwijzen voor deze nieuwe domeinen om door de CDN te leiden. Zodra de domeinen worden toegevoegd en DNS wordt bijgewerkt, zal een passend [&#x200B; 1&rbrace; certificaat van de Encrypt van A.S. &lbrace;worden voorzien. &#x200B;](https://letsencrypt.org/) Als u geen domein verwijdert waarnaar [!DNL Fastly] verwijst met een jokerteken, verwijdert Adobe het gedeelde certificaat. Dit kan in een plaatsafval resulteren als u niet de gevormde URL FQDN en zelfde URL FQDN opstelling in uw DNS hebt. Daarom moet u bevestigen dat de geconfigureerde URL&#39;s ook een-op-een overeenkomst hebben in hun DNS-code die verwijst naar [!DNL Fastly] .

## Wat moet ik doen als mijn domein niet meer naar Adobe Commerce wijst?

Als uw domein niet meer naar Adobe Commerce verwijst, verwijdert u het van het systeem [!DNL Fastly] / Adobe Commerce. Zie [!DNL Fastly] [&#x200B; Deleting a domain &#x200B;](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) om meer te leren. Hoewel u uw domein niet naar Adobe Commerce hoeft te verwijzen, controleert u of een TLS-certificaat van het hoogste niveau is vereist. Als een top-level domein wordt vereist, gelieve uw DNS bij te werken om aan Adobe Commerce te richten. Als het reeds aan Adobe Commerce richt, werk uw verslag van CAA bij om [&#x200B; te omvatten laat-encrypt &#x200B;](https://letsencrypt.org/). Als u deze stappen uitvoert, zult u LE Cert bijgewerkt zien met de noodzakelijke secundaire URL&#39;s die de cert behandelt. &#x200B;

## Gerelateerde lezing

[&#x200B; Levering SSL/TLS certificaten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) in onze ontwikkelaarsdocumentatie
