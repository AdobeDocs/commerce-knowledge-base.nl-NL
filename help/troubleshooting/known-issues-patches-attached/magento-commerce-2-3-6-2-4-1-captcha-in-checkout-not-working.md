---
title: Adobe Commerce 2.3.6, 2.4.1 CAPTCHA bij afrekenen werkt niet
description: Dit artikel bevat een patch voor het probleem waarbij de CAPTCHA-functie voor afrekenen niet werkt zoals wordt verwacht op de pagina Place Order wanneer betalingsproviders van derden zoals Paypal Express, Payflow Pro of CyberSource in Adobe Commerce worden gebruikt.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 CAPTCHA bij afrekenen werkt niet

Dit artikel bevat een patch voor het probleem waarbij de CAPTCHA-functie voor afrekenen niet werkt zoals wordt verwacht op de pagina Place Order wanneer betalingsproviders van derden zoals Paypal Express, Payflow Pro of CyberSource in Adobe Commerce worden gebruikt.

Dit bekende probleem wordt vermeld in onze documentatie voor ontwikkelaars:

<u> voor Adobe Commerce 2.3.6 </u>:

* [ Adobe Commerce 2.3.6 de Nota&#39;s van de Versie: Bekende Kwesties ](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/commerce-2-3-6.html)
* [ Magento Open Source 2.3.6 de Nota&#39;s van de Versie: Bekende Kwesties ](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u> voor Adobe Commerce 2.4.1 </u>:

* [ Adobe Commerce 2.4.1 de Nota&#39;s van de Versie: Bekende Kwesties ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-1#known-issues)
* [ Magento Open Source 2.4.1 de Nota&#39;s van de Versie: Bekende Kwesties ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-1#known-issues)

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden) 2.3.6 en 2.4.1
* Magento Open Sourcen 2.3.6 en 2.4.1

## Probleem

<u> Stappen om te reproduceren </u>

1. Stel ten minste een van deze betalingsmethoden in Commerce in: Paypal Express, Payflow Pro of CyberSource.
1. Ga naar **Admin > Opslag > Configuratie > Klanten > de Configuratie van de Klant > CAPTCHA**.
   * Plaats **laat CAPTCHA op Storefront** toe = *ja*.
   * Selecteer in **Forms**: *Controle/Plaatsende Orde*, *Login*, en *vergeten wachtwoord*.
   * Plaats **Weergavemodus** = *Na aantal pogingen om* (om het **Aantal Onsuccesvolle Pogingen aan Login** te maken verschijnen het plaatsen) in te loggen.
   * Plaats **Aantal Onsuccesvolle Pogingen aan Login** = *0* (om het werk van captcha alle tijd te maken).
1. Voeg aan de voorzijde een product toe aan de winkelwagen en probeer het uit te checken.
1. Voer op de pagina Betalingsgegevens Captcha in en probeer het uit te checken met Paypal Express, Payflow Pro of CyberSource.

<u> Verwacht resultaat:</u>

De CAPTCHA-functie functioneert naar behoren.

<u> Ware resultaat:</u>

De vertoningen van het foutenbericht: *gelieve te verstrekken code CAPTCHA en opnieuw te proberen.*

## Oplossing

Pas een van de onderstaande patches toe, afhankelijk van het feit of u zich op Adobe Commerce op locatie/Adobe Commerce op cloudinfrastructuur/Magento Open Source 2.3.6 of 2.4.1 bevindt.

## Patches

De patches zijn gekoppeld aan dit artikel en kunnen in zowel `.composer` - als `.git` -indeling worden gedownload.

Als u een patch wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op een van de volgende koppelingen:

<u> voor Adobe Commerce op-gebouw/Adobe Commerce op wolkeninfrastructuur/Magento Open Source 2.3.6 </u>:

* [Composer patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u> voor Adobe Commerce op-gebouw/Adobe Commerce op wolkeninfrastructuur/Magento Open Source 2.4.1 </u>:

* [Composer patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git patch MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Deze patches zijn niet compatibel met andere Adobe Commerce- of Magento Open Source-versies en -versies.

## Hoe de pleister aanbrengen

<u> Composer flard </u>

Zie [ hoe te om een componentenflard toe te passen die door Adobe ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze basis van steunkennis voor composer flardinstructies wordt verstrekt.

<u> het flardtje van de Git </u>

Zie ontwikkelaarsdocumentatie [ Toepassend flarden: De flarden van de Douane ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches) voor flardinstructies van de it voor Adobe Commerce/Magento Open Source.
