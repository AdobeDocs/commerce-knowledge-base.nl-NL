---
title: Problemen met Composer-plug-ins bij de upgrade naar Adobe Commerce 2.4.4
description: Dit artikel biedt een oplossing om het probleem met composer-plug-ins te voorkomen wanneer u een upgrade uitvoert van Adobe Commerce 2.4.3 en eerder naar Adobe Commerce 2.4.4 of hoger (wanneer toekomstige versies worden uitgebracht).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Problemen met Composer-plug-ins bij de upgrade naar Adobe Commerce 2.4.4

Dit artikel biedt een oplossing om problemen met composer-plug-ins te voorkomen wanneer u een upgrade uitvoert van Adobe Commerce 2.4.3 en eerder naar Adobe Commerce 2.4.4 of hoger (wanneer toekomstige versies worden uitgebracht).

## Betrokken producten en versies

* Adobe Commerce op locatie, elke versie bij het bijwerken naar 2.4.4 of hoger (indien vrijgegeven)
* Adobe Commerce op cloudinfrastructuur, elke versie bij het bijwerken naar versie 2.4.4 of hoger (indien vrijgegeven)
* Magento Open Source, elke versie bij het bijwerken naar versie 2.4.4 of hoger (wanneer deze wordt vrijgegeven)

## Probleem

Wanneer u na juli 2022 een update naar Adobe Commerce 2.4.4 of hoger uitvoert, wordt mogelijk een waarschuwing van de componist over plug-ins weergegeven.

<u>Stappen om te reproduceren</u>:

Vereisten: Adobe Commerce 2.4.3 of eerder is geïnstalleerd.

1. De upgrade starten zoals wordt beschreven in [Een upgrade uitvoeren](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. Voer de `composer update` gebruiken om de Adobe Commerce-toepassing bij te werken.

<u>Verwachte resultaten</u>:

Upgrade is voltooid.

<u>Werkelijke resultaten</u>:

Installatie mislukt met een fout die lijkt op het volgende:

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Oorzaak

Na juli 2022 wijzigt Composer de standaardwaarde van de component [`allow-plugins` option](https://getcomposer.org/doc/06-config.md#allow-plugins) tot `{}` en plug-ins worden alleen geladen als dit is toegestaan.

## Oplossing

Voeg het volgende toe aan uw `composer.json` -bestand, afhankelijk van de manier waarop u Adobe Commerce hebt geïnstalleerd:

* Als het project is gemaakt [met de `composer create-project` command](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage):

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Als het project op een andere manier is gemaakt en niet `"dealerdirect/phpcodesniffer-installer"` in `"require-dev"` sectie:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Na het bijwerken van de `composer.json` bestand, voer het `composer update` en start het upgradeproces opnieuw.
