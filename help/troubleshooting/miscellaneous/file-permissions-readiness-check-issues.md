---
title: Gereedheidscontrole voor bestandsmachtigingen
description: 'Dit artikel bevat een oplossing voor problemen met de gereedheidscontrole voor bestandsmachtigingen. Mappen in het Adobe Commerce-bestandssysteem moeten kunnen worden geschreven door de gebruiker van de webserver en, indien van toepassing, door de eigenaar van het Adobe Commerce-bestandssysteem. Een fout gelijkend op de volgende vertoningen in de Tovenaar van de Opstelling van het Web als uw toestemmingen niet behoorlijk worden geplaatst:'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Gereedheidscontrole voor bestandsmachtigingen

Dit artikel bevat een oplossing voor problemen met de gereedheidscontrole voor bestandsmachtigingen. Mappen in het Adobe Commerce-bestandssysteem moeten kunnen worden geschreven door de gebruiker van de webserver en, indien van toepassing, door de eigenaar van het Adobe Commerce-bestandssysteem. Een fout gelijkend op de volgende vertoningen in de Tovenaar van de Opstelling van het Web als uw toestemmingen niet behoorlijk worden geplaatst:

![&#x200B; install_rc_file-perms.png &#x200B;](assets/install_rc_file-perms.png)

De manier waarop u het probleem verhelpt, hangt af van het feit of u een installatie voor één gebruiker of voor twee gebruikers hebt:

* *Één gebruiker* betekent u login aan de server van Adobe Commerce zoals de zelfde gebruiker die ook de Webserver in werking stelt. Dit type installatie komt veel voor in gedeelde hostomgevingen.
* *Twee gebruikers* betekent u typisch *niet* login als, of schakelaar aan, de gebruiker van de Webserver. Meestal meldt u zich aan als één gebruiker en voert u de webserver uit als een andere gebruiker. Dit is typisch bij privé het ontvangen of als u uw eigen server hebt.

## Resolutie van één gebruiker

Als u opdrachtregeltoegang hebt, voert u de volgende opdracht in, ervan uitgaande dat Adobe Commerce is geïnstalleerd in `/var/www/html/magento2` :

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

Als u geen opdrachtregeltoegang hebt, gebruikt u een FTP-client of een toepassing voor bestandsbeheer die door uw hostingprovider wordt geleverd om machtigingen in te stellen.

## Resolutie van twee gebruikers

Als u desgewenst alle opdrachten op één regel wilt invoeren, voert u het volgende in, ervan uitgaande dat Adobe Commerce is geïnstalleerd in `/var/www/html/magento2` en dat de naam van de webservergroep `apache` is:

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Als de systeemmachtigingen voor het gebeurtenisbestand onjuist zijn ingesteld en niet kunnen worden gewijzigd door de eigenaar van het Adobe Commerce-bestandssysteem, kunt u de opdracht invoeren als een gebruiker met `root` -rechten:

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
