---
title: '''[!DNL FedEx] Migratie van SOAP naar RESTful API voor de integratie van verzendmethoden'
promoted: true
description: Pas een patch toe om de [!DNL FedEx] migratie van SOAP naar RESTful API voor de integratie van verzendmethoden voor Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] Migratie van SOAP naar RESTful-API voor de integratie van verzendmethoden

Dit artikel bevat een patch voor het oplossen van problemen met de [!DNL FedEx] migratie van SOAP naar RESTful API voor de integratie van verzendmethoden voor Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] het volgen, de Bevestiging van het Adres, en bevestigt de Talen van de Definitie van de Diensten van het Web van Postcodes (WSDLS) zullen op 15 mei 2024 worden gepensioneerd. Gebaseerd op SOAP [!DNL FedEx Web Services] is in ontwikkelingsinsluiting en is vervangen door [!DNL FedEx] RESTFUL API&#39;s. Raadpleeg voor meer informatie [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Deze wijziging is van invloed op onze huidige [!DNL FedEx] implementatie van de integratie van verzendmethoden in Adobe Commerce. Hiervoor moeten we onze huidige implementatie herstellen en migreren van verouderde SOAP API&#39;s naar de nieuwste [!DNL FedEx] RESTFUL API&#39;s.

Vanaf 15 mei 2024 kunnen Adobe Commerce-klanten onze huidige [!DNL FedEx] integratie van verzendmethoden, dus Adobe geeft deze hotfix uit waarmee klanten van Adobe Commerce 2.4.4+ de nieuwste [!DNL FedEx] RESTFUL-API&#39;s in plaats van de vervangen SOAP-API&#39;s.


## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur en op locatie, en Magento Open Source:

* 2.4.4-p4
* 2.4.5.
* 2.4.5-pX
* 2.4.6.
* 2.4.6-pX

## Oorzaak

De [!DNL FedEx] vervangen door de RESTful-API&#39;s. Zie [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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

Pak het bestand uit en zie [Hoe een door Adobe geleverde componentpleister aanbrengen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) in onze kennisbasis voor ondersteuning voor instructies.

## Hoe te om te bepalen of de pleisters zijn aangebracht

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatenteerd, zou u kunnen willen controleren of de flard met succes is toegepast. Dit gebruikt (voorbeeld: *AC-9363*) als de te controleren pleister.

<u>U kunt dit doen door de volgende stappen te nemen</u>:

1. [Installeer de [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Voer de opdracht uit:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. U zou output gelijkend op dit moeten zien, waar AC-9363 terugkeert *Toegepast* status:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
