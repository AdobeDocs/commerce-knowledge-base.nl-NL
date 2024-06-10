---
title: '[!DNL UPS] integratiemigratie van verzendmethoden [!DNL SOAP] tot [!DNL RESTful API]'
promoted: true
description: Pas een patch toe om de [!DNL UPS] integratiemigratie van verzendmethoden [!DNL SOAP] tot [!DNL RESTful API] voor Adobe Commerce 2.4.4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] integratiemigratie van verzendmethoden [!DNL SOAP] tot [!DNL RESTful API]

>[!NOTE]
>
>Als u een van de drie patches van dit artikel hebt geüpload voordat u **6 juni 2024**: Als u deze kwestie wegens [!DNL Metric System/SI] meetwaarden (kilo&#39;s en centimeters) die niet worden gebruikt, moet u een van deze nieuwe, bijgewerkte patches die nu in dit artikel zijn gepubliceerd opnieuw toepassen voor uw versie van Adobe Commerce/Magento Open Source van 2.4.4+/2.4.5+/2.4.6+, omdat u anders de [!DNL Metric System/SI] metingen van **kilogram** en **centimeter** in de [!DNL UPS] verzendmethoden in het dialoogvenster **[!DNL Admin configuration]**. Deze nieuwe patches zijn compatibel met de eerder vrijgegeven patches. Dit probleem wordt permanent opgelost in het bereik van de komende Adobe Commerce versie 2.4.7-p1-release die gepland is voor **11 juni 2024**.

>[!NOTE]
>
>Als u een van de drie patches van dit artikel hebt geüpload voordat u **10 oktober 2023** dient u een van deze patches die nu in dit artikel is gepubliceerd opnieuw toe te passen voor uw 2.4.4+/2.4.5+/2.4.6+-versie van Adobe Commerce/Magento Open Source, omdat u anders geen specifieke patches kunt selecteren en configureren [!DNL UPS] verzendmethoden in het dialoogvenster **[!DNL Admin configuration]** en u zult ze allemaal moeten inschakelen. Deze nieuwe patches zijn compatibel met de eerder vrijgegeven patches.

Dit artikel bevat een patch voor het oplossen van problemen met de [!DNL United Parcel Service (UPS)] integratiemigratie van verzendmethoden [!DNL SOAP] tot [!DNL RESTful API] voor Adobe Commerce 2.4.4 - 2.4.6-pX.

Volgens de meest recente actualiseringen van de [!DNL UPS API] Beveiligingsmodel, [!DNL UPS] heeft een [!DNL OAuth 2.0] beveiligingsmodel voor iedereen [!DNL APIs] (Meer informatie vindt u in het dialoogvenster [[!DNL UPS] Beheerdersportaal Toegang Key-migratiehandleiding](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) de algemene veiligheid te verbeteren om fraude te verminderen en te zorgen voor een betere [!DNL API] mogelijkheden.

Deze wijziging is van invloed op onze huidige [!DNL UPS] implementatie van de integratie van de verzendmethode in Adobe Commerce en vereist dat we onze huidige implementatie herstellen en migreren van [!DNL SOAP API] aan de [!DNL RESTful API] om steun te kunnen verlenen [!DNL OAuth 2.0] verificatieprotocollen.

**Begin in juni 2024**, Adobe Commerce-handelaren zullen niet kunnen communiceren met onze huidige [!DNL UPS] integratie, dus geven wij deze hotfix vrij, die Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ verkopers toestaat om naar recentste te migreren [!DNL UPS REST APIs].

Dit probleem wordt opgelost in Adobe Commerce/Magento Open Source versie 2.4.7 en de oplossing wordt ook opgenomen in de 2.4.7-bèta2-release in oktober 2023.

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur en op locatie, en Magento Open Source:

* 2.4.4.
* 2.4.4-pX
* 2.4.5.
* 2.4.5-pX
* 2.4.6.
* 2.4.6-pX

## Oorzaken

De [!DNL UPS] vrijgegeven [beveiligingsupdate voor hun [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Als u een Europese Unie hebt (andere oorsprong kan hetzelfde probleem ervaren) als de herkomst van de verzending, zal dit een fout veroorzaken in de [!DNL UPS REST] request: &quot;*Een zending mag geen KGS/IN, LBS/CM of OZS/CM hebben als maateenheid.*&quot;

## Oplossing

Gebruik de volgende bijgevoegde patches, afhankelijk van uw Adobe Commerce/Magento Open Source-versie:

Als u het probleem wilt verhelpen in de 2.4.4+-, 2.4.5+- en 2.4.6+-versies, moet u de bijbehorende patch toepassen op de onderstaande versie van Adobe Commerce/Magento Open Source.

## Reparatie

Gebruik de volgende bijgevoegde patches, afhankelijk van uw Adobe Commerce/Magento Open Source-versie:

### Voor versies 2.4.4, 2.4.4-pX:

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### Voor versies 2.4.5, 2.4.5-pX:

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### Voor versies 2.4.6, 2.4.6-pX:

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

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
