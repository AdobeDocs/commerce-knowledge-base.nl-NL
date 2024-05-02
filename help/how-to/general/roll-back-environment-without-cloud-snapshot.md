---
title: Omgeving terugdraaien zonder Cloud-opname
description: Dit artikel bevat twee oplossingen om een omgeving terug te draaien zonder een momentopname van uw omgeving op Adobe Commerce op cloudinfrastructuur.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: f3c976bd44dbc47bd5cc8076f1679d56910cfaf3
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Omgeving terugdraaien zonder Cloud-opname

Dit artikel bevat twee oplossingen om een omgeving terug te draaien zonder een momentopname van uw omgeving op Adobe Commerce op cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op cloudinfrastructuur, [alle ondersteunde versies](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Kies de meest geschikte optie voor uw kwestie:

* Als u een stabiele build hebt, maar geen geldige momentopname - [Scenario 1: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH)](#scen2).
* Als de build wordt verbroken en u geen geldige momentopname hebt - [Scenario 2: Geen opname; build verbroken (geen SSH-verbinding)](#scen3).

## Scenario 1: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH) {#scen2}

Deze sectie toont hoe te om een milieu terug te draaien wanneer u geen momentopname hebt gecreeerd maar tot het milieu via SSH kan toegang hebben.

De stappen zijn:

1. Configuratiebeheer uitschakelen.
1. Verwijder de Adobe Commerce-software.
1. Herstel de git-vertakking.

Na het uitvoeren van deze stappen:

* de Adobe Commerce-installatie keert terug naar de toestand Vanilla (hersteld database; configuratie van implementatie verwijderd; directory&#39;s onder `var` gewist)
* uw it-vertakking is in het verleden ingesteld op de gewenste status

Lees de gedetailleerde stappen hieronder:

### Stap 0 (Vereiste): Verwijder config.php om het Beheer van de Configuratie onbruikbaar te maken {#disable_config_management}

Wij moeten het Beheer van de Configuratie onbruikbaar maken zodat het niet automatisch de vorige configuratiemontages tijdens plaatsing toepast.

Om configuratiebeheer onbruikbaar te maken, zorg ervoor dat uw `/app/etc/` map bevat niet de `config.php` (voor Adobe Commerce 2.2.x) of `config.local.php` (voor Adobe Commerce 2.1.x).

Ga als volgt te werk om het configuratiebestand te verwijderen:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verwijder het configuratiebestand:
   * Voor Adobe Commerce 2.2:

   ```php
    rm app/etc/config.php
   ```

   * Voor Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Meer informatie over Configuratiebeheer door te controleren:

* [Implementatiedowntime in Adobe Commerce op cloudinfrastructuur verminderen](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze kennisbasis voor ondersteuning.
* [Configuratiebeheer voor opslaginstellingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in onze ontwikkelaarsdocumentatie.

### Stap 1: De Adobe Commerce-software verwijderen met de opdracht Setup:verwijderen {#setup-uninstall}


De Adobe Commerce-software wordt verwijderd en de database wordt hersteld, de implementatieconfiguratie wordt verwijderd en mappen onder `var`.

Controleren [De Adobe Commerce-software verwijderen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in onze ontwikkelaarsdocumentatie.

Voer de volgende stappen uit om de Adobe Commerce-software te verwijderen:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Uitvoeren `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Verwijderen bevestigen.

Het volgende bericht wordt weergegeven om te bevestigen dat het verwijderen is gelukt:

```php
[SUCCESS]: Magento uninstallation complete.
```

Dit betekent dat we onze Adobe Commerce-installatie (inclusief DB) hebben teruggezet naar de authentieke (Vanilla) staat.

### Stap 2: De git-vertakking herstellen {#reset-git-branch}

Met het terugstellen van de it, keren wij de code aan de gewenste staat in het verleden terug.

1. De omgeving klonen naar uw lokale ontwikkelomgeving. U kunt de opdracht kopiëren in de Cloud Console:    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Open de geschiedenis van uw verplichtingen. Gebruiken `--reverse` om geschiedenis in omgekeerde volgorde weer te geven voor meer gemak:

   ```git
     git log --reverse
   ```

1. Selecteer de commit hash waarop u goed bent geweest. Om code aan zijn authentiek staat (Vanilla) terug te stellen, vind zeer eerste begaan die uw tak (milieu) creeerde.    ![Een commit hash selecteren in de git-console](assets/select_commit_hash.png)
1. Voorinstelling voor hard git toepassen:

   ```git
     git reset --h <commit_hash>
   ```

1. Wijzigingen op de server doorvoeren:

   ```git
     git push --force <origin> <branch>
   ```

Na het uitvoeren van deze stappen, wordt onze git tak teruggesteld en de volledige git verandering is duidelijk. De laatste git-push activeert de herimplementatie om alle wijzigingen toe te passen en Adobe Commerce opnieuw te installeren.

## Scenario 2: Geen opname; build verbroken (geen SSH-verbinding) {#scen3}

Deze sectie toont hoe te om een milieu terug te draaien wanneer het in een kritieke staat is: de plaatsingsprocedure kan niet in de bouw van een werkende toepassing slagen, zo makend de verbinding van SSH niet beschikbaar.

In dit scenario moet u eerst de werkstatus van uw Adobe Commerce-toepassing herstellen met behulp van de git-reset en vervolgens de Adobe Commerce-software verwijderen (om de database neer te zetten en te herstellen, de implementatieconfiguratie te verwijderen, enz.). Het scenario impliceert de zelfde stappen zoals in Scenario 1, maar de orde van stappen is verschillend en er is een extra geleidelijke hergroepering. De stappen zijn:

[1. Herstel de git-vertakking.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Configuratiebeheer uitschakelen.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Verwijder de Adobe Commerce-software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;punt; opnieuw inzetten forceren.

Na het uitvoeren van deze stappen, zult u de zelfde resultaten hebben zoals in Scenario 1.

### Stap 4: Opnieuw inzetten forceren

Leg vast (dit zou leeg kunnen zijn begaan, hoewel wij het niet adviseren) en duw het aan de server om redistribueren te teweegbrengen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Als instellen mislukt:verwijderen, database handmatig opnieuw instellen

Indien het `setup:uninstall` De opdracht mislukt met een fout en kan niet worden voltooid. Mogelijk wordt de DB handmatig met de volgende stappen gewist:

1. [SSH voor uw omgeving](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verbinding maken met de MySQL-database:

   ```sql
   mysql -h database.internal
   ```

1. Zet de `main` DB:

   ```sql
   drop database main;
   ```

1. Een leeg bestand maken `main` DB:

   ```sql
   create database main;
   ```

1. Verwijder de volgende configuratiebestanden: `config.php`, `config.php` `.bak`, `env.php`, en `env.php.bak`.

Nadat u de database opnieuw hebt ingesteld, [een git-push naar de omgeving uitvoeren om herimplementatie te starten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) en installeer Adobe Commerce in een nieuwe database. of [Voer de opdracht Opnieuw implementeren uit](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [Een momentopname herstellen op Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Een opname maken](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Momentopnamen en back-upbeheer](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Vertakkingen beheren met de Cloud Console - Logboeken weergeven](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Implementatiefout component](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Uw project beheren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
