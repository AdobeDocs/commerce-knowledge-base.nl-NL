---
title: Tijdelijke Adobe Commerce aanvragen voor uitgebreide cloudinfrastructuur
description: Als uw organisatie een online gebeurtenis plant waarin u veel verkeer verwacht, of u plotseling vindt dat uw site een gebeurtenis met veel verkeer ondergaat, kunt u een [Support Ticket] (/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) indienen om tijdelijke extra cloudcapaciteit voor uw Adobe Commerce in de cloudinfrastructuur aan te vragen.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
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

Om tijdelijke extra wolkencapaciteit aan te vragen, leg het Ticket van de a [ Steun ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) bij het Centrum van de Steun van Adobe Commerce met de volgende informatie voor:

>[!NOTE]
>
>De *keus van het Verzoek van de Vakantiedruk 0} is slechts een optie tussen de maanden van Oktober en van December.*

1. Selecteer het [!DNL Adobe Commerce] product dat u wilt ondersteunen voor:
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Vul de volgende velden in:
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(zorg ervoor deze duidelijk de kwestie en de context beschrijven.)*

1. Selecteer *Verzoek van de Verandering van de Infrastructuur* van het **[!UICONTROL Issue Reason]** dropdown menu.

1. Kies de **[!UICONTROL Environment]** in het vervolgkeuzemenu.

1. Selecteer de juiste **[!UICONTROL Product Version]** in het vervolgkeuzemenu.

1. Kies *het Project van de Wolk Resize (vCPU)* van het **[!UICONTROL Which Infra Change you would like to do today]** dropdown menu.

1. **selecteer[!UICONTROL Architecture]**:
   * *StandaardArchitectuur:* Uitgezochte *Volgende Beschikbare Grootte* van **selecteer de Grootte** dropdown menu.
   * *Schaalde Architectuur:* wanneer geselecteerd, verandert het scherm om twee extra gebieden te tonen:
      * *Grootte voor de Knoop van het Web*
      * *Grootte voor de Knoop van de Dienst* *(ga de gewenste grootten voor elke knoop in.)*

1. Voer de **[!UICONTROL From Date]** in UTC-indeling (datum en tijd) in.

1. Voer de **[!UICONTROL To Date]** in UTC-indeling (datum en tijd) in.

1. Verstrek **[!UICONTROL Project URL]** *(die onder https://accounts.magento.cloud/, typisch in het formaat `https://[REGION].magento.cloud/projects/PROJECT_ID` wordt gevonden)*

1. Voer de **[!UICONTROL Project ID]** in.

1. Geef **[!UICONTROL Affected URL]** *op (moet beginnen met `http://` of `https://`.)*

1. Selecteer **[!UICONTROL Priority]** .

1. Selecteer **[!UICONTROL Business Impact]** .

1. Bevestigen **[!UICONTROL Time Zone]** *(bijv., `(UTC-5:00) Indiana (East)`)*

1. Enter **[!UICONTROL Phone Number]** *(bijv., `+12015550123`)*

1. Klik op **[!UICONTROL Submit]** om de kwestie van de ondersteuning te voltooien.

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
   * [CPU-toewijzingsberekening voor Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Controleren of de host moet worden bijgewerkt voor Adobe Commerce in de cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [CPU-configuratie van host controleren op Adobe Commerce in cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Voor informatie over hoe te om stroomonderbrekingen te identificeren, verwijs naar [ uitvallen voor Adobe Commerce op wolk ](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) in onze basis van de steunkennis identificeren en meten.
* Raadpleeg de volgende artikelen in de documentatie voor ontwikkelaars voor informatie over het verbeteren van de prestaties van de site om te voorkomen dat u een capaciteitsuitbreiding moet gebruiken:
   * [Afbeeldingsgrootte](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [In cache plaatsen van volledige pagina](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-gereedschappen](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
