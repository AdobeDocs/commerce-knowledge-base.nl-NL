---
title: Monitoringoverzicht [!DNL Adobe Commerce on cloud pro infrastructure]
description: Dit document bevat informatie over Adobe Commerce-infrastructuurbewaking en -meldingen.
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 4926bcff19b8c4c7e2a9a9dfb0cb1fc72a9821ba
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Monitoringoverzicht [!DNL Adobe Commerce on cloud pro infrastructure]

Dit document bevat informatie over Adobe Commerce-infrastructuurbewaking en -meldingen.

De controle laat verkopers, systeemintegrators, en interne teams van de Adobe toe om plaatsbeschikbaarheid en ontoereikende schijfruimte problemen op te lossen.

## Probleemoplossing en -oplossing

Adobe Commerce-instanties bevatten over het algemeen aangepaste code en configuraties. Adobe biedt geen ondersteuning voor problemen met aangepaste code en configuraties en lost deze problemen niet op. Adobe helpt handelaren problemen in onze kennisbasis op te lossen en te identificeren en biedt aanbevolen oplossingen en beste praktijken voor preventie en oplossing. Wij moedigen handelaren en partners aan om de onderstaande tabellen te gebruiken om te begrijpen wat wordt gecontroleerd en wie verantwoordelijk is voor de oplossing.

Als meldingen worden geactiveerd, stuurt het Adobe Commerce-supportteam het probleem op. Als deel van de triage, foutenlogboeken, en andere middelen worden geanalyseerd. Op basis van de proefversie, extra [!DNL Zendesk] de steunkaartjes worden gecreeerd of aan handelaren of partners (in het geval van douaneupdates) of aan de interne teams van de Adobe om de kwestie op te lossen.

## Adobe Commerce: standaardbewaking

De onderstaande gebeurtenissen worden gecontroleerd en het Adobe Commerce-team neemt de nodige stappen om geïdentificeerde problemen op te lossen en te melden.

## De beschikbaarheid van de plaats controleren

| Beschikbaarheid van site | Beschrijving |
|------------|------------|
| **Monitoringdoelstelling** | De beschikbaarheid van de site bijhouden. |
| **Instrumenteerd op** | Enkel [!DNL URL] geselecteerd voor hoog [!DNL SLA]. |
| **Beschrijving** | De beschikbaarheid van de plaats wordt bepaald gebaseerd op de drempels die rond metrisch worden gevormd. De melding dat de site uitvalt wordt geactiveerd als de controle gedurende 10 minuten mislukt en er geen actieve implementatie wordt uitgevoerd. |
| **Ontvanger van melding** | Merchant/Partner en Adobe. |
| **Actie via Adobe** | Verantwoordelijk voor het triageren en corrigeren van het probleem als het gaat om de Adobe Commerce-infrastructuur. |
| **Handelsbemiddeling** | Verantwoordelijk voor het oplossen van de kwestie als veroorzaakt door veranderingen of douanecode die door handelaar/partner wordt geïntroduceerd. Raadpleeg voor het oplossen van problemen: [Problemen met site-onderaan oplossen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html). |

## Controle van de schijfruimte

| Controle van de schijfruimte | Beschrijving |
|------------|------------|
| **Monitoringdoelstelling** | Schijfruimtegebruik volgen. |
| **Instrumenteerd op** | [!DNL MySQL] schijf en media schijfpartities. |
| **Metrisch** | De vrije schijfruimte wordt elke minuut gecontroleerd op de gastheer. De waarschuwing wordt opgeheven als slechts 5% of 2 GB vrije ruimte wordt verlaten. De kritieke drempel die bij de resterende vrije ruimte wordt geplaatst is 2% of 1 GB. |
| **Beschrijving** | Het bericht wordt verzonden gebaseerd op de drempels die rond vrije schijfruimte voor de gastheer worden gevormd. Er wordt automatisch een keer extra schijfruimte toegevoegd aan de relevante koppeling ([!DNL MySQL] of media) om een uitval van een site te voorkomen en de handelaar tijd te geven om schijfruimte te wissen en/of om code of logbestanden te identificeren en op te lossen die tot een snelle toename van het schijfgebruik leiden. |
| **Ontvanger van melding** | Merchant/Partner en Adobe. |
| **Actie via Adobe** | Stem automatisch het ondersteuningsticket op en er wordt automatisch extra schijfruimte toegevoegd aan de relevante koppeling ([!DNL MySQL] of media) om te voorkomen dat een site wordt afgebroken. |
| **Handelsbemiddeling** | Raadpleeg de volgende bronnen voor waarschuwingen over schijfruimte op het huidige waarschuwingsniveau: <ul><li>[[!DNL Managed alerts for Adobe Commerce]: waarschuwing voor schijf](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-warning-alert.html)</li><li>[[!DNL Managed alerts for Adobe Commerce]: kritieke schijf](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-disk-critical-alert.html) </li></ul> |
