---
title: '[!DNL USPS] Ondersteuning voor hotfix van de Ground Advantage-verzendmethode voor AC-9182'
promoted: true
description: Pas een patch toe om de [!DNL USPS] Uitgave van de grondvoordeel-verzendmethode AC-9182 voor Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Ondersteuning voor hotfix van de verzendmethode voor grondvoordeel voor AC-9182

Dit artikel bevat een patch voor het nieuwe probleem AC-9182. **[!DNL USPS]Grondvoordeel** verzendmethode in Adobe Commerce 2.4.4 - 2.4.6-p2.

Op 9 juli 2023 heeft de US Postal Service ([!DNL USPS]) een nieuwe verzendmethode heeft uitgebracht, [[!DNL USPS] Grondvoordeel](https://www.usps.com/ship/ground-advantage.htm).

Deze nieuwe verzendmethode vervangt de drie belangrijkste huidige verzendmethoden:

* [!DNL USPS] Detailhandel
* [!DNL USPS] First-Class Package Service
* [!DNL USPS] Bovengrond selecteren

[[!DNL USPS] aangekondigd](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) dat deze drie verzendmethoden vanaf 30 september 2023 worden stopgezet en dat alle klanten de nieuwe **[!DNL USPS]Grondvoordeel** in plaats daarvan.

Na 30 september 2023 kunnen dus niet alle Adobe Commerce-handelaren die de verzendmethode van USPS gebruiken, verzendkosten krijgen van [!DNL USPS] door deze drie oude verzendmethoden nog te gebruiken.

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

De [!DNL USPS] een [!DNL API] bijwerken.

## Oplossing

U moet de onderstaande AC-9182-patch toepassen om het probleem op te lossen in de versies 2.4.4, 2.4.5 en 2.4.6.

## Reparatie

De patch is aan dit artikel gekoppeld. Klik op de volgende koppeling om deze te downloaden:

[AC-9182_USPS_Ground_Advantage_Shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Hoe de pleister aanbrengen

Pak het bestand uit en zie [Hoe een door Adobe geleverde componentpleister aanbrengen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze kennisbasis voor ondersteuning voor instructies.

## Hoe te om te bepalen of de pleisters zijn aangebracht

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatcheerd, zou u kunnen willen controleren of de markering AC-9182 met succes is toegepast.

<u>U kunt dit doen door de volgende stappen te nemen</u>:

1. [Installeer de [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Voer de opdracht uit:

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. U zou output gelijkend op dit moeten zien, waar AC-9182 terugkeert *Toegepast* status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
