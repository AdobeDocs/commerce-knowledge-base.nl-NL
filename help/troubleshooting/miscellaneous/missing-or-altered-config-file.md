---
title: Ontbrekend of gewijzigd configuratiebestand
description: Los het probleem op met het ontbrekende of gewijzigde configuratiebestand voor Adobe Commerce.
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Ontbrekend of gewijzigd configuratiebestand

In dit artikel wordt beschreven hoe u het probleem kunt oplossen waarbij configuratiebestanden zijn gewijzigd of ontbreken.

## Betrokken producten en versies

* Adobe Commerce op cloud-infrastructuur, alle versies

## Probleem

Configuratiebestanden `config.php` en/of `env.php` zijn onjuist gewijzigd of ontbreken.

## Oplossing

Tijdens het implementatieproces wordt voor elk configuratiebestand een back-upbestand gemaakt:

* `app/etc/config.php.bak` — bevat systeemspecifieke instellingen en wordt tijdens het maken automatisch gegenereerd als dit niet het geval is
* `app/etc/env.php.bak` — bevat gevoelige configuratiegegevens

U kunt ze herstellen met de opdracht ECE-gereedschappen `backup:restore` .

De BAK-bestanden zijn een product van het implementatieproces. Als u na de implementatie handmatig een configuratiebestand wijzigt, worden uw wijzigingen niet doorgevoerd in de bestaande BAK-bestanden.

U kunt als volgt de configuratiebestanden herstellen:

1. Login aan uw verre bewaarplaats gebruikend [ SSH ](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).
1. Maak een lijst met de beschikbare back-upbestanden.

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. Herstel de configuratiebestanden.

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   U ontvangt een lijst met bestaande configuratiebestanden die worden beïnvloed door de terugzetbewerking.

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. Gebruik de optie `--force` om alle bestanden te overschrijven.

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. U kunt desgewenst een specifiek configuratiebestand herstellen.

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
