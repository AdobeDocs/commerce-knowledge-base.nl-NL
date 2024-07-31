---
title: Adobe Commerce Support Knowledge Base
description: Alles wat u moet weten om problemen op te lossen en uw Commerce-winkel te onderhouden.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 738a5455267647d294d222d5bb6149254dcb93dd
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Adobe Commerce Support Knowledge Base

![ homepage van de Kennisbank ](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

De informatie in deze Kennisbank wordt ontworpen als aanvulling op [ de Documentatie van de Ontwikkelaar van Adobe Commerce ](https://developer.adobe.com/commerce/docs), en [ Handleiding van de Merchant van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html), en andere publicaties van Adobe Commerce. Het behandelt het oplossen van problemen en beste praktijken, gastheeraankondigingen, antwoorden FAQs, en benadrukt specifieke scenario&#39;s die (om het even welke reden) niet vermeld in de officiële documentatie zijn.

## Wat zit er in de Knowledge Base?

| CATEGORIE | BESCHRIJVING |
| --- | --- |
| [ Hulpmiddelen van de Steun ](/help/support-tools/overview.md) | Verbeter uw e-commercewinkelervaring met de verschillende ondersteuningsinstrumenten die Adobe Commerce biedt. Wij bieden gepersonaliseerde beste praktijken, diagnose en controlehulpmiddelen, en de meest relevante informatie over uw plaats. |
| [ Mededelingen ](/help/announcements/overview.md) | Ontvang belangrijke updates van de Adobe Commerce-teams. |
| [ het Oplossen van problemen ](/help/troubleshooting/overview.md) | Haal oplossingen en patches voor zelfbediening van het Adobe Commerce Support-team. |
| [ Gids van de Gebruiker van het Centrum van de Hulp ](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Leer hoe u uw ondersteuningstickets beheert, gedeelde toegang verleent en de Knowledge Base op effectieve wijze doorbladert. |
| [ hoe te ](/help/how-to/overview.md) | Kies voor duidelijke stapsgewijze instructies van het Adobe Commerce Support-team. |
| [ Veelgestelde vragen ](/help/faq/overview.md) | Veelgestelde vragen over het beleid, de strategieën en de specifieke eigenschappen van Adobe Commerce zijn te vinden. |

>[!NOTE]
>
>Om een nieuw kaartje te dossier, teken binnen aan [ het Centrum van de Hulp van Adobe Commerce ](https://support.magento.com/) en volg de stappen die onder [ worden gedetailleerd een Ticket van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) voorleggen.
>
>Als u niet de optie ziet om een kaartje voor te leggen, verwijs naar *[voorlegt een kaarthink niet getoond ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* sectie in onze [ Gids van de Gebruiker van het Centrum van de Hulp ](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Nieuwe functies

<table style="width:100%">
  <tr>
    <th style="width:70%">Beschrijving</th>
    <th style="width:15%">Type</th>
    <th style="width:15%">Datum</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment"> CLI <code>Magento-cloud</code> toont geen actief milieu:</a> er zijn verscheidene actieve milieu's, en u probeert om met een milieu in wisselwerking te staan door een Magento-wolk CLI (bevel-lijn hulpmiddel) bevel in werking te stellen. Nochtans, maakt de herinnering om het gewenste milieu te kiezen geen lijst van deze milieu.
    </td>
    <td>Nieuw artikel</td>
    <td>30 juli 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches"> hoe te om een veiligheidspatch te verkrijgen en toe te passen:</a> Dit artikel verstrekt instructies op hoe te om een veiligheidspatch te verkrijgen en toe te passen dat is vrijgegeven, maar de instructies zijn niet beschikbaar.  
    </td>
    <td>Nieuw artikel</td>
    <td>30 juli 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch"> die terug terugvallen aan Elasticsearch7 wanneer de onderzoeksmotor aan Openssearch wordt geplaatst:</a> Dit artikel verstrekt een oplossing voor de kwestie wanneer het Terugvallen naar fout Elasticsearch7 voorkomt wanneer de onderzoeksmotor aan OpenSearch in Adobe Commerce wordt geplaatst. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error"> Ontbroken Plaatsing: Er zijn geen bevelen die in de "geheime voorgeheugen"namespace fout worden bepaald:</a> Dit artikel verstrekt een oplossing voor de kwestie wanneer uw plaatsing ontbreekt en één van de fouten die in het logboek wordt getoond is <em> Er zijn geen bevelen die in "geheim voorgeheugen"namespace </em> worden bepaald. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response"> ACSD-55566: <code>mergeCart</code> de mutatie ontbreekt met interne serverfout in de reactie van GraphQL:</a> ACSD-55566 herstelt de kwestie waar de <code>mergeCart</code> mutatie met een interne serverfout in de reactie van GraphQL ontbreekt. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd.  
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront"> ACSD-56546: De configureerbare en bundelproducten tonen als uit voorraad op de opslagplaats:</a> ACSD-56546 flardmoeilijke moeilijke situatie waar de configureerbare en bundelproducten als uit voorraad op de opslagplaats tonen. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd.  
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information"> ACSD-57565: Het orde dashboard toont onjuiste ordeinformatie:</a> ACSD-57565 flardfixes de kwestie waar het ordedashboard onjuiste ordeinformatie toont tot de tijdspanne wordt bijgewerkt. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql"> ACSD-57394: Onjuiste productsortering door veelvoudige soortattributen in GraphQL:</a> ACSD-57394 herstelt de flard de kwestie waar de producten verkeerd gesorteerd zijn wanneer het gebruiken van veelvoudige soortattributen in GraphQL. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations"> ACSD-57854: De reactie van GraphQL bevat gehandicapte categorieën die niet in de categoriesamenvoegingen zouden moeten worden vermeld:</a> ACSD-57854 herstelt de kwestie waar de reactie van GraphQL gehandicapte categorieën bevat die niet in de categoriesamenvoegingen zouden moeten worden vermeld. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing"> ACSD-57074: Ja/Geen douaneattribuut met <code>price_*</code> prefix in <code>attribute_code</code> attribuut werkt niet met het indexeren:</a> het markering ACSD-57074 bevestigt de kwestie waar <em> ja/Nr </em> douaneattribuut met <code>price_*</code> prefix in het <code>attribute_code</code> attribuut niet met het indexeren werkt. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 is geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons"> ACSD-55241: Gebruikte en Tijden Gebruikte attributen tonen onjuiste waarden voor geproduceerde coupons:</a> ACSD-55241 herstelt de kwestie waar de Gebruikte en Tijden Gebruikte attributen onjuiste waarden voor geproduceerde coupons tonen. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 is geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products"> ACSD-56760: Admin gebruiker is beperkt tot een specifieke website en kan geen nieuwe producten sorteren of toevoegen:</a> ACSD-56760 flardmoeilijke situatie waar de gebruiker Admin die tot een specifieke website wordt beperkt en nieuwe producten binnen een categorie niet kan sorteren of toevoegen voor het geval dat de Webopslag het eigen wortelcategorie heeft. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 is geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address"> ACSD-56635: De ingevoerde klanten worden gedupliceerd met het zelfde e-mailadres wanneer rekening het delen aan Globaal wordt geplaatst:</a> ACSD-56635 flardmoeilijke situatie waar de ingevoerde klant met het zelfde e-mailadres wordt gedupliceerd wanneer de invoer met rekening het delen wordt gebruikt die aan Globaal wordt geplaatst. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked"> ACSD-57315: De nieuwe transactie wordt gecreeerd in PayPal Payflow Pro telkens als de ophaalknoop wordt geklikt:</a> ACSD-57315 flardmoeilijke situatie de kwestie waar een nieuwe transactie in PayPal Payflow Pro wordt gecreeerd telkens als de ophaalknoop op het scherm van de meningstransactie in Admin wordt geklikt. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger"> ACSD-56741: De fouten van de het gegevensbestandopstelling van het oplossen van problemen met de trekkers van douane MySQL:</a> ACSD-56741 herstelt de flard waar een foutenmelding <em> probeert om tot seriecompensatie op waarde ongeldig type toegang te hebben </em> verschijnt tijdens <code>setup:upgrade</code> toe te schrijven aan een douane MySQL trekker in het gegevensbestand niet verwant aan indexatie en MView. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear"> ACSD-58008: Het uitgeven van de einddatum als leeg veroorzaakt de programmaupdate om te verdwijnen:</a> ACSD-58008 herstelt de flard waar het uitgeven van de einddatum als lege oorzaken de planningupdate om te verdwijnen. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies"> ACSD-57337: De gebruiker van Admin met toegangsbeperkingen kon alle bedrijven in het net van Bedrijven bekijken:</a> ACSD-57337 het flard verhelpt de kwestie waar een admin gebruiker met toegangsbeperkingen aan specifieke websites bedrijven van alle websites in het net van Bedrijven kon bekijken. Deze patch is beschikbaar wanneer <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 wordt geïnstalleerd. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth"> de Plaatsing ontbreekt met correcte toegangssleutels in <code>env:COMPOSER_AUTH</code> of <code>auth.json</code>:</a> Dit artikel verstrekt een oplossing voor de kwestie wanneer uw plaatsing met een fout zoals in het plaatsingslogboek ontbreekt. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests"> hoe te om WAF voor GraphQL- verzoeken over te slaan:</a> Dit artikel verklaart hoe te om WAF voor GraphQL- verzoeken te mijden wanneer Fastly WAF uw verzoeken van GraphQL blokkeert. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full"> E-mail die dat de uitvoeropslag verklaart bijna volledig is:</a> Dit artikel verstrekt een oplossing voor de kwestie waar u een e-mail die ontvangt dat de uitvoeropslag bijna volledig is. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud"> Verbetering MariaDB 10.4 aan 10.5 voor Adobe Commerce op wolk:</a> Dit artikel verklaart hoe te van MariaDB 10.4 aan 10.5 te bevorderen om Adobe Commerce op wolkeninfrastructuur te blijven gebruiken. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions"> Herziene flarden voor de toegangsverlies van Kaarten van Google op alle versies van Adobe Commerce:</a> Dit artikel verstrekt een moeilijke situatie voor de handelaren van Adobe Commerce die niet compatibel met om het even welke recente versies van Google Kaarten van 3.54+ zijn. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102"> update van de Veiligheid beschikbaar voor Adobe Commerce - APSB24-40:</a> Dit artikel deelt een update met betrekking tot CVE-2024-34102. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments"> slechte prestaties in integratiemilieu's:</a> Dit artikel verstrekt een oplossing voor de kwestie waar de Pro integratiemilieu's en de het opvoeren van de Starter milieu's slecht presteren. 
    </td>
    <td>Nieuw artikel </td>
    <td>30 juli 2024</td>
 </tr>
</table>

## Populaire artikelen

* [Overschakelen naar OpenSearch for Adobe Commerce op Cloud 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Apache log4j2 kwetsbaarheid in Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Beveiligingsupdates beschikbaar voor Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Onderkennen en meten van uitvallen voor Adobe Commerce op cloudinfrastructuur](/help/how-to/general/how-to-identify-outages.md)
* [OmgevingsvCPU-laag in uw cluster weergeven op Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce op cloud-infrastructuur: berekening van CPU-toewijzing](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce on cloud-infrastructuur: CPU-configuratie van host controleren](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
