---
title: '[!DNL USPS] Ondersteuning voor hotfix van de verzendmethode voor grondvoordeel voor AC-9182'
promoted: true
description: Pas een flard toe om de  [!DNL USPS]  het verschepen methodekwestie AC-9182 voor Adobe Commerce 2.4.4 - 2.4.6-p2 te behandelen.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Ondersteuning voor hotfix van de verzendmethode voor grondvoordeel voor AC-9182

Dit artikel bevat een patch voor het oplossen van het probleem AC-9182 voor de nieuwe verzendmethode **[!DNL USPS]Ground Advantage** in Adobe Commerce 2.4.4 - 2.4.6-p2.

Op 9 juli 2023, gaf de Dienst van Postal van Verenigde Staten ([!DNL USPS]) een nieuwe het verschepen methode, [[!DNL USPS]  Voordeel van de Gronde ](https://www.usps.com/ship/ground-advantage.htm) vrij.

Deze nieuwe verzendmethode vervangt de drie belangrijkste huidige verzendmethoden:

* [!DNL USPS] Retailbasis
* [!DNL USPS] First-Class Package Service
* [!DNL USPS] Grondvlak voor selecteren van pakket

[[!DNL USPS]  kondigde ](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) aan dat vanaf 30 September, 2023, deze drie verschepende methodes zullen worden beëindigd en alle klanten de nieuwe **[!DNL USPS]methode van het Voordeel van de Gronde** in plaats daarvan moeten gebruiken.

Na 30 september 2023 zullen alle Adobe Commerce-handelaren die de verzendmethode USPS gebruiken, geen verzendkosten meer van [!DNL USPS] kunnen krijgen met deze drie oude verzendmethoden.

Dit probleem wordt opgelost in het bereik van de volgende beveiligingspatchreleases in oktober 2023, in de versies 2.4.6-p3, 2.4.5-p5 en 2.4.4-p6.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur en op locatie, en Magento Open Source:

* 2.4.4.
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5.
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6.
* 2.4.6-p1
* 2.4.6-p2

## Oorzaak

De [!DNL USPS] heeft een [!DNL API] update uitgevoerd.

## Oplossing

U moet de onderstaande AC-9182-patch toepassen om het probleem op te lossen in de versies 2.4.4, 2.4.5 en 2.4.6.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling om deze te downloaden:

[AC-9182_USPS_Ground_Advantage_Shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Hoe de pleister aanbrengen

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Hoe te om te bepalen of de pleisters zijn aangebracht

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatcheerd, zou u kunnen willen controleren of de markering AC-9182 met succes is toegepast.

<u> u kunt dit doen door de volgende stappen te nemen </u>:

1. [ installeer  [!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Voer de opdracht uit:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. U zou output gelijkend op dit moeten zien, waar AC-9182 de *Toegepaste* status terugkeert:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
