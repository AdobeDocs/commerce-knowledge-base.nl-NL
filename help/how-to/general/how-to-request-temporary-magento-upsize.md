---
title: Tijdelijke Adobe Commerce aanvragen voor uitgebreide cloudinfrastructuur
description: Als uw organisatie een online gebeurtenis plant waarin u veel verkeer verwacht, of u plotseling vindt dat uw site een gebeurtenis met veel verkeer ondergaat, kunt u een [Support Ticket] (/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) indienen om tijdelijke extra cloudcapaciteit voor uw Adobe Commerce in de cloudinfrastructuur aan te vragen.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Tijdelijke Adobe Commerce aanvragen voor uitgebreide cloudinfrastructuur

Als uw organisatie een online gebeurtenis plant waarin u hoog verkeer verwacht, of u plotseling uw plaats vindt om een hoge verkeersgebeurtenis te ondergaan, kunt u file [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) om tijdelijke extra wolkencapaciteit voor uw Adobe Commerce op de opslag van de wolkeninfrastructuur aan te vragen.

>[!NOTE]
>
>48 kantooruren zijn vereist voor verzoeken om een upgrade in andere gevallen dan noodgevallen. Upgrades voor promotiecampagnes worden niet als noodsituaties beschouwd, tenzij de site volledig niet functioneel is of veel meer verkeer krijgt dan verwacht en de prestaties ernstig zijn verslechterd.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Hoe te om hoge verkeersgebeurtenissen te identificeren

In New Relic Alerts, kunt u de voorwaarden van de basislijnalarm gebruiken om drempels te bepalen die zich aan het gedrag van uw gegevens aanpassen.

Waarschuwing bij basislijn is handig voor het maken van waarschuwingsvoorwaarden die:

* U wordt alleen op de hoogte gesteld wanneer gegevens zich abnormaal gedragen.
* Pas dynamisch aan veranderende gegevens en tendensen, met inbegrip van dagelijkse of wekelijkse tendensen aan.

Bovendien werkt basislijnwaarschuwingen goed met nieuwe toepassingen wanneer u nog geen bekend gedrag hebt.

Volg deze koppeling voor meer informatie over New Relic [Anomalische detectie met toegepaste intelligentie](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Als u een waakzaam bericht ontvangt dat een hoge verkeersgebeurtenis voorstelt kunt u moeten overwegen [het voorleggen van een Ticket van de Steun](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) aanvullende capaciteit aanvragen. Voer de onderstaande stappen uit.

## De prestaties van uw site controleren

Adobe biedt een reeks New Relic-waarschuwingsbeleid voor Adobe Commerce op het gebied van cloudinfrastructuur Pro-planningsarchitectuur en Adobe Commerce op het gebied van de Starter-planningsarchitectuur van de cloud om de volgende prestatiekernwaarden bij te houden:

* [Apdex score](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Foutfrequentie
* Schijfruimte (alleen beschikbaar in productieomgevingen van Pro-architectuur)

Op basis van best practices uit de branche worden in dit beleid drempelwaarden voor waarschuwingen en kritieke omstandigheden vastgesteld die van invloed zijn op de prestaties. Als er op uw site een infrastructuur- of toepassingsprobleem optreedt dat een waarschuwingsdrempel activeert, stuurt New Relic waarschuwingsberichten zodat u het probleem proactief kunt verhelpen. Om dit beleid te gebruiken, moet u berichtkanalen vormen om de waakzame berichten te ontvangen.

Volg deze koppeling voor meer informatie [op prestaties gebaseerde waarschuwingen configureren](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Stappen om tijdelijke upgrade aan te vragen

Voer de onderstaande stappen uit om een [Support-ticket](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) om tijdelijke extra wolkencapaciteit aan te vragen:

Een [Support-ticket in het Adobe Commerce Support Center](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), na het invoeren van de volgende informatie:

>[!NOTE]
>
>De *Vakantiepopieverzoek* De keuze is slechts een optie tussen de maanden oktober en december.

1. Selecteer het Adobe Commerce-product waarvoor u ondersteuning zoekt.
1. Vul de eerste vier velden (Product, Organisatie, Type implementatie, Onderwerp) in.
1. Selecteren *Adobe Commerce cloud-infrastructuur* in de **Reden contactpersoon** vervolgkeuzelijst.
1. Selecteren *Aanvraag voor piekcapaciteit vakantie* in de **Reden voor contact met Adobe Commerce-infrastructuur** vervolgkeuzemogelijkheden. Klikken **OK** in het pop-upbericht waarin wordt verzocht om een opzegtermijn van 48 kantooruren voor tijdelijke extra verzoeken om cloudcapaciteit.
1. Datums selecteren voor de verplichte velden **Begindatum wijzigen** en **Einddatum wijzigen**. De voorkeur **Begintijd wijzigen** is ook een verplicht veld.
1. Vul de volgende vier velden in.
1. In de **Beschrijving** als u aanvullende informatie over de grootte hebt, geeft u deze hier op. Als er geen specifieke grotere capaciteit wordt gevraagd, wordt u verhoogd tot de volgende grotere capaciteit van de omgeving. De verzoeken van de vloedgolf zullen aan de volgende grotere grootte van uw huidige grootte in gebreke blijven. Indien u aanvullende capaciteit nodig hebt, vermeld dan dat in de **Beschrijving** veld. Verhoogde capaciteit wordt afgetrokken van uw contractueel vastgelegde piekdagen of vCPU-dagen. Het venster voor capaciteitsuitbreiding is standaard vijf dagen, maar als u meer of minder dagen nodig hebt, kunt u dit in uw [Support-ticket](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Wanneer de upgrade is gepland, past een geautomatiseerd systeem de grootte van uw cloudinstantie aan. U kunt geen kaartmelding ontvangen wanneer de procedure is voltooid. Met het gereedschap Waarneming voor Adobe Commerce kunt u uw AWS- of Azure-instantietypen weergeven op [de wijziging controleren](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## De geschiedenis van uw upformaten weergeven

U kunt de historie van de aangevraagde formaatwijzigingen bekijken door de gegevens bij uw te vragen **CSM (Customer Success Manager)**.
De volgende informatie is beschikbaar voor elk resize verzoek:

* **Begindatum van grootte**: datum van verzoek voor bijwerken.
* **Einddatum van grootte**: datum waarop de cluster naar de vorige grootte is geretourneerd.
* **vCPU-grootte**: de grootte van de cluster na de vergroting.
* **Daggebruik**: gedurende hoeveel dagen is de cluster opgewaardeerd gebleven.
* **Period vCPU**: vCPU grootte is gewijzigd met het aantal dagen dat is gebruikt. (vCPU grootte 192 x 25 dagen is bijvoorbeeld 4.800).


## Gerelateerde lezing

* Voor inzichten, methodes, en voorbeelden van om plaatsprestaties te meten en te verbeteren, verwijs naar de volgende diepgaande artikelen in onze steun kennisbasis:
   * [Berekening van CPU-toewijzing voor Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Controleren of de host moet worden bijgewerkt voor Adobe Commerce in de cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [CPU-configuratie van host controleren op Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Voor informatie over hoe te om stroomonderbrekingen te identificeren, verwijs naar [Onderkennen en meten van uitvallen voor Adobe Commerce in de cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in onze kennisbasis voor ondersteuning.
* Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor informatie over het verbeteren van de prestaties van de site om te voorkomen dat u een capaciteitsuitbreiding moet gebruiken:
   * [Afbeeldingsgrootte](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [In cache plaatsen van volledige pagina](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-gereedschappen](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
