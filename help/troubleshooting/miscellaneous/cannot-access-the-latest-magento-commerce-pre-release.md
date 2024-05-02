---
title: Kan de nieuwste Adobe Commerce-pre-release niet openen
description: Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste pre-releasecode van Adobe Commerce te gebruiken.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Kan de nieuwste Adobe Commerce-pre-release niet openen

Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste pre-releasecode van Adobe Commerce te gebruiken.

>[!NOTE]
>
>Als u problemen hebt met bètatoegang, raadpleegt u de [Kan de nieuwste bètaversie niet openen](/help/how-to/general/cannot-access-the-latest-beta-version.md) artikel.

## Probleem

In dit artikel worden de volgende problemen besproken met de toegang tot de pre-releasecode:

* U kunt de pre-releasecode niet vinden.
* Kan Adobe Commerce-versie voor vroege toegang niet downloaden van [magento.com](https://account.magento.com/customer/account/login) gebruiken van Composer.

## Oorzaak

Dit zijn de meest voorkomende oorzaken van problemen:

* U zoekt naar de code voor vroege toegang op de verkeerde locatie.
* U gebruikt onjuiste MageID wanneer het toegang tot van de code via Composer.
* Uw account maakt geen deel uit van het programma Pre-release.

## Oplossing

### Locatie van code voor vroege toegang

Tijdens de release zijn de releasepakketten beschikbaar op twee locaties:

1. Via Composer op [magento.com](https://repo.magento.com/) het gebruik van de primaire MageID voor de account. Voor meer informatie over het gebruik van Composer raadpleegt u [Adobe Commerce installeren met Composer](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) in onze ontwikkelaarsdocumentatie.
1. **Mijn account** > **Downloads** op [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>De pakketten van de versie zijn niet beschikbaar op GitHub tot de datum GA.

### MageID die u moet gebruiken

U moet de primaire MageID gebruiken verbonden aan uw Adobe Commerce of rekening van de Partner. Het pre-releaseprogramma is niet gekoppeld aan een contactpersoon die gedeelde toegang heeft. Vroege toegang is alleen toegankelijk via Composer of [repo.magento.com](https://repo.magento.com/) door de MageID die is gekoppeld aan uw Adobe Commerce-licentie of Partner-licentie.

#### Hoe kom ik erachter of mijn MageID de primaire is?

**Voor handelaren**

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Aanmelden [magento.com](https://account.magento.com/customer/account/login) en ga naar de **Mijn product en services** tab. Controleer of je de Adobe Commerce-licentiegegevens hier ziet:
   * Als u de Adobe Commerce-licentiegegevens ziet, is uw MageID primair.
   * Als u de Adobe Commerce-licentiegegevens niet ziet, heeft uw MageID alleen gedeelde toegang. Als u wilt weten wie de primaire id-houder is, gaat u naar de **Gedeeld met mij** Let op de SHARENAME die daar is opgegeven. Klikken **Wisselen tussen accounts** en selecteer de waarde die u hebt genoteerd in SHARENAME. Op de welkomstpagina ziet u het e-mailbericht van de houder van de primaire id.
1. Als u deze informatie om welke reden dan ook niet kunt vinden op [magento.com](https://account.magento.com/customer/account/login), neem contact op met het accountteam van de Adobe.
1. Als geen van bovenstaande punten werkt, gelieve [contactondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Voor partners**

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Aanmelden [magento.com](https://account.magento.com/customer/account/login) en ga naar de **Mijn product en services** tab. In de sub-sectie van Partners, controleer of ziet u de actieve de vergunningsinformatie van de Partner:
   * Als u de actieve de vergunningsinformatie van de Partner ziet, dan is uw MageID primair. De licentie van de Partner is actief als de waarde DATE van het EIND een datum in de toekomst is.
   * Als u niet de actieve de vergunningsinformatie van de Partner ziet, dan heeft uw MageID slechts gedeelde toegang. Als u wilt weten wie de primaire id-houder is, gaat u naar de **Gedeeld met mij** Let op de SHARENAME die daar is opgegeven. Klikken **Wisselen tussen accounts** en selecteer de waarde die u hebt genoteerd in SHARENAME. Op de welkomstpagina ziet u het e-mailbericht van de houder van de primaire id.
1. Als u deze informatie om welke reden dan ook niet kunt vinden op [magento.com](https://account.magento.com/customer/account/login), gelieve uw Manager van de Partner te contacteren.
1. Als geen van bovenstaande punten werkt, gelieve [с contactondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Geen onderdeel van het pre-releaseprogramma

Om in het programma van de Toegang van de pre-versie te worden omvat, moet uw organisatie een actieve rekening van Adobe Commerce of van de Partner hebben die in goed staat is. Als u van mening bent dat u aan deze criteria voldoet en geen toegang hebt tot de pre-releasecode, gelieve [contactondersteuning](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) met uw MageID.
