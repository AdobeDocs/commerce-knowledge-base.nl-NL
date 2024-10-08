---
title: Back-upproblemen
description: Dit artikel bevat een overzicht van de mogelijke oplossingen voor problemen met het maken van back-ups.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
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

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Ga het volgende CLI bevel in:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Voor extra informatie over steunen, zie [ file en rol terug het dossiersysteem, media, en gegevensbestand.](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-backup.html)

## Onvoldoende schijfruimte {#insufficient-disk-space-trouble-backup-space-}

Als de reservekopie is mislukt als gevolg van onvoldoende schijfruimte, moet u doorgaans schijfruimte vrijmaken door sommige bestanden naar een ander opslagapparaat of station te verplaatsen. Er kunnen echter andere manieren zijn om dit probleem op te lossen. Zie een van de volgende bronnen voor tips:

* [ 8 Uiteinden om de Problemen van de Schijf van Linux &amp; van Unix van Systemen zoals volledige Schijf op te lossen of kan niet aan de Schijf ](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk) schrijven
* [ serverfout: df zegt schijf volledig is, maar het is niet ](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [ unix.stackexchange.com: Het volgen neer waar de schijfruimte op Linux is gegaan?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Fout besturingssysteem {#operating-system-error-trouble-backup-os-}

Helaas, kunnen wij om het even wat specifiek wegens de verscheidenheid van fouten niet adviseren u zou kunnen ontmoeten. Wij kunnen u echter voorstellen:

* Neem contact op met de systeembeheerder.
* De openbare forums van het onderzoek zoals [ Uitwisseling van het Stapel ](https://unix.stackexchange.com) of [ Overloop van de Stapel ](https://stackoverflow.com)
* Open a [ GitHub kwestie ](https://github.com/magento/magento2/issues) en wij zullen proberen om te helpen.

## Back-up mislukt {#backup-fails-trouble-backup-all-}

Als de steun ontbreekt of als alle reservetests ontbreken, is het mogelijk de [ eigenaar van het het dossiersysteem van Adobe Commerce ](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/file-sys-perms-over.html) heeft niet voldoende voorrechten en eigendom van het het dossiersysteem van Adobe Commerce. Een andere gebruiker kan bijvoorbeeld eigenaar zijn van de bestanden of de bestanden kunnen alleen-lezen zijn.

Let met name op de machtigingen voor het bestandssysteem en de eigendom van de map `<magento_root>/var` en submappen. Voor meer informatie, zie [ plaats de toestemmingen en de eigendom van het dossiersysteem ](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-system-perms.html).
