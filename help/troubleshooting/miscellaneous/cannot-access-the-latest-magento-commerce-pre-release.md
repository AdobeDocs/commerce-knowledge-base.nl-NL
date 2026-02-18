---
title: Kan de nieuwste Adobe Commerce-pre-release niet openen
description: Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste pre-releasecode van Adobe Commerce te gebruiken.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Kan de nieuwste Adobe Commerce-pre-release niet openen

Dit artikel biedt oplossingen voor problemen wanneer u probeert de nieuwste pre-releasecode van Adobe Commerce te gebruiken.

>[!NOTE]
>
>Als u problemen met de toegang van Beta hebt verwijs naar [&#x200B; niet tot het recentste versie van Beta &#x200B;](/help/how-to/general/cannot-access-the-latest-beta-version.md) artikel toegang heeft.

## Probleem

In dit artikel worden de volgende problemen besproken met de toegang tot de pre-releasecode:

* U kunt de pre-releasecode niet vinden.
* Het ontbreken om de vroege versie van toegangsAdobe Commerce van [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) te downloaden gebruikend Composer.

## Oorzaak

Dit zijn de meest voorkomende oorzaken van problemen:

* U zoekt naar de code voor vroege toegang op de verkeerde locatie.
* U gebruikt onjuiste MageID wanneer het toegang tot van de code via Composer.
* Uw account maakt geen deel uit van het programma Pre-release.

## Oplossing

### Locatie van code voor vroege toegang

Tijdens de release zijn de releasepakketten beschikbaar op twee locaties:

1. Via Composer op [&#x200B; magento.com &#x200B;](https://repo.magento.com/) gebruikend primaire MageID voor de rekening. Voor meer details op hoe te om Composer te gebruiken, gelieve te verwijzen naar [&#x200B; installeer Adobe Commerce gebruikend Composer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/composer) in onze ontwikkelaarsdocumentatie.
1. **Mijn Rekening** > **Downloads** op [&#x200B; account.magento.com &#x200B;](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>De pakketten van de versie zijn niet beschikbaar op GitHub tot de datum GA.

### MageID die u moet gebruiken

U moet de primaire MageID gebruiken verbonden aan uw Adobe Commerce of rekening van de Partner. Het pre-releaseprogramma is niet gekoppeld aan een contactpersoon die gedeelde toegang heeft. De vroege toegang kan slechts via Composer of [&#x200B; repo.magento.com &#x200B;](https://repo.magento.com/) door MageID worden betreden verbonden aan uw vergunning van Adobe Commerce of Partner.

#### Hoe kom ik erachter of mijn MageID de primaire is?

**voor handelaren**

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Logboek in [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) en gaat naar **Mijn Product en de Diensten** tabel. Controleer of je de Adobe Commerce-licentiegegevens hier ziet:
   * Als u de Adobe Commerce-licentiegegevens ziet, is uw MageID primair.
   * Als u de Adobe Commerce-licentiegegevens niet ziet, heeft uw MageID alleen gedeelde toegang. Om te weten te komen wie de primaire identiteitskaart houder is, ga naar **Gedeeld met me** Bericht SHARENAME die daar wordt gespecificeerd. Klik **de Rekeningen van de Schakelaar** en selecteer de waarde u in SHARENAME hebt genoteerd. Op de welkomstpagina ziet u het e-mailbericht van de houder van de primaire id.
1. Als om het even welke reden u deze informatie over [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) niet kunt vinden, gelieve uw Team van de Rekening van Adobe te contacteren.
1. Als niets van de bovengenoemde werken, gelieve [&#x200B; contactSteun &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).

**voor partners**

Ga als volgt te werk om te weten te komen of uw MageID primair is:

1. Logboek in [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) en gaat naar **Mijn Product en de Diensten** tabel. In de sub-sectie van Partners, controleer of ziet u de actieve de vergunningsinformatie van de Partner:
   * Als u de actieve de vergunningsinformatie van de Partner ziet, dan is uw MageID primair. De licentie van de Partner is actief als de waarde DATE van het EIND een datum in de toekomst is.
   * Als u niet de actieve de vergunningsinformatie van de Partner ziet, dan heeft uw MageID slechts gedeelde toegang. Om te weten te komen wie de primaire identiteitskaart houder is, ga naar **Gedeeld met me** Bericht SHARENAME die daar wordt gespecificeerd. Klik **de Rekeningen van de Schakelaar** en selecteer de waarde u in SHARENAME hebt genoteerd. Op de welkomstpagina ziet u het e-mailbericht van de houder van de primaire id.
1. Als om het even welke reden u deze informatie over [&#x200B; magento.com &#x200B;](https://account.magento.com/customer/account/login) niet kunt vinden, gelieve uw Manager van de Partner te contacteren.
1. Als geen van bovenstaande werken, gelieve [&#x200B; с Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) contacteren.

### Geen onderdeel van het pre-releaseprogramma

Om in het programma van de Toegang van de pre-versie te worden omvat, moet uw organisatie een actieve rekening van Adobe Commerce of van de Partner hebben die in goed staat is. Als u gelooft u aan deze criteria voldoet en niet tot de pre-versiecode toegang hebt, gelieve [&#x200B; de Steun van het contact &#x200B;](https://experienceleague.adobe.com/nl/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) met uw MageID.
