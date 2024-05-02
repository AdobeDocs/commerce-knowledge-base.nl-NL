---
title: Onvoldoende geheugen tijdens installatie of upgrade
description: In dit artikel wordt gesproken over oplossingen voor het probleem van de geheugenfout tijdens het installeren/upgraden van Adobe Commerce op locatie en het Magento Open Sourcen van producten op locatie.
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Onvoldoende geheugen tijdens installatie of upgrade

In dit artikel wordt gesproken over oplossingen voor het probleem van de geheugenfout tijdens het installeren/upgraden van Adobe Commerce op locatie en het Magento Open Sourcen van producten op locatie.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.3.x
* Magento Open Source ter plaatse 2.3.x

## Probleem

Wanneer het installeren van of het bijwerken van Adobe Commerce of de toepassing of de componenten van de Magento Open Source zoals uitbreidingen, thema&#39;s, of taalpakketten, gebruikend de Tovenaar van de Opstelling van het Web, een fout gelijkend op de volgende vertoningen:

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

De fout

```bash
proc_open(): fork failed - Cannot allocate memory
```

kan ook op de opdrachtregel worden weergegeven.

## Oplossing {#solution}

We raden u aan [2 GB geheugen toewijzen aan PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) in onze ontwikkelaarsdocumentatie om ervoor te zorgen uw installatie of verbetering succesvol is.

Als u dat al hebt gedaan, maakt u een wisselbestand op uw computer. Een Linux-computer gebruikt *wisselruimte* als er meer geheugenbronnen nodig zijn en het RAM vol is. De wisselruimte wordt gebruikt voor inactieve pagina&#39;s in het geheugen.

Hieronder vindt u alleen suggesties; mogelijk zijn andere opties beschikbaar. Raadpleeg een netwerkbeheerder of een andere betrouwbare bron voordat u verdergaat. U moet de opdrachten uitvoeren om een wisselbestand te maken als een gebruiker met `root` rechten.

### Bestand wisselen op Ubuntu {#swap-file-on-ubuntu}

Gebruik de `fallocate` bevel zoals die in deze verwijzingen wordt besproken:

* [Hoe wordt omwisselen toegevoegd op Ubuntu 14.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [Hoe voegt u wisselruimte toe op Ubuntu 16.04 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### Bestand wisselen op CentOS {#swap-file-on-centos}

Gebruik de `mkswap` bevel zoals die in deze verwijzingen wordt besproken:

* [Omwisselen toevoegen op CentOS 6 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [Omwisselen toevoegen op CentOS 7 (Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [Ruimte wisselen (RedHat-klantenportal)](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
