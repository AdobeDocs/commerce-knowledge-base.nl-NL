---
title: Problemen met gereedheid voor PHP-versie
description: In dit artikel wordt gesproken over de oplossingen voor de PHP-versieproblemen die u kunt tegenkomen bij het installeren/upgraden van Adobe Commerce op locatie met de wizard Webinstellingen.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Problemen met gereedheid voor PHP-versie

In dit artikel wordt gesproken over de oplossingen voor de PHP-versieproblemen die u kunt tegenkomen bij het installeren/upgraden van Adobe Commerce op locatie met de wizard Webinstellingen.

>[!WARNING]
>
>In Adobe Commerce op cloudinfrastructuur kan een upgrade van de service niet naar de productieomgeving worden uitgevoerd zonder dat het infrastructuurteam hiervan 48 kantooruren op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Dus 48 uur voor het moment dat uw veranderingen in productie moeten zijn [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) het gedetailleerd van uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

## Betrokken producten en versies

* Adobe Commerce op locatie 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Niet-ondersteunde PHP-versie

### Probleem

De controle mislukt omdat je een niet-ondersteunde PHP versie gebruikt.

### Oplossing

Om dit probleem op te lossen, gebruikt u een van de ondersteunde versies die in de ontwikkelaarsdocumentatie worden vermeld [2.3.x Systeemvereisten](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) en [2.2.x Systeemvereisten](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## Controle van gereedheid voor PHP wordt niet weergegeven

### Probleem

De PHP gereedheidscontrole geeft de PHP versie niet weer zoals de volgende afbeelding laat zien.
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Oplossing

Dit is een symptoom van een onjuiste installatie van de snijtaak. Zie voor meer informatie [Uitsnijdtaken instellen](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) in onze ontwikkelaarsdocumentatie.

## Onjuiste PHP-versie

### Probleem

De controle rapporteert de onjuiste PHP versie. Doorgaans gebeurt dit alleen voor geavanceerde gebruikers die meerdere PHP-versies hebben geïnstalleerd. In sommige gevallen mislukt de gereedheidscontrole; in andere gevallen kan deze slagen.

Als de PHP-versie die door de gereedheidscontrole wordt gemeld onjuist is, is dit het resultaat van een onjuiste match van PHP versies tussen de PHP CLI en de webserver plug-in. Adobe Commerce vereist dat je *één versie* van PHP voor zowel de CLI (die wordt uitgevoerd als de webserver (waarop Commerce Admin, Component Manager en System Upgrade wordt uitgevoerd).

### Oplossing

We gaan ervan uit dat als je dit probleem hebt, je een ervaren gebruiker bent die waarschijnlijk meerdere versies van PHP op je systeem heeft geïnstalleerd.

Ga als volgt te werk om het probleem op te lossen:

* Start de webserver of php-fm opnieuw.
* Controleer de `$PATH` omgevingsvariabele voor meerdere paden naar PHP.
* Gebruik de `which php` Als dit niet juist is, verwijdert u het of maakt u een symlink naar de juiste PHP versie.
* Een [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) pagina om meer informatie te verzamelen.
* Zorg ervoor dat u een ondersteunde PHP-versie gebruikt volgens onze systeemvereisten, in de documentatie voor ontwikkelaars:
   * [Adobe Commerce 2.3.x-systeemvereisten](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Adobe Commerce 2.2.x-systeemvereisten](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Stel dezelfde PHP-instellingen in voor zowel de PHP opdrachtregel als de PHP webserver plug-in, zoals beschreven in [PHP-configuratieopties](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) in onze ontwikkelaarsdocumentatie.
