---
title: Kan de nieuwste Beta-versie niet openen
description: Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste Beta-versies van code voor Adobe Commerce te gebruiken. De Beta-code is alleen beschikbaar voor officiële Adobe partners die het proces hebben gevolgd dat is beschreven in [Adobe Commerce Beta Program] (https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Kan de nieuwste Beta-versie niet openen

Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste Beta-versies van code voor Adobe Commerce te gebruiken. De code van Beta is slechts beschikbaar voor officiële Adobe partners die het proces hebben gevolgd dat in [&#x200B; wordt beschreven het Programma van Beta van Adobe Commerce &#x200B;](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Probleem

In dit artikel worden de volgende kwesties behandeld met betrekking tot de toegang tot de code voor vroege toegang:

* De versie van Adobe Commerce Beta is niet beschikbaar voor download onder **Mijn Rekening** > **Downloads** op [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login).
* Het ontbreken om de vroege versie van toegangsAdobe Commerce van [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) te downloaden gebruikend Composer.

## Oorzaak

Dit zijn de meest voorkomende oorzaken van problemen:

* U zoekt naar de code voor vroege toegang op de verkeerde locatie.
* U gebruikt de onjuiste MageID.
* De ontwikkelaar heeft toegangstoetsen van correcte MageID nodig.
* Je account maakt geen deel uit van het Beta-programma.

## Oplossing

### Locatie van code voor vroege toegang

Tijdens bètatoegangsperioden, zijn de versiepakketten slechts beschikbaar via Composer op [&#x200B; repo.magento.com &#x200B;](https://repo.magento.com/). De pakketten van de versie zijn niet beschikbaar op portals GitHub en Adobe Commerce tijdens deze periode, en wij zullen hen aan deze plaatsen op de datum GA publiceren. Voor meer details op hoe te om Composer te gebruiken, gelieve [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer) te klikken.

### MageID die u moet gebruiken

U moet primaire MageID gebruiken verbonden aan uw rekening van de Partner. Het Beta-programma is niet gekoppeld aan een contactpersoon die gedeelde toegang heeft. De vroege toegang kan slechts via Composer of [&#x200B; repo.magento.com &#x200B;](https://repo.magento.com/) door MageID worden betreden verbonden aan uw vergunning van de Partner.

#### Hoe kom ik erachter of mijn MageID primaire is

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Logboek in [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) en gaat naar **Mijn Product en de Diensten** tabel. In de sub-sectie van Partners, controleer of ziet u de actieve de vergunningsinformatie van de Partner:
   * Als u de actieve de vergunningsinformatie van de Partner ziet, dan is uw MageID primair. De licentie van de Partner is actief als de waarde DATE van het EIND een datum in de toekomst is.
   * Als u niet de actieve de vergunningsinformatie van de Partner ziet, dan heeft uw MageID slechts gedeelde toegang. Om te weten te komen wie de primaire identiteitskaart houder is, ga naar **Gedeeld met me** Bericht SHARENAME die daar wordt gespecificeerd. Klik **de Rekeningen van de Schakelaar** en selecteer de waarde u in SHARENAME hebt genoteerd. Op de welkomstpagina ziet u de e-mail van de houder van de primaire id.
1. Als om het even welke reden u deze informatie over [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) niet kunt vinden, gelieve uw Manager van de Partner te contacteren.
1. Als niets van de bovengenoemde werken, gelieve [&#x200B; contactSteun &#x200B;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Ontwikkelaar heeft geen juiste toegang tot toetsen

Als u de primaire eigenaar van MageID bent en toegang moet geven tot een ontwikkelaar in uw team, voert u de volgende stappen uit:

1. Heb de primaire eigenaar MageID login in [&#x200B; account.magento.com &#x200B;](https://account.magento.com/customer/account/login).
1. Selecteer het **lusje van de Marketplace van 0&rbrace; &lbrace;en klik dan** Sleutels van de Toegang **.**
1. Selecteer **creeer een Nieuwe sleutel van de Toegang** en noem het.
1. Verzend de sleutels naar uw ontwikkelaar.

### Geen onderdeel van het programma voor vroege toegang

Ons Beta Access-programma is alleen beschikbaar voor onze Oplossing en Technische Partners, zodat zij onze preproductiecode kunnen evalueren. Om in het programma van de Toegang van Beta te worden omvat, moet uw organisatie een actieve rekening van de Partner van de Adobe hebben die in goed staat is en de NDA van Beta [&#x200B; hier &#x200B;](https://github.com/magento/magento2/wiki/Magento-Beta-Program) heeft ondertekend. Als u gelooft u aan deze criteria voldoet en niet tot de bètacode toegang hebt, gelieve [&#x200B; commercebeta@adobe.com &#x200B;](mailto:commercebeta@adobe.com) te contacteren.
