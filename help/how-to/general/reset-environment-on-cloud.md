---
title: De Adobe Commerce-omgeving herstellen op cloudinfrastructuur
description: In dit artikel worden verschillende scenario's getoond voor het terugdraaien van een omgeving op Adobe Commerce op cloudinfrastructuur.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: ddde2385f1d94194b34e9ed51f6cbda55c916d90
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# De Adobe Commerce-omgeving herstellen op cloudinfrastructuur

In dit artikel worden verschillende scenario&#39;s getoond voor het terugdraaien van een omgeving op Adobe Commerce op cloudinfrastructuur.

Kies de meest geschikte optie voor uw kwestie:

* Als u activiteiten hebt gepland (geplande implementatie of upgrade) - [Scenario 1: Geplande activiteit)](#scen1).
* Als u een geldige momentopname hebt - [Scenario 2: Een momentopname herstellen](#scen2).
* Als u een stabiele build hebt, maar geen geldige momentopname - [Scenario 3: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH)](#scen3).
* Als de build wordt verbroken en u geen geldige momentopname hebt - [Scenario 4: Geen momentopname; build verbroken (geen SSH-verbinding)](#scen4).

## Scenario 1: Geplande activiteit

Met een geplande implementatie of upgrade kunt u het eenvoudigst en aanbevolen [!UICONTROL Rollback] Het is aan de handelaar om als onderdeel van uw voorbereidingen het volgende te doen:

>[!NOTE]
>
>Test deze stappen altijd in uw **[!UICONTROL Staging Environment]** eerst!

<u>Vijf dagen vóór de upgrade-/implementatieactiviteiten</u>:

1. Controleer de grootte van de huidige database.
1. Controleer of u voldoende schijfruimte hebt `/data/exports` om een [!UICONTROL Database Dump]. Als u niet genoeg schijfruimte hebt, verwijdert u ongewenste gegevens of maakt u een ondersteuningscase en vraagt u de schijf uit te breiden.

<u>Op de dag van de wijzigingen</u>:

1. De website plaatsen in [!UICONTROL Maintenance Mode].<br>
Meer informatie over [In- of uitschakelen [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) in onze gebruikershandleiding, en [[!UICONTROL Maintenance Mode] upgradeopties](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) in onze upgradehandleiding.
1. Neem een lokale [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Indien een [!UICONTROL Rollback] is vereist</u>:

1. Als toepassingen zoals [!DNL MariaDB] als onderdeel van deze geplande activiteit is bijgewerkt, moet de toepassing eerst opnieuw zijn geïnstalleerd op een vorige versie.
1. [!UICONTROL Rollback] de database die gebruikmaakt van de lokale [!UICONTROL Database Dump]en importeer deze opnieuw in [!DNL MariaDB].
1. [!UICONTROL Rollback] de code via [!DNL Git] naar een vorige werkversie.

Gebruiken [!UICONTROL Snapshots] is niet de geadviseerde manier om/geplande activiteit te bevorderen [!UICONTROL rollbacks/restores], aangezien het veel langer duurt om de gegevens op te halen in vergelijking met een lokale [!UICONTROL Database Dump], zoals hierboven in stap 2 van de **Indien een [!UICONTROL Rollback] is vereist** sectie.

[!UICONTROL Snapshots] niet op de knoop/de server worden gehouden, worden zij gehouden op een afzonderlijk opslagblok, en aangezien dat gegeven van de blokopslag over het netwerk aan een nieuwe schijf moet worden overgebracht, vergt het tijd in het proces. Die nieuwe schijf wordt dan op de knoop opgezet klaar voor herwinning/invoer op de originele schijf die met de knoop/de server wordt verbonden.

Wanneer u dit vergelijkt met het importeren van een lokale [!UICONTROL Database Dump], zijn de gegevens reeds terugwinnbaar op de knoop/de server, zodat wordt veel tijd bewaard als slechts a [!UICONTROL Database Import] is vereist.

## Scenario 2: Een momentopname herstellen

Lezen: [Een momentopname herstellen op Adobe Commerce op cloudinfrastructuur](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) in onze ontwikkelaarsdocumentatie.

>[!NOTE]
>
>Het maken van een momentopname moet onze eerste stap zijn nadat u Adobe Commerce hebt benaderd via een account voor de cloud-infrastructuur en voordat u grote wijzigingen aanbrengt. Het is een goede praktijk en hoogst geadviseerd.

Lezen: [Een opname maken](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) in onze ontwikkelaarsdocumentatie.

## Scenario 3: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH)

Deze sectie toont hoe te om een milieu terug te stellen wanneer u geen momentopname hebt gecreeerd maar tot het milieu via SSH kan toegang hebben.

De stappen zijn:

1. Configuratiebeheer uitschakelen.
1. Verwijder de Adobe Commerce-software.
1. De [!DNL git] vertakking.

Na het uitvoeren van deze stappen:

* Uw Adobe Commerce-installatie keert terug naar de toestand Vanilla (herstelde database; configuratie van implementatie verwijderd; directory&#39;s onder `var` gewist).
* Uw [!DNL git] vertakking wordt in het verleden teruggezet naar de gewenste status.

Lees de gedetailleerde stappen hieronder.

### Stap 0 (Vereiste): Verwijder config.php om het Beheer van de Configuratie onbruikbaar te maken

Wij moeten het Beheer van de Configuratie onbruikbaar maken zodat het niet automatisch de vorige configuratiemontages tijdens plaatsing toepast.

Om configuratiebeheer onbruikbaar te maken, zorg ervoor dat uw `/app/etc/` map bevat niet de `config.php` bestand.

Ga als volgt te werk om het configuratiebestand te verwijderen:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verwijder het configuratiebestand: `rm app/etc/config.php`

Lees meer over Configuratiebeheer:

* [Implementatiedowntime in Adobe Commerce op cloudinfrastructuur verminderen](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze kennisbasis voor ondersteuning.
* [Configuratiebeheer voor opslaginstellingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in onze ontwikkelaarsdocumentatie.

### Stap 1: De Adobe Commerce-software verwijderen met de opdracht Setup:verwijderen


De Adobe Commerce-software wordt verwijderd en de database wordt hersteld, de implementatieconfiguratie wordt verwijderd en mappen onder `var`.

Lezen: [De Adobe Commerce-software verwijderen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in onze ontwikkelaarsdocumentatie.

Voer de volgende stappen uit om de Adobe Commerce-software te verwijderen:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Uitvoeren `setup:uninstall` : `bin/magento setup:uninstall`
1. Verwijderen bevestigen.

Het volgende bericht wordt weergegeven om te bevestigen dat het verwijderen is gelukt:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dit betekent dat we onze Adobe Commerce-installatie (inclusief DB) hebben teruggezet naar de authentieke (Vanilla) staat.

### Stap 2: De [!DNL git] vertakking

Met [!DNL git] herstellen, herstellen wij de code aan de gewenste staat in het verleden.

1. De omgeving klonen naar uw lokale ontwikkelomgeving. U kunt de opdracht kopiëren in de Cloud Console:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Open de geschiedenis van uw verplichtingen. Gebruiken `--reverse` om geschiedenis in omgekeerde volgorde weer te geven voor meer gemak: `git log --reverse`
1. Selecteer de commit hash waarop u goed bent geweest. Om code aan zijn authentiek staat (Vanilla) terug te stellen, vind zeer eerste begaan die uw tak (milieu) creeerde.
   ![Een commit hash selecteren in de git-console](assets/select_commit_hash.png)
1. Harde toepassen [!DNL git] opnieuw instellen: `git reset --h <commit_hash>`
1. Wijzigingen op de server doorvoeren: `git push --force <origin> <branch>`

Nadat u deze stappen hebt uitgevoerd, [!DNL git] vertakking wordt teruggesteld en de volledige [!DNL git] changelog is duidelijk. De laatste [!DNL git] Druk op de toets om opnieuw te implementeren om alle wijzigingen toe te passen en Adobe Commerce opnieuw te installeren.

## Scenario 4: Geen opname; build verbroken (geen [!DNL SSH] verbinding)

Deze sectie toont hoe te om een milieu terug te stellen wanneer het in een kritieke staat is: de plaatsingsprocedure kan niet in de bouw van een werkende toepassing slagen, zo makend [!DNL SSH] verbinding niet beschikbaar.

In dit scenario moet u eerst de werkstatus van uw Adobe Commerce-toepassing herstellen met [!DNL git] de Adobe Commerce-software opnieuw instellen en vervolgens verwijderen (om de database neer te zetten en te herstellen, de configuratie van de implementatie te verwijderen, enz.). Het scenario omvat dezelfde stappen als in scenario 3, maar de volgorde van de stappen is verschillend en er is een extra step - force reïntegratie. De stappen zijn:

1. [De [!DNL git] vertakking.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
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

Indien het `setup:uninstall` De opdracht mislukt met een fout en kan niet worden voltooid. Mogelijk wordt de DB handmatig met de volgende stappen gewist:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verbinding maken met de MySQL-database: `mysql -h database.internal` (Voor Pro-omgevingen raadpleegt u: [MySQL-service instellen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Zet de DB \&quot;main\&quot; neer: `drop database main;`
1. Lege database \&quot;main\&quot; maken: `create database main;`
1. Verwijder de volgende configuratiebestanden: `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

Nadat u de database opnieuw hebt ingesteld, [een [!DNL git] duwen naar de omgeving om herimplementatie te starten](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) en installeer Adobe Commerce in een nieuwe database. of [Voer de opdracht Opnieuw implementeren uit](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
