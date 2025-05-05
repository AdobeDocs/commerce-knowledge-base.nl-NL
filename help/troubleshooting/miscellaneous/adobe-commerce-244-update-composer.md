---
title: Problemen met Composer-plug-ins bij de upgrade naar Adobe Commerce 2.4.4
description: Dit artikel biedt een oplossing om het probleem met composer-plug-ins te voorkomen wanneer u een upgrade uitvoert van Adobe Commerce 2.4.3 en eerder naar Adobe Commerce 2.4.4 of hoger (wanneer toekomstige versies worden uitgebracht).
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

<u> Stappen om </u> te reproduceren:

Vereisten: Adobe Commerce 2.4.3 of eerder is geïnstalleerd.

1. Begin de verbetering zoals die in [ wordt beschreven een verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=nl-NL) uitvoeren.
1. Voer de opdracht `composer update` uit om de Adobe Commerce-toepassing bij te werken.

<u> Verwachte resultaten </u>:

Upgrade is voltooid.

<u> Ware resultaten </u>:

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

Na juli 2022 wijzigt Composer de standaardwaarde van de optie [`allow-plugins` ](https://getcomposer.org/doc/06-config.md#allow-plugins) in `{}` en de plug-ins worden alleen geladen als dit is toegestaan.

## Oplossing

Voeg het volgende toe aan uw `composer.json` -bestand, afhankelijk van de manier waarop u Adobe Commerce hebt geïnstalleerd:

* Als het project [ gebruikend het `composer create-project` bevel ](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer#get-the-metapackage) is gecreeerd:

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* Als het project op een andere manier is gemaakt en niet `"dealerdirect/phpcodesniffer-installer"` in `"require-dev"` -sectie heeft:

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

Nadat u het `composer.json` -bestand hebt bijgewerkt, voert u de opdracht `composer update` uit en start u het upgradeproces opnieuw.
