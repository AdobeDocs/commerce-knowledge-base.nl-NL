---
title: '[!DNL FedEx] de migratie van de de verzendingsmethode integratie van SOAP aan RESTful API'
promoted: true
description: Pas een flard toe om de  [!DNL FedEx]  verschepende migratie van de methodeintegratie van SOAP aan RESTful API voor Adobe Commerce 2.4.4-p4 - 2.4.6-pX te behandelen.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] migratie van SOAP naar RESTful-API voor verzendmethoden

Dit artikel bevat een patch voor het oplossen van problemen met de integratiemigratie van SOAP naar RESTful-API voor Adobe Commerce 2.4.4-p4 - 2.4.6-pX voor de verzendmethode. [!DNL FedEx]

[!DNL FedEx Web Services] tracking, Address Validation en Validate Postal Codes Web Services Definition Languages (WSDLS) worden op 15 mei 2024 afgesloten. Het SOAP [!DNL FedEx Web Services] bevindt zich in ontwikkelingsbeperking en is vervangen door [!DNL FedEx] RESTFUL API&#39;s. Raadpleeg [[!DNL FedEx Web Services] ](https://www.fedex.com/en-us/developer/web-services.html) voor meer informatie.

Deze wijziging is van invloed op onze huidige implementatie van de [!DNL FedEx] -verzendmethode in Adobe Commerce. Hiervoor is het nodig dat we onze huidige implementatie herstellen en overstappen van verouderde SOAP API&#39;s naar de nieuwste [!DNL FedEx] RESTFUL API&#39;s.

Vanaf 15 mei 2024 kunnen Adobe Commerce-klanten onze huidige integratie met de verzendmethode [!DNL FedEx] niet gebruiken. Adobe geeft deze hotfix dus uit, waarmee Adobe Commerce 2.4.4+-klanten de nieuwste [!DNL FedEx] RESTFUL API&#39;s kunnen gebruiken in plaats van de vervangen SOAP.


## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur en op locatie, en Magento Open Source:

* 2.4.4-p4
* 2.4.5.
* 2.4.5-pX
* 2.4.6.
* 2.4.6-pX

## Oorzaak

De [!DNL FedEx] heeft hun op SOAP gebaseerde API&#39;s vervangen door de RESTful-API&#39;s. Zie [[!DNL FedEx Web Services] ](https://www.fedex.com/en-us/developer/web-services.html).

## Oplossing

Gebruik de volgende bijgevoegde patches, afhankelijk van uw Adobe Commerce/Magento Open Source-versie:

Als u het probleem wilt verhelpen in de 2.4.4+-, 2.4.5+- en 2.4.6+-versies, moet u de bijbehorende patch toepassen op de onderstaande versie van Adobe Commerce/Magento Open Source.

## Reparatie

Gebruik de volgende bijgevoegde patches, afhankelijk van uw Adobe Commerce/Magento Open Source-versie:

### Voor versies 2.4.4-p4:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Voor versies 2.4.5, 2.4.5-pX:

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Voor versies 2.4.6, 2.4.6-pX:


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Hoe de pleister aanbrengen

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze basis van steunkennis voor instructies wordt verstrekt.

## Hoe te om te bepalen of de pleisters zijn aangebracht

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatenteerd, zou u kunnen willen controleren of de flard met succes is toegepast. Dit gebruikt (Voorbeeld: *AC-9363*) als flard om te controleren.

<u> u kunt dit doen door de volgende stappen te nemen </u>:

1. [ installeer  [!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Voer de opdracht uit:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. U zou output gelijkend op dit moeten zien, waar AC-9363 de *Toegepaste* status terugkeert:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
