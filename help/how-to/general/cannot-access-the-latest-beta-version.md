---
title: Kan de nieuwste bètaversie niet openen
description: Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste bètaversies van code voor Adobe Commerce te gebruiken. De bètacode is alleen beschikbaar voor officiële Adobe partners die het proces hebben gevolgd dat is beschreven in [Adobe Commerce Beta Program] (https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Kan de nieuwste bètaversie niet openen

Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste bètaversies van code voor Adobe Commerce te gebruiken. Bètcode is alleen beschikbaar voor officiële Adobe-partners die het in [Adobe Commerce Beta-programma](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Probleem

In dit artikel worden de volgende kwesties behandeld met betrekking tot de toegang tot de code voor vroege toegang:

* Adobe Commerce Beta-versie is niet beschikbaar voor downloaden onder **Mijn account** > **Downloads** op [magento.com](https://account.magento.com/customer/account/login).
* Kan Adobe Commerce-versie voor vroege toegang niet downloaden van [magento.com](https://account.magento.com/customer/account/login) gebruiken van Composer.

## Oorzaak

Dit zijn de meest voorkomende oorzaken van problemen:

* U zoekt naar de code voor vroege toegang op de verkeerde locatie.
* U gebruikt de onjuiste MageID.
* De ontwikkelaar heeft toegangstoetsen van correcte MageID nodig.
* Uw account maakt geen deel uit van het bètaprogramma.

## Oplossing

### Locatie van code voor vroege toegang

Tijdens toegangsperioden voor bèta zijn releasepakketten alleen beschikbaar via Composer op [repo.magento.com](https://repo.magento.com/). De pakketten van de versie zijn niet beschikbaar op portals GitHub en Adobe Commerce tijdens deze periode, en wij zullen hen aan deze plaatsen op de datum GA publiceren. Voor meer informatie over het gebruik van Composer klikt u op [hier](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### MageID die u moet gebruiken

U moet primaire MageID gebruiken verbonden aan uw rekening van de Partner. Het bètaprogramma is niet gekoppeld aan een contactpersoon met gedeelde toegang. Vroege toegang is alleen toegankelijk via Composer of [repo.magento.com](https://repo.magento.com/) door MageID verbonden aan uw vergunning van de Partner.

#### Hoe kom ik erachter of mijn MageID primaire is

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Aanmelden [magento.com](https://account.magento.com/customer/account/login) en ga naar de **Mijn product en services** tab. In de sub-sectie van Partners, controleer of ziet u de actieve de vergunningsinformatie van de Partner:
   * Als u de actieve de vergunningsinformatie van de Partner ziet, dan is uw MageID primair. De licentie van de Partner is actief als de waarde DATE van het EIND een datum in de toekomst is.
   * Als u niet de actieve de vergunningsinformatie van de Partner ziet, dan heeft uw MageID slechts gedeelde toegang. Als u wilt weten wie de primaire id-houder is, gaat u naar de **Gedeeld met mij** Let op de SHARENAME die daar is opgegeven. Klikken **Wisselen tussen accounts** en selecteer de waarde die u hebt genoteerd in SHARENAME. Op de welkomstpagina ziet u de e-mail van de houder van de primaire id.
1. Als u deze informatie om welke reden dan ook niet kunt vinden op [magento.com](https://account.magento.com/customer/account/login), gelieve uw Manager van de Partner te contacteren.
1. Als geen van bovenstaande punten werkt, gelieve [contactondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Ontwikkelaar heeft geen juiste toegang tot toetsen

Als u de primaire eigenaar van MageID bent en toegang moet geven tot een ontwikkelaar in uw team, voert u de volgende stappen uit:

1. De primaire MageID-eigenaar aanmelden bij [account.magento.com](https://account.magento.com/customer/account/login).
1. Selecteer de **Marketplace** en klik vervolgens op **Toegangssleutels**.
1. Selecteren **Een nieuwe toegangstoets maken** en noem deze.
1. Verzend de sleutels naar uw ontwikkelaar.

### Geen onderdeel van het programma voor vroege toegang

Ons BetaAccess-programma is alleen beschikbaar voor onze Oplossing en technische partners, zodat deze onze preproductiecode kunnen evalueren. Om in het programma van de Toegang van Beta te omvatten, moet uw organisatie een actieve rekening van de Partner van de Adobe hebben die in goed staat is en Beta NDA heeft ondertekend [hier](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Als u van mening bent dat u aan deze criteria voldoet en geen toegang hebt tot de bètacode, neemt u contact op met [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
