---
title: Back-upproblemen
description: Dit artikel bevat een overzicht van de mogelijke oplossingen voor problemen met het maken van back-ups.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Back-upproblemen

Dit artikel bevat een overzicht van de mogelijke oplossingen voor problemen met het maken van back-ups.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.x
* Magento Open Source 2.3.x

## Back-up uitgeschakeld {#backup-disabled}

Als de Adobe Commerce-back-upfunctie niet wordt gestart of het volgende bericht wordt weergegeven, moet u deze functie inschakelen voordat u een back-up maakt.

```terminal
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Ga het volgende CLI bevel in:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Voor meer informatie over back-ups raadpleegt u [Maak een back-up van het bestandssysteem, de media en de database en rol deze terug.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Onvoldoende schijfruimte {#insufficient-disk-space-trouble-backup-space-}

Als de reservekopie is mislukt als gevolg van onvoldoende schijfruimte, moet u doorgaans schijfruimte vrijmaken door sommige bestanden naar een ander opslagapparaat of station te verplaatsen. Er kunnen echter andere manieren zijn om dit probleem op te lossen. Zie een van de volgende bronnen voor tips:

* [8 tips voor het oplossen van problemen met Linux- en Unix-systemen op de vaste schijf, zoals de schijf vol of kan niet naar de schijf schrijven](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfout: df zegt dat de schijf vol is, maar niet](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: Waar is de schijfruimte gebleven voor Linux?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Fout besturingssysteem {#operating-system-error-trouble-backup-os-}

Helaas, kunnen wij om het even wat specifiek wegens de verscheidenheid van fouten niet adviseren u zou kunnen ontmoeten. Wij kunnen u echter voorstellen:

* Neem contact op met de systeembeheerder.
* Openbare forums zoeken zoals [Stapeluitwisseling](https://unix.stackexchange.com) of [Stapeloverloop](https://stackoverflow.com)
* Een [GitHub-probleem](https://github.com/magento/magento2/issues) en we zullen proberen te helpen .

## Back-up mislukt {#backup-fails-trouble-backup-all-}

Als de back-up mislukt of als alle back-uptests mislukken, is het mogelijk dat de [Adobe Commerce-eigenaar bestandssysteem](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) heeft onvoldoende rechten en eigendom van het Adobe Commerce-bestandssysteem. Een andere gebruiker kan bijvoorbeeld eigenaar zijn van de bestanden of de bestanden kunnen alleen-lezen zijn.

Let vooral op de rechten van het bestandssysteem en de eigendom van de `<magento_root>/var` directory en subdirectory&#39;s. Zie voor meer informatie [Machtigingen en eigendom van bestandssysteem instellen](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
