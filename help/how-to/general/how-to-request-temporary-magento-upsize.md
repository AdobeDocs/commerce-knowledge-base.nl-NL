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

Als uw organisatie een online gebeurtenis plant waarin u hoog verkeer verwacht, of u plotseling uw plaats vindt om een hoge verkeersgebeurtenis te ondergaan, kunt u a [ Ticket van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) indienen om tijdelijke extra wolkencapaciteit voor uw Adobe Commerce op de opslag van de wolkeninfrastructuur te verzoeken.

>[!NOTE]
>
>48 kantooruren zijn vereist voor verzoeken om een upgrade in andere gevallen dan noodgevallen. Upgrades voor promotiecampagnes worden niet als noodsituaties beschouwd, tenzij de site volledig niet functioneel is of veel meer verkeer krijgt dan verwacht en de prestaties ernstig zijn verslechterd.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Hoe te om hoge verkeersgebeurtenissen te identificeren

In New Relic Alerts, kunt u de voorwaarden van de basislijnalarm gebruiken om drempels te bepalen die zich aan het gedrag van uw gegevens aanpassen.

Waarschuwing bij basislijn is handig voor het maken van waarschuwingsvoorwaarden die:

* U wordt alleen op de hoogte gesteld wanneer gegevens zich abnormaal gedragen.
* Pas dynamisch aan veranderende gegevens en tendensen, met inbegrip van dagelijkse of wekelijkse tendensen aan.

Bovendien werkt basislijnwaarschuwingen goed met nieuwe toepassingen wanneer u nog geen bekend gedrag hebt.

Volg deze verbinding om meer over New Relic [ Anomaly opsporing met toegepaste Intelligentie ](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/) te leren.

Als u een waakzaam bericht ontvangt dat een hoge verkeersgebeurtenis voorstelt kunt u [ overwegen die een Bestelwagen van de Steun ](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) voorleggen om extra capaciteit te vragen. Voer de onderstaande stappen uit.

## De prestaties van uw site controleren

Adobe biedt een reeks New Relic-waarschuwingsbeleid voor Adobe Commerce op het gebied van cloudinfrastructuur Pro-planningsarchitectuur en Adobe Commerce op het gebied van de Starter-planningsarchitectuur van de cloud om de volgende prestatiekernwaarden bij te houden:

* [ score van de Index ](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Foutfrequentie
* Schijfruimte (alleen beschikbaar in productieomgevingen van Pro-architectuur)

Op basis van best practices uit de branche worden in dit beleid drempelwaarden voor waarschuwingen en kritieke omstandigheden vastgesteld die van invloed zijn op de prestaties. Als er op uw site een infrastructuur- of toepassingsprobleem optreedt dat een waarschuwingsdrempel activeert, stuurt New Relic waarschuwingsberichten zodat u het probleem proactief kunt verhelpen. Om dit beleid te gebruiken, moet u berichtkanalen vormen om de waakzame berichten te ontvangen.

Volg deze verbinding om te leren hoe te [ op prestaties-gebaseerde alarm ](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts) vormen.

## Stappen om tijdelijke upgrade aan te vragen

Volg de stappen hieronder om a [ Ticket van de Steun ](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) voor te leggen om tijdelijke extra wolkencapaciteit te verzoeken:

Verzend a [ Ticket van de Steun bij het Centrum van de Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), na het invoeren van de volgende informatie:

>[!NOTE]
>
>De *keus van het Verzoek van de Vakantiedruk 0&rbrace; is slechts een optie tussen de maanden van Oktober en van December.*

1. Selecteer het Adobe Commerce-product waarvoor u ondersteuning zoekt.
1. Vul de eerste vier velden (Product, Organisatie, Type implementatie, Onderwerp) in.
1. Selecteer *de wolkeninfrastructuur van Adobe Commerce* in de **drop-down Reden van het Contact**.
1. Selecteer *Verzoek van de Capaciteit van de Vakantieduur van 0&rbrace; {in de **3} drop-down opties van de Reden van het Contact van de Infrastructuur van Adobe Commerce.*** Klik **O.K.** op het pop-up bericht vragend 48 bedrijfsuren&#39; bericht voor tijdelijke extra verzoeken van de wolkencapaciteit.
1. Selecteer data voor de verplichte gebieden **Resize Datum van het Begin** en **Resize Datum van het Eind**. De aangewezen **Resize Tijd van het Begin** is ook een verplicht gebied.
1. Vul de volgende vier velden in.
1. Op het **gebied van de Beschrijving**, als u extra informatie over grootte hebt, verstrek het hier. Als er geen specifieke grotere capaciteit wordt gevraagd, wordt u verhoogd tot de volgende grotere capaciteit van de omgeving. De verzoeken van de vloedgolf zullen aan de volgende grotere grootte van uw huidige grootte in gebreke blijven. Als u extra capaciteit vereist, gelieve erop te wijzen dat op het **gebied van de Beschrijving**. Verhoogde capaciteit wordt afgetrokken van uw contractueel vastgelegde piekdagen of vCPU-dagen. Het typische venster van de capaciteitsverhoging is vijf dagen, maar als u meer of minder dagen nodig hebt, gelieve dit in uw [ Ticket van de Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) te wijzen.

>[!NOTE]
>
>Wanneer de upgrade is gepland, past een geautomatiseerd systeem de grootte van uw cloudinstantie aan. U kunt geen kaartmelding ontvangen wanneer de procedure is voltooid. U kunt de Waarneming voor het hulpmiddel van Adobe Commerce gebruiken om uw AWS of Azure instantietypes te bekijken om [ de verandering ](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md) te verifiëren.

## De geschiedenis van uw upformaten weergeven

U kunt de geschiedenis van gevraagde resizes bekijken door de informatie van uw **CSM (de Manager van het Succes van de Klant) te verzoeken**.
De volgende informatie is beschikbaar voor elk resize verzoek:

* **Datum van het Begin van de Grootte**: datum van upsize verzoek.
* **Einddatum van de Grootte**: datum toen de cluster aan de vorige grootte werd teruggekeerd.
* **grootte vCPU**: de grootte van de cluster na upsize.
* **het Gebruik van Dagen**: voor hoeveel dagen bleef de cluster omhoog.
* **Periode vCPU**: veranderde vCPU grootte door het aantal dagen het werd gebruikt. (vCPU grootte 192 x 25 dagen is bijvoorbeeld 4.800).


## Gerelateerde lezing

* Voor inzichten, methodes, en voorbeelden van om plaatsprestaties te meten en te verbeteren, verwijs naar de volgende diepgaande artikelen in onze steun kennisbasis:
   * [Berekening van CPU-toewijzing voor Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Controleren of de host moet worden bijgewerkt voor Adobe Commerce in de cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [CPU-configuratie van host controleren op Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Voor informatie over hoe te om stroomonderbrekingen te identificeren, verwijs naar [ uitvallen voor Adobe Commerce op wolk ](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in onze basis van de steunkennis identificeren en meten.
* Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor informatie over het verbeteren van de prestaties van de site om te voorkomen dat u een capaciteitsuitbreiding moet gebruiken:
   * [Afbeeldingsgrootte](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [In cache plaatsen van volledige pagina](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-gereedschappen](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
