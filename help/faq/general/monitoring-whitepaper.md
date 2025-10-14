---
title: Bewaking van feitenblad voor  [!DNL Adobe Commerce on cloud pro infrastructure]
description: Dit document bevat informatie over Adobe Commerce-infrastructuurbewaking en -meldingen.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Werkblad controleren voor [!DNL Adobe Commerce on cloud pro infrastructure]

Dit document bevat informatie over Adobe Commerce-infrastructuurbewaking en -meldingen.

De controle laat verkopers, systeemintegrators, en interne teams van Adobe toe om plaatsbeschikbaarheid en ontoereikende schijfruimte problemen op te lossen.

## Probleemoplossing en -oplossing

Adobe Commerce-instanties bevatten over het algemeen aangepaste code en configuraties. Adobe biedt geen ondersteuning voor problemen met aangepaste code en configuraties en lost deze problemen niet op. Adobe helpt handelaren problemen op te lossen en problemen in onze kennisbasis te identificeren en biedt aanbevolen oplossingen en beste praktijken voor preventie en oplossing. Wij moedigen handelaren en partners aan om de onderstaande tabellen te gebruiken om te begrijpen wat wordt gecontroleerd en wie verantwoordelijk is voor de oplossing.

Als meldingen worden geactiveerd, stuurt het Adobe Commerce-supportteam het probleem op. Als deel van de triage, foutenlogboeken, en andere middelen worden geanalyseerd. Op basis van het triage-abonnement worden extra [!DNL Zendesk] ondersteuningstickets gemaakt voor handelaren of partners (in het geval van aangepaste updates) of voor interne teams van Adobe om het probleem op te lossen.

## Adobe Commerce: standaardbewaking

De onderstaande gebeurtenissen worden gecontroleerd en het Adobe Commerce-team neemt de nodige stappen om geïdentificeerde problemen op te lossen en te melden.

## De beschikbaarheid van de plaats controleren

| Beschikbaarheid van site | Beschrijving |
|------------|------------|
| **Doel van de Controle** | De beschikbaarheid van de site bijhouden. |
| **Instrumented op** | Enkel [!DNL URL] geselecteerd voor hoog [!DNL SLA] . |
| **Beschrijving** | De beschikbaarheid van de plaats wordt bepaald gebaseerd op de drempels die rond metrisch worden gevormd. De melding dat de site uitvalt wordt geactiveerd als de controle gedurende 10 minuten mislukt en er geen actieve implementatie wordt uitgevoerd. |
| **Ontvanger van het Bericht** | Merchant/Partner en Adobe. |
| **Actie door Adobe** | Verantwoordelijk voor het triageren en corrigeren van het probleem als het gaat om de Adobe Commerce-infrastructuur. |
| **Actie door handelaar** | Verantwoordelijk voor het oplossen van de kwestie als veroorzaakt door veranderingen of douanecode die door handelaar/partner wordt geïntroduceerd. Voor het oplossen van problemen, gelieve te verwijzen naar: [&#x200B; Plaats neer Troubleshooter &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=nl-NL). |

## Controle van de schijfruimte

| Controle van de schijfruimte | Beschrijving |
|------------|------------|
| **Doel van de Controle** | Schijfruimtegebruik volgen. |
| **Instrumented op** | [!DNL MySQL] schijf en media schijfpartities. |
| **Metrisch** | De vrije schijfruimte wordt elke minuut gecontroleerd op de gastheer. De waarschuwing wordt opgeheven als slechts 5% of 2 GB vrije ruimte wordt verlaten. De kritieke drempel die bij de resterende vrije ruimte wordt geplaatst is 2% of 1 GB. |
| **Beschrijving** | Het bericht wordt verzonden gebaseerd op de drempels die rond vrije schijfruimte voor de gastheer worden gevormd. Er wordt automatisch extra schijfruimte één keer toegevoegd aan de relevante koppeling ([!DNL MySQL] of media) om te voorkomen dat een site wordt afgebroken en om de handelaar tijd te geven om schijfruimte te wissen en/of om code of logbestanden te identificeren en op te lossen die leiden tot een snelle toename van schijfgebruik. |
| **Ontvanger van het Bericht** | Merchant/Partner en Adobe. |
| **Actie door Adobe** | Verhoog automatisch het steunkaartje en extra schijfruimte wordt automatisch toegevoegd aan de relevante onderstel ([!DNL MySQL] of media) om een plaatsafval te verhinderen. |
| **Actie door handelaar** | Raadpleeg de volgende bronnen voor waarschuwingen over schijfruimte op het huidige waarschuwingsniveau: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: waarschuwing voor een schijffout &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce]: kritieke schijf alarm &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
