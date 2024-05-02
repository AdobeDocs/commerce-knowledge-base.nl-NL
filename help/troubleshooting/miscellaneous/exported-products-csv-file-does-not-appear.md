---
title: Het CSV-bestand met geëxporteerde producten wordt niet weergegeven
description: Dit artikel bevat een oplossing voor het probleem waarbij u probeert producten te exporteren naar een CSV-bestand in Commerce Admin, maar het bestand wordt niet weergegeven.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: 465eb89cf5c5169b0b459ab7e6bdcbd418781093
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Het CSV-bestand met geëxporteerde producten wordt niet weergegeven

Dit artikel bevat een oplossing voor het probleem waarbij u probeert producten te exporteren naar een CSV-bestand in Commerce Admin, maar het bestand wordt niet weergegeven.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, alle [ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

<u>Stappen om te reproduceren</u>

Vereisten: de **Geheime sleutel toevoegen aan URL&#39;s** optie is ingesteld op *Ja*. De optie is geconfigureerd in Commerce Admin onder **Winkels** > **Configuratie** > **Geavanceerd** > **Beheerder** > **Beveiliging**.

1. Navigeer in Beheer naar **Systeem** > **Gegevensoverdracht** > **Exporteren**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Selecteren
   * **Type entiteit**: *Producten*
   * **Bestandsindeling exporteren**: *CSV*
   * **Veldbehuizing**: Laat los.
1. Klikken **Doorgaan**.
1. Het volgende bericht wordt weergegeven: *&quot;Bericht wordt toegevoegd aan wachtrij, wacht om uw bestand binnenkort op te halen&quot;*.

<u>Verwacht resultaat</u>

Het .csv-bestand met de geëxporteerde producten wordt binnen een paar minuten in het raster weergegeven.

<u>Werkelijk resultaat</u>

Het CSV-bestand met de geëxporteerde producten wordt niet binnen 10 minuten of langer weergegeven in het raster.

## Oorzaak

Een bekend probleem met de exportfunctionaliteit in Adobe Commerce-toepassingsonderdeel versie 2.3.2.

## Oplossing

Er zijn twee mogelijke oplossingen voor dit probleem:

* Schakel de optie Geheime sleutel toevoegen aan URL uit.
* Voer de `bin/magento queue:consumers:start exportProcessor` handmatig te gebruiken en eventueel te configureren voor uitsnijden.

Zie de details voor beide opties in de volgende alinea&#39;s.

### Schakel de optie Geheime sleutel toevoegen aan URL uit

1. Navigeer in Beheer naar **Winkels** > **Configuratie** > **Geavanceerd** > **Beheerder** > **Beveiliging**.
1. Stel de **Geheime sleutel toevoegen aan URL&#39;s** optie voor *Nee.*
1. Klikken **Config opslaan**.
1. Cache opschonen onder **Systeem** > **Gereedschappen** > **Cachebeheer** of via uitvoering    ```bash    bin/magento cache:clean``` of in de Admin.

### Voer de exportopdracht handmatig en optioneel uit om de opdracht als een snijtaak toe te voegen

Als u het exportbestand wilt ophalen, voert u het `bin/magento queue:consumers:start exportProcessor` gebruiken. Nadat u dit hebt uitgevoerd, moet het bestand in het raster worden weergegeven.


Als u het proces optioneel als een snijtaak wilt toevoegen, moet u de opdracht `CRON_CONSUMERS` aan de `.magento.env.yaml` bestand.

#### Proces toevoegen als een snijtaak (optioneel)

1. Zorg ervoor dat de uitsnede is ingesteld en geconfigureerd. Zie [Uitsnijdtaken instellen](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) voor meer informatie.
1. Voer het volgende bevel uit om een lijst van gebruikers van de berichtrij terug te keren:     `./bin/magento queue:consumers:list`
1. Voeg het volgende toe aan uw `.magento.env.yaml` in de hoofdmap van de toepassing en neemt de gebruikers op die u wilt toevoegen. Hier ziet u bijvoorbeeld de consument die nodig is voor exportverwerking:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Vervolgens drukt u op dit bijgewerkte bestand en implementeert u de omgeving opnieuw. Ook verwijzing [Aangepaste uitsnijdtaken toevoegen aan uw project](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Als u de `.magento.env.yaml` bestand voor uw omgeving, en u denkt dat het is verwijderd, moet u een nieuw bestand maken `.magento.env.yaml`. Deze is mogelijk aanvankelijk leeg, u kunt desgewenst gegevens toevoegen. Verwijs naar de volgende artikelen: [Omgevingsvariabelen voor implementatie configureren](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) en [Omgevingsvariabelen](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>In Adobe Commerce over cloud Infrastructure Pro-projecten [automatisch aanmaken, functie](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) moet zijn ingeschakeld op uw Adobe Commerce op cloudinfrastructuur voordat u aangepaste uitsnijdtaken kunt toevoegen aan Faging- en Productieomgevingen met `.magento.app.yaml`. Als deze functie niet is ingeschakeld, [een ondersteuningsticket maken](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), om de taak voor u toe te voegen.
