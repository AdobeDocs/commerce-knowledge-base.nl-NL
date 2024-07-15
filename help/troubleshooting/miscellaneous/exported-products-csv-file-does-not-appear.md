---
title: Het CSV-bestand met geëxporteerde producten wordt niet weergegeven
description: Dit artikel bevat een oplossing voor het probleem waarbij u probeert producten te exporteren naar een CSV-bestand in Commerce Admin, maar het bestand wordt niet weergegeven.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: d55702ab97f3770d0ec71322f6c24448f0169ad4
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Het CSV-bestand met geëxporteerde producten wordt niet weergegeven

Dit artikel bevat een oplossing voor het probleem waarbij u probeert producten te exporteren naar een CSV-bestand in Commerce Admin, maar het bestand wordt niet weergegeven.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, alle [ gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Probleem

<u> Stappen om te reproduceren </u>

Eerste vereisten: **voeg Geheime Sleutel aan URLs** optie toe wordt geplaatst aan *ja*. De optie wordt gevormd in Commerce Admin onder **Opslag** > **Configuratie** > **Geavanceerd** > **Admin** > **Veiligheid**.

1. In Admin, navigeer aan **Systeem** > **Overdracht van Gegevens** > **de Uitvoer**.

   ![ magento_export_products_2.3.4.png ](assets/magento_export_products_2.3.4.png)

1. Selecteren
   * **Type van Entiteit**: *Producten*
   * **Formaat van het Dossier van de Uitvoer**: *CSV*
   * **de Bijlage van het Gebied**: verlaten ongecontroleerd.
1. Klik **verdergaan**.
1. Het volgende bericht wordt getoond: *&quot;Bericht wordt toegevoegd aan rij, wacht om uw dossier spoedig te krijgen&quot;*.

<u> Verwacht resultaat </u>

Het .csv-bestand met de geëxporteerde producten wordt binnen een paar minuten in het raster weergegeven.

<u> Werkelijk resultaat </u>

Het CSV-bestand met de geëxporteerde producten wordt niet binnen 10 minuten of langer weergegeven in het raster.

## Oorzaak

Een bekend probleem met de exportfunctionaliteit in Adobe Commerce-toepassingsonderdeel versie 2.3.2.

## Oplossing

Er zijn twee mogelijke oplossingen voor dit probleem:

* Schakel de optie Geheime sleutel toevoegen aan URL uit.
* Voer de opdracht `bin/magento queue:consumers:start exportProcessor` handmatig uit en configureer deze eventueel voor uitsnijden.

Zie de details voor beide opties in de volgende alinea&#39;s.

### Schakel de optie Geheime sleutel toevoegen aan URL uit

1. In Admin, navigeer aan **Opslag** > **Configuratie** > **Geavanceerd** > **Admin** > **Veiligheid**.
1. Plaats **Geheime Sleutel aan URLs** optie aan *Nr.*
1. Klik **sparen Config**.
1. Reinig geheime voorgeheugen onder **Systeem** > **Hulpmiddelen** > **Beheer van het Geheime voorgeheugen** of door in werking te stellen    ```bash    bin/magento cache:clean``` of in de Admin.

### Voer de exportopdracht handmatig en optioneel uit om de opdracht als een snijtaak toe te voegen

Voer de opdracht `bin/magento queue:consumers:start exportProcessor` uit om het exportbestand op te halen. Nadat u dit hebt uitgevoerd, moet het bestand in het raster worden weergegeven.


Als u het proces optioneel als een snijtaak wilt toevoegen, moet u de variabele `CRON_CONSUMERS` aan het `.magento.env.yaml` -bestand toevoegen.

#### Proces toevoegen als een snijtaak (optioneel)

1. Zorg ervoor dat de uitsnede is ingesteld en geconfigureerd. Zie [ de banen van de opstelling cron ](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) voor details.
1. Voer het volgende bevel uit om een lijst van gebruikers van de berichtrij terug te keren:     `./bin/magento queue:consumers:list`
1. Voeg het volgende toe aan uw `.magento.env.yaml` -bestand in de hoofdmap van de toepassing en neem de consumenten op die u wilt toevoegen. Hier ziet u bijvoorbeeld de consument die nodig is voor exportverwerking:

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Vervolgens drukt u op dit bijgewerkte bestand en implementeert u de omgeving opnieuw. Ook verwijzing [ voegt de banen van de douanecurn aan uw project ](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) in onze ontwikkelingsdocumentatie toe.

>[!NOTE]
>
>Als u het `.magento.env.yaml` -bestand niet kunt vinden voor uw omgeving en u denkt dat het is verwijderd, moet u een nieuw `.magento.env.yaml` maken. Deze is mogelijk aanvankelijk leeg, u kunt desgewenst gegevens toevoegen. Verwijzing de volgende artikelen: [ vorm milieuvariabelen voor plaatsing ](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) en [ de variabelen van het Milieu ](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) in onze ontwikkelaarsdocumentatie.

>[!TIP]
>
>[ YAML dossiers ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) zijn gevoelig geval en staan geen lusjes toe. Wees voorzichtig met het gebruik van consistente inspringing in het .magento.env.yaml-bestand, anders werkt de configuratie mogelijk niet naar behoren. De voorbeelden in de documentatie en in het voorbeeldbestand gebruiken een inspringing met twee spaties. Gebruik de Griekenland-hulpmiddelen bevestigen bevel om uw configuratie te controleren.

>[!NOTE]
>
>Op Adobe Commerce op de Pro projecten van de wolkeninfrastructuur, moet de [ auto-crons eigenschap ](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) op uw Adobe Commerce op wolkeninfrastructuur worden toegelaten alvorens u de banen van de douaneKneep aan het Opvoeren en van de Productie milieu&#39;s kunt toevoegen gebruikend `.magento.app.yaml`. Als deze eigenschap niet wordt toegelaten, [ creeer een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), om de baan te hebben die voor u wordt toegevoegd.
