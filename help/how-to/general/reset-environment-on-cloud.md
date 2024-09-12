---
title: De Adobe Commerce-omgeving herstellen op cloudinfrastructuur
description: In dit artikel worden verschillende scenario's getoond voor het terugdraaien van een omgeving op Adobe Commerce op cloudinfrastructuur.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 598459365cad811966ed529356cb9ab876f49a38
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 0%

---

# De Adobe Commerce-omgeving herstellen op cloudinfrastructuur

In dit artikel worden verschillende scenario&#39;s getoond voor het terugdraaien van een omgeving op Adobe Commerce op cloudinfrastructuur.

Kies de meest geschikte optie voor uw kwestie:

* Als u activiteit (geplande plaatsing of verbetering) hebt gepland - [ Scenario 1: Geplande activiteit) ](#scen1).
* Als u een geldige momentopname hebt - [ Scenario 2: herstel een momentopname ](#scen2).
* Als u een stabiele bouwstijl hebt, maar geen geldige momentopname - [ Scenario 3: Geen momentopname, bouwt stabiel (de verbinding van SSH beschikbaar) ](#scen3).
* Als de bouwstijl gebroken is en u geen geldige momentopname hebt - [ Scenario 4: Geen momentopname; bouwt gebroken (geen verbinding SSH) ](#scen4).

## Scenario 1: Geplande activiteit

Met een geplande implementatie of upgrade kunt u het eenvoudigst en aanbevolen [!UICONTROL Rollback] zijn dat de leverancier, als onderdeel van uw voorbereidingen, het volgende doet:

>[!NOTE]
>
>Test deze stappen altijd eerst in de **[!UICONTROL Staging Environment]** .

<u> Vijf dagen voorafgaand aan de verbetering/plaatsingsactiviteiten </u>:

1. Controleer de grootte van de huidige database.
1. Controleer of er voldoende schijfruimte op `/data/exports` is om een [!UICONTROL Database Dump] vast te houden. Als u niet genoeg schijfruimte hebt, verwijdert u ongewenste gegevens of maakt u een ondersteuningscase en vraagt u de schijf uit te breiden.

<u> op de dag van de veranderingen </u>:

1. Plaats de website in [!UICONTROL Maintenance Mode] .
Lees meer over [ toelaten of onbruikbaar maken [!UICONTROL Maintenance Mode] ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) in onze gebruikersgids, en [[!UICONTROL Maintenance Mode] opties voor verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) in onze verbeteringsgids.
1. Uitsnijdtaken uitschakelen. Lees meer over het onbruikbaar maken van kroonbanen in onze [ handleiding van de eigenschappen van kronen ](<https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>).
1. Neem een lokale [[!UICONTROL Database Dump] ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u> als a [!UICONTROL Rollback] </u> wordt vereist:

1. Als Toepassingen zoals [!DNL MariaDB] zijn bijgewerkt als onderdeel van deze geplande activiteit, moet u de toepassing eerst opnieuw installeren op een vorige versie.
1. [!UICONTROL Rollback] De database met de lokale [!UICONTROL Database Dump] en importeer deze opnieuw in [!DNL MariaDB] .
1. [!UICONTROL Rollback] de code via [!DNL Git] naar een vorige werkende versie.

Het gebruiken van [!UICONTROL Snapshots] is niet de geadviseerde manier voor verbetering/geplande activiteit [!UICONTROL rollbacks/restores], aangezien het veel langer duurt om de gegevens terug te winnen vergeleken bij lokaal [!UICONTROL Database Dump], zoals hierboven genomen in Stap 2 van **als a [!UICONTROL Rollback]** sectie wordt vereist.

[!UICONTROL Snapshots] worden niet op de knoop/server gehouden, worden zij gehouden op een afzonderlijk opslagblok, en aangezien dat gegeven van de blokopslag over het netwerk aan een nieuwe schijf moet worden overgebracht, vergt het tijd in het proces. Die nieuwe schijf wordt dan op de knoop opgezet klaar voor herwinning/invoer op de originele schijf die met de knoop/de server wordt verbonden.

Wanneer u dit vergelijkt met het importeren van een lokale [!UICONTROL Database Dump] , kunnen de gegevens al worden opgehaald op het knooppunt of de server. Daarom wordt veel tijd opgeslagen omdat alleen een [!UICONTROL Database Import] vereist is.

## Scenario 2: Een momentopname herstellen

Lees: [ herstel een momentopname op Adobe Commerce op wolkeninfrastructuur ](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Het maken van een momentopname moet onze eerste stap zijn nadat u Adobe Commerce hebt benaderd via een account voor de cloud-infrastructuur en voordat u grote wijzigingen aanbrengt. Het is een goede praktijk en hoogst geadviseerd.

Lees: [ creeer een momentopname ](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) in onze ontwikkelaarsdocumentatie.

## Scenario 3: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH)

Deze sectie toont hoe te om een milieu terug te stellen wanneer u geen momentopname hebt gecreeerd maar tot het milieu via SSH kan toegang hebben.

De stappen zijn:

1. Configuratiebeheer uitschakelen.
1. Verwijder de Adobe Commerce-software.
1. Stel de [!DNL git] vertakking opnieuw in.

Na het uitvoeren van deze stappen:

* De Adobe Commerce-installatie keert terug naar de toestand Vanilla (database hersteld; configuratie van implementatie verwijderd; mappen onder `var` gewist).
* De [!DNL git] -vertakking is in het verleden teruggezet naar de gewenste status.

Lees de gedetailleerde stappen hieronder.

### Stap 0 (Vereiste): Verwijder config.php om het Beheer van de Configuratie onbruikbaar te maken

Wij moeten het Beheer van de Configuratie onbruikbaar maken zodat het niet automatisch de vorige configuratiemontages tijdens plaatsing toepast.

Als u Configuration Management wilt uitschakelen, moet u ervoor zorgen dat de map `/app/etc/` het `config.php` -bestand niet bevat.

Ga als volgt te werk om het configuratiebestand te verwijderen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verwijder het configuratiebestand: `rm app/etc/config.php`

Lees meer over Configuratiebeheer:

* [ vermindert plaatsingsonderbreking op Adobe Commerce op wolkeninfrastructuur ](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze basis van steunkennis.
* [ het beheer van de Configuratie voor opslagmontages ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in onze ontwikkelaarsdocumentatie.

### Stap 1: De Adobe Commerce-software verwijderen met de opdracht Setup:verwijderen


Als u de Adobe Commerce-software verwijdert, wordt de database neergezet en hersteld, wordt de implementatieconfiguratie verwijderd en worden mappen onder `var` gewist.

Lees: [ desinstalleert de software van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in onze ontwikkelaarsdocumentatie.

Voer de volgende stappen uit om de Adobe Commerce-software te verwijderen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Uitvoeren `setup:uninstall` : `bin/magento setup:uninstall`
1. Verwijderen bevestigen.

Het volgende bericht wordt weergegeven om te bevestigen dat het verwijderen is gelukt:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dit betekent dat we onze Adobe Commerce-installatie (inclusief DB) hebben teruggezet naar de authentieke (Vanilla) staat.

### Stap 2: De [!DNL git] vertakking herstellen

Met [!DNL git] reset, keren we de code terug naar de gewenste status in het verleden.

1. De omgeving klonen naar uw lokale ontwikkelomgeving. U kunt de opdracht kopiëren in de Cloud Console:    ![ copy_git_clone.png ](assets/copy_git_clone.png)
1. Open de geschiedenis van uw verplichtingen. Gebruik `--reverse` om de historie in omgekeerde volgorde weer te geven voor meer gemak: `git log --reverse`
1. Selecteer de commit hash waarop u goed bent geweest. Om code aan zijn authentiek staat (Vanilla) terug te stellen, vind zeer eerste begaan die uw tak (milieu) creeerde.
   ![ alt tekst ](image.png)
1. Harde [!DNL git] reset toepassen: `git reset --h <commit_hash>`
1. Push changes to server: `git push --force <origin> <branch>`

Nadat u deze stappen hebt uitgevoerd, wordt de [!DNL git] -vertakking opnieuw ingesteld en is de gehele [!DNL git] -wijziging gewist. De laatste push van [!DNL git] activeert de herimplementatie om alle wijzigingen toe te passen en Adobe Commerce opnieuw te installeren.

## Scenario 4: Geen opname; build verbroken (geen [!DNL SSH] verbinding)

In deze sectie wordt getoond hoe u een omgeving opnieuw kunt instellen in een kritieke toestand: de implementatieprocedure kan er niet in slagen een werkende toepassing te ontwikkelen, waardoor de [!DNL SSH] -verbinding niet beschikbaar is.

In dit scenario moet u eerst de werkstatus van uw Adobe Commerce-toepassing herstellen met behulp van [!DNL git] reset en vervolgens de Adobe Commerce-software verwijderen (om de database neer te zetten en te herstellen, de implementatieconfiguratie te verwijderen, enz.). Het scenario omvat dezelfde stappen als in scenario 3, maar de volgorde van de stappen is verschillend en er is een extra step - force reïntegratie. De stappen zijn:

1. [Herstel de  [!DNL git]  tak.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Configuratiebeheer uitschakelen.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Verwijder de Adobe Commerce-software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Forceer opnieuw implementeren.

Na het uitvoeren van deze stappen, zult u de zelfde resultaten hebben zoals in Scenario 3.

### Stap 4: Opnieuw inzetten forceren

Leg vast (dit zou leeg kunnen zijn begaan, hoewel wij het niet adviseren) en duw het aan de server om redistribueren te teweegbrengen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Als instellen mislukt:verwijderen, database handmatig opnieuw instellen

Als het uitvoeren van de opdracht `setup:uninstall` mislukt met een fout en niet kan worden voltooid, wordt de DB mogelijk handmatig gewist met de volgende stappen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verbind met de DB MySQL: `mysql -h database.internal` (Voor Pro milieu&#39;s zie: [ Opstelling de dienst MySQL ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Zet de `main` DB neer: `drop database main;`
1. Maak een lege `main` DB: `create database main;`
1. Verwijder de volgende configuratiebestanden: `config.php`, `config.php.bak`, `env.php`, `env.php.bak`

Na het terugstellen van OB, [ maak a  [!DNL git]  duw aan het milieu om opnieuw op te stellen ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) en Adobe Commerce aan nieuw gecreeerd OB te installeren. Of [ stel het redistribueren bevel ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands) in werking.
