---
title: 'De "Plaatsing ontbreekt met "Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1"'
description: 'In dit artikel wordt gesproken over de oorzaken en oplossingen voor de Adobe Commerce met betrekking tot de cloudinfrastructuur, waar de constructiefase van het implementatieproces mislukt, en de foutmelding wordt samengevat met: *"Fout bij het bouwen van project: De bouwhaak is mislukt met statuscode 1"*."'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# De plaatsing ontbreekt met &quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1

Dit artikel spreekt over de oorzaken en de oplossingen voor Adobe Commerce op de kwestie van de wolkeninfrastructuur, waar de bouwstijlfase van het plaatsingsproces ontbreekt, en het foutenbericht wordt samengevat met: *&quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1&quot;*.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

<u> Stappen om </u> te reproduceren:

Trigger de plaatsing manueel of door een fusie, duw, of synchronisatie van uw milieu uit te voeren.

<u> Verwacht resultaat </u>:

De implementatie is voltooid.

<u> Werkelijk resultaat </u>:

1. De bouwfase mislukt en het hele implementatieproces zit vast.
1. In het logboek van de plaatsingsfout, beëindigt het foutenbericht met: *&quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1. Geaborteerde build&quot;.*

## Oorzaak

Er zijn meerdere redenen waarom het bouwen van een omgeving mislukt. Gewoonlijk, in het plaatsingslogboek, zult u een lange foutenmelding zien, waar het eerste deel specifieker betreffende de reden zou zijn, en de conclusie *&quot;Fout bouwend project: De bouwstijlhaak ontbrak met statuscode 1. Geaborteerde build&quot;.*

Als u het eerste probleemspecifieke deel nader bekijkt, kunt u het probleem beter identificeren. Hier zijn de gemeenschappelijkste, en de volgende sectie verstrekt oplossingen voor hen:

* Er is geen beschikbare opslagruimte.
* Onjuiste configuratie ECE-Tools.
* De patch die u wilt toepassen, is niet compatibel met uw Adobe Commerce-versie of veroorzaakt conflicten met andere patches die zijn toegepast of met uw aanpassingen.
* De problemen met de code van douanemodules verhinderen met succes de bouw.

## Oplossing

* Controleer of er voldoende opslagruimte is. Voor informatie over hoe te om beschikbare ruimte te controleren, zie de [ schijfruimte van de Controle op wolkenmilieu gebruikend CLI ](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) artikel. U kunt overwegen de logboekfolders en/of het verhogen van schijfruimte te reinigen.
* Zorg ervoor dat ECE-Tools correct zijn geconfigureerd.
* Controleer of het probleem wordt veroorzaakt door de pleister. Los het conflict op of contacteer [ de Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Zie hieronder voor meer informatie.
* Controleer of het probleem wordt veroorzaakt door de aangepaste extensie. Los het conflict op of contacteer de uitbreidingsontwikkelaars voor de oplossing.

De volgende alinea&#39;s bevatten nadere bijzonderheden.

### Logboeken opschonen en/of ruimte vergroten

Voor opruiming in aanmerking te nemen mappen:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Voor details op hoe te om schijfruimte te verhogen als u op Adobe Commerce op het planarchitectuur van de Aanzet van de wolkeninfrastructuur bent, zie [ de schijfruimte van de Verhoging voor het milieu van de Integratie op wolk ](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Dezelfde instructies kunnen worden gebruikt voor het vergroten van de ruimte van Adobe Commerce op de integratie-omgeving van de cloudinfrastructuur Pro. Voor ProProductie/het Staging, moet u een kaartje aan [ Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) indienen, en verhoogde schijfruimte verzoeken. Maar het wordt gecontroleerd door Platform. Maar doorgaans hoeft u dit niet te doen voor de Staging/Production of Pro-architectuur, aangezien Adobe Commerce deze parameters voor u controleert en u waarschuwt en/of acties uitvoert volgens het contract.

### Zorg ervoor dat ECE-gereedschappen correct zijn geconfigureerd

1. Zorg ervoor dat de build-haken correct zijn gedefinieerd in het `magento.app.yaml` -bestand. Als u Adobe Commerce 2.2.X gebruikt, moeten de haken voor het bouwen als volgt worden gedefinieerd:

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Gebruik de [ Verbetering aan artikel-hulpmiddelen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) artikel voor verwijzing.

1. Zorg ervoor dat het pakket ECE-tools aanwezig is in het `composer.lock` -bestand door de volgende opdracht uit te voeren:    <pre><code class="language-bash"> grep &quot;<code class="language-yaml"> &quot;naam&quot;: &quot;magento/ece-tools&quot;</code>&#39; composer.lock</code></pre>    Als ze worden opgegeven, ziet het antwoord er als volgt uit:    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Zie [ Verbetering aan artikel-hulpmiddelen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) artikel voor verwijzing.

### Veroorzaakt de pleister het probleem?

Als het de toegepaste flard is die het milieu verhindert met succes te bouwen, zult u iets gelijkend op het volgende in opstellen logboek zien:

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Deze foutberichten betekenen dat de patch die u wilt toepassen, is gemaakt voor een andere Adobe Commerce-versie of conflicteert met uw aanpassingen of eerder toegepaste patches. Probeer om het conflict op te lossen of contact [ Steun van Adobe Commerce ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Veroorzaakt de uitbreiding het probleem?

Als het de douaneuitbreiding is die het milieu om met succes verhindert te bouwen, zult u de naam van de douanemodule(en) die in het plaatsingslogboek worden vermeld, samen met het bijzondere conflict zien door deze module wordt veroorzaakt. Los het conflict op of contacteer de uitbreidingsontwikkelaars voor de oplossing.

### Controleer of de wijzigingen zijn toegepast

Leg de wijzigingen vast en duw op deze. Dit zal de plaatsing automatisch teweegbrengen.
