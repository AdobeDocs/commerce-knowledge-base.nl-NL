---
title: Adobe Commerce 2.3.6, 2.4.1 CAPTCHA bij afrekenen werkt niet
description: Dit artikel bevat een patch voor het probleem waarbij de CAPTCHA-functie voor afrekenen niet werkt zoals wordt verwacht op de pagina Place Order wanneer betalingsproviders van derden zoals Paypal Express, Payflow Pro of CyberSource in Adobe Commerce worden gebruikt.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 CAPTCHA bij afrekenen werkt niet

Dit artikel bevat een patch voor het probleem waarbij de CAPTCHA-functie voor afrekenen niet werkt zoals wordt verwacht op de pagina Place Order wanneer betalingsproviders van derden zoals Paypal Express, Payflow Pro of CyberSource in Adobe Commerce worden gebruikt.

Dit bekende probleem wordt vermeld in onze documentatie voor ontwikkelaars:

<u>Voor Adobe Commerce 2.3.6</u>:

* [Opmerkingen bij de release van Adobe Commerce 2.3.6: bekende problemen](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Opmerkingen bij de release van Magento Open Source 2.3.6: bekende problemen](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Voor Adobe Commerce 2.4.1</u>:

* [Opmerkingen bij de release van Adobe Commerce 2.4.1: bekende problemen](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Opmerkingen bij de release van Magento Open Source 2.4.1: bekende problemen](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.6 en 2.4.1
* Magento Open Sourcen 2.3.6 en 2.4.1

## Probleem

<u>Stappen om te reproduceren</u>

1. Stel ten minste een van deze betalingsmethoden in Commerce in: Paypal Express, Payflow Pro of CyberSource.
1. Ga naar **Beheer > Opslag > Configuratie > Klanten > Klantenconfiguratie > CAPTCHA** .
   * Set **CAPTCHA inschakelen in de Storefront** = *Ja* .
   * Selecteren in **Forms** : *Afhandeling/Plaatsingsvolgorde* , *Aanmelden* , en *Wachtwoord vergeten* .
   * Set **Weergavemodus** = *Na aantal aanmeldpogingen* (om de **Aantal mislukte aanmeldpogingen** wordt weergegeven).
   * Set **Aantal mislukte aanmeldpogingen** = *0* (om captcha de hele tijd te laten werken).
1. Voeg aan de voorzijde een product toe aan de winkelwagen en probeer het uit te checken.
1. Voer op de pagina Betalingsgegevens Captcha in en probeer het uit te checken met Paypal Express, Payflow Pro of CyberSource.

<u>Verwacht resultaat:</u>

De CAPTCHA-functie functioneert naar behoren.

<u>Werkelijk resultaat:</u>

Het foutbericht wordt weergegeven: *Geef de CAPTCHA-code op en probeer het opnieuw.*

## Oplossing

Pas een van de onderstaande patches toe, afhankelijk van het feit of u zich op Adobe Commerce op locatie/Adobe Commerce op cloudinfrastructuur/Magento Open Source 2.3.6 of 2.4.1 bevindt.

## Patches

De patches zijn gekoppeld aan dit artikel en kunnen in beide versies worden gedownload `.composer` en `.git` indelingen.

Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op een van de volgende koppelingen:

<u>Voor Adobe Commerce on-premiss/Adobe Commerce on cloud infrastructure/Magento Open Source 2.3.6</u> :

* [Composer patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Voor Adobe Commerce on-premiss/Adobe Commerce on cloud infrastructure/Magento Open Source 2.4.1</u> :

* [Composer patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Deze patches zijn niet compatibel met andere Adobe Commerce- of Magento Open Source-versies en -versies.

## Hoe de pleister aanbrengen

<u>Composer-patch</u>

Zie [Hoe een door Adobe geleverde componentpleister aanbrengen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning van composer-patchinstructies.

<u>Git patch</u>

Zie documentatie voor ontwikkelaars [Patches toepassen: aangepaste patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) voor patchinstructies voor Adobe Commerce/Magento Open Source.
