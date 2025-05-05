---
title: Omgeving terugdraaien zonder Cloud-opname
description: Dit artikel bevat twee oplossingen om een omgeving terug te draaien zonder een momentopname van uw omgeving op Adobe Commerce op cloudinfrastructuur.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Omgeving terugdraaien zonder Cloud-opname

Dit artikel bevat twee oplossingen om een omgeving terug te draaien zonder een momentopname van uw omgeving op Adobe Commerce op cloudinfrastructuur.

## Betrokken producten en versies

* Adobe Commerce op wolkeninfrastructuur, [ alle gesteunde versies ](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Kies de meest geschikte optie voor uw kwestie:

* Als u een stabiele bouwstijl hebt, maar geen geldige momentopname - [ Scenario 1: Geen momentopname, bouwt stabiel (de verbinding van SSH beschikbaar) ](#scen2).
* Als de bouwstijl gebroken is en u geen geldige momentopname hebt - [ Scenario 2: Geen momentopname; bouwt gebroken (geen verbinding SSH) ](#scen3).

## Scenario 1: Geen momentopname, bouwstijl stabiel (beschikbare verbinding SSH) {#scen2}

Deze sectie toont hoe te om een milieu terug te draaien wanneer u geen momentopname hebt gecreeerd maar tot het milieu via SSH kan toegang hebben.

De stappen zijn:

1. Configuratiebeheer uitschakelen.
1. Verwijder de Adobe Commerce-software.
1. Herstel de git-vertakking.

Na het uitvoeren van deze stappen:

* keert uw Adobe Commerce-installatie terug naar de toestand Vanilla (database hersteld; configuratie van implementatie verwijderd; mappen onder `var` gewist)
* uw it-vertakking is in het verleden ingesteld op de gewenste status

Lees de gedetailleerde stappen hieronder:

### Stap 0 (Vereiste): Verwijder config.php om het Beheer van de Configuratie onbruikbaar te maken {#disable_config_management}

Wij moeten het Beheer van de Configuratie onbruikbaar maken zodat het niet automatisch de vorige configuratiemontages tijdens plaatsing toepast.

Als u Configuration Management wilt uitschakelen, moet u ervoor zorgen dat de map `/app/etc/` geen `config.php` -bestanden (voor Adobe Commerce 2.4.x) of `config.local.php` -bestanden (voor Adobe Commerce 2.1.x) bevat.

Ga als volgt te werk om het configuratiebestand te verwijderen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verwijder het configuratiebestand:
   * Voor Adobe Commerce 2.4:

   ```php
    rm app/etc/config.php
   ```

   * Voor Adobe Commerce 2.1:

   ```php
     rm app/etc/config.local.php
   ```

Meer informatie over Configuratiebeheer door te controleren:

* [ vermindert plaatsingsonderbreking op Adobe Commerce op wolkeninfrastructuur ](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) in onze basis van steunkennis.
* [ het beheer van de Configuratie voor opslagmontages ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) in onze ontwikkelaarsdocumentatie.

### Stap 1: De Adobe Commerce-software verwijderen met de opdracht Setup:verwijderen {#setup-uninstall}


Als u de Adobe Commerce-software verwijdert, wordt de database neergezet en hersteld, wordt de implementatieconfiguratie verwijderd en worden mappen onder `var` gewist.

Het overzicht [ desinstalleert de software van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) in onze ontwikkelaarsdocumentatie.

Voer de volgende stappen uit om de Adobe Commerce-software te verwijderen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Uitvoeren `setup:uninstall` :

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

1. De omgeving klonen naar uw lokale ontwikkelomgeving. U kunt de opdracht kopiëren in de Cloud Console:    ![ copy_git_clone.png ](assets/copy_git_clone.png)
1. Open de geschiedenis van uw verplichtingen. Gebruik `--reverse` om de historie in omgekeerde volgorde weer te geven voor meer gemak:

   ```git
     git log --reverse
   ```

1. Selecteer de commit hash waarop u goed bent geweest. Om code aan zijn authentiek staat (Vanilla) terug te stellen, vind zeer eerste begaan die uw tak (milieu) creeerde.    ![ Selecterend begaan hash in git console ](assets/select_commit_hash.png)
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

[ 2. Schakel Configuratiebeheer uit.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Verwijder de Adobe Commerce-software.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&punt; Opnieuw distribueren forceren.

Na het uitvoeren van deze stappen, zult u de zelfde resultaten hebben zoals in Scenario 1.

### Stap 4: Opnieuw inzetten forceren

Leg vast (dit zou leeg kunnen zijn begaan, hoewel wij het niet adviseren) en duw het aan de server om redistribueren te teweegbrengen:

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Als instellen mislukt:verwijderen, database handmatig opnieuw instellen

Als het uitvoeren van de opdracht `setup:uninstall` mislukt met een fout en niet kan worden voltooid, wordt de DB mogelijk handmatig gewist met de volgende stappen:

1. [ SSH aan uw milieu ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Verbinding maken met de MySQL-database:

   ```sql
   mysql -h database.internal
   ```

1. Zet de `main` DB neer:

   ```sql
   drop database main;
   ```

1. Een lege `main` DB maken:

   ```sql
   create database main;
   ```

1. Verwijder de volgende configuratiebestanden: `config.php`, `config.php` `.bak` , `env.php` en `env.php.bak` .

Na het terugstellen van OB, [ maak een git duw aan het milieu om opnieuw op te stellen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) en Adobe Commerce aan nieuw gecreeerd OB te installeren. Of [ stel het redistribueren bevel ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands) in werking.

## Gerelateerde lezing

In onze documentatie voor ontwikkelaars:

* [ herstel een momentopname op Wolk ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [ creeer een momentopname ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [ Momentopnamen en reservebeheer ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [ beheer takken met de Console van de Wolk - de logboeken van de Mening ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [ de mislukte plaatsing van de Component ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [ beheer uw project ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
