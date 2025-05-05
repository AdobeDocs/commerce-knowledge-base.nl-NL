---
title: Klantprofielen die niet in Experience Platform worden weergegeven
description: Dit artikel verstrekt het oplossen van problemenstappen als uw gegevens van het klantenprofiel niet in het Experience Platform verschijnen wanneer het gebruiken van de  [!DNL Data Connection]  uitbreiding.
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Klantprofielen die niet in Experience Platform worden weergegeven

Dit artikel bevat stappen voor het oplossen van problemen als de gegevens van uw klantprofiel niet in het Experience Platform worden weergegeven wanneer u de extensie Gegevensverbinding gebruikt.

## Betrokken producten en versies

* Adobe Commerce 2.4.x met geïnstalleerde [!DNL Data Connection] extensie

## Probleem

U hebt geïnstalleerd en gevormd de [[!DNL Data Connection] ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/data-connection/overview) uitbreiding en hebt de gegevens van het klantenprofiel om naar het Experience Platform toegelaten worden verzonden, maar dat profielgegeven verschijnt niet in het Experience Platform.

## Oplossing

Controleer het volgende als er geen gegevens over het klantprofiel in het Experience Platform worden weergegeven:

### Bevestig dat de nieuwste versie van [!DNL Data Connection] is geïnstalleerd

Controleer of u de nieuwste versie van de extensie `experience-platform-connector` hebt geïnstalleerd.

Zie de [[!DNL Data Connection]  nota&#39;s van de uitbreidingsversie ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/data-connection/release-notes) voor informatie over de recentste versie.

>[!NOTE]
>
>De meest recente versie van de extensie [!DNL Data Connection] bevat de module `customers-connector` , die verantwoordelijk is voor het verzenden van profielgegevens naar het Experience Platform. De module `customers-connector` moet versie `1.2.0` of hoger zijn.

### Bevestig de klant-schakelaar module wordt gevormd

Bevestig dat de module `customers-connector` is geconfigureerd op basis van het installatiescenario.

#### Adobe Commerce on Cloud-infrastructuur

1. Schakel de globale variabele `ENABLE_EVENTING` in `.magento.env.yaml` in. [ leer meer ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global).

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. Pas bijgewerkte bestanden toe op de cloud-omgeving en druk ze op deze bestanden. Wanneer de plaatsing wordt gebeëindigd, laat het verzenden van gebeurtenissen met het volgende bevel toe:

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Adobe Commerce-installatie ter plaatse

Voer de volgende opdrachten uit om het genereren van code en Adobe Commerce Events in te schakelen:

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Bevestig dat u profielgegevens hebt ingeschakeld om te worden vastgelegd en verzonden naar Experience Platform

Controleer in Commerce Admin of de volgende velden zijn ingesteld:

* Controleer in **[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]** of de selectievakjes [!UICONTROL Back office events] en [!UICONTROL Customer profiles] zijn ingeschakeld.
* Zorg ervoor dat het veld *[!UICONTROL Profile Dataset ID]* correct is en een andere gegevensset is dan wat u momenteel gebruikt voor gedrags- en back-office gebeurtenisgegevens.

### Controleren of gebeurtenissen naar staging of productie worden verzonden

1. Voer de volgende opdracht uit om de huidige Adobe Developer-omgeving te tonen:

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. Als de omgeving is ingesteld op *[!UICONTROL Stage]* , wijzigt u deze in *[!UICONTROL Production]* met de volgende opdracht:

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### Query Event Data SaaS-tabel

Verbind en voer de volgende [!DNL SQL] vraag uit om de verslagen van het klantenprofiel te verifiëren verschijnen in
`event_data_saas` en dat er geen fouten zijn:

```sql
Copy code
select * from event_data_saas;
```

### Fouten in het publiceren van gebeurtenissen afhandelen

1. Als de volgende fout optreedt, controleert u of de SaaS-verbindingssleutels voor de sandbox en productie correct zijn:

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. Ga naar de pagina *[!UICONTROL Commerce Services Connector]* in Admin en controleer of de opgegeven toetsen van [!UICONTROL sandbox/production] correct zijn geconfigureerd. Controleer ook of de instellingen van de Commerce-account [!UICONTROL sandbox/production] overeenkomen met die in [!UICONTROL Commerce Services Connector] . Leer [ meer ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey).

### Controleer of de service-id in de lijst van gewenste personen staat en bevestig deze met Adobe Commerce-ondersteuning

1. Controleer of [!UICONTROL Commerce Services Connector] `serviceId` wordt weergegeven in de lijst van gewenste personen in Adobe Commerce.
1. De steun van Adobe Commerce van het contact [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) om de status van de lijst van gewenste personen te bevestigen.

## Gerelateerde lezing

* [[!DNL Data Connection] ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/data-connection/overview) -extensie in de gebruikershandleiding van Commerce Services
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce
