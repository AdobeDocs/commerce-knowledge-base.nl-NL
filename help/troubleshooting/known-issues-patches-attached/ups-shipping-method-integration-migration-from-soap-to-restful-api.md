---
title: '[!DNL UPS] het verschepen migratie van de methodeintegratie van  [!DNL SOAP]  aan  [!DNL RESTful API]'
promoted: true
description: Pas een flard toe om de  [!DNL UPS]  verschepende migratie van de methodeintegratie van  [!DNL SOAP]  aan  [!DNL RESTful API]  voor Adobe Commerce 2.4.4 - 2.4.6-pX te behandelen.
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS] Integratie van verzendmethoden migreren van [!DNL SOAP] naar [!DNL RESTful API]

>[!NOTE]
>
>Als u om het even welke drie flarden van dit artikel vóór **Juni 6, 2024** uploadde: Als u deze kwestie wegens [!DNL Metric System/SI] metingen (kilo en centimeters) wegens niet die wordt gebruikt onder ogen ziet, zou u één van deze nieuwe, bijgewerkte flarden opnieuw moeten toepassen die nu in dit artikel voor uw 2.4.4+/2.4.5+ versie van Adobe Commerce/2.4.6+ worden gepubliceerd Magento Open Source opnieuw, omdat anders u niet de [!DNL Metric System/SI] metingen van **kilo** en **centimeters** in [!DNL UPS] het verschepen methodes in **[!DNL Admin configuration]** kunt selecteren. Deze nieuwe patches zijn compatibel met de eerder vrijgegeven patches. Deze kwestie zal permanent in werkingsgebied van aanstaande versie van Adobe Commerce 2.4.7-p1 gepland voor **Juni 11, 2024** worden bevestigd.

>[!NOTE]
>
>Als u om het even welke drie die flarden van dit artikel vóór **10 Oktober, 2023** uploadde, zou u één van deze flarden opnieuw moeten toepassen nu in dit artikel voor uw 2.4.4+/2.4.5+/2.4.6+ versie van Adobe Commerce/Magento Open Source wordt gepubliceerd, omdat anders u niet specifieke [!DNL UPS] het verschepen methodes in &lbrace;3 kunt selecteren en vormen en u moet ze allemaal inschakelen. **[!DNL Admin configuration]** Deze nieuwe patches zijn compatibel met de eerder vrijgegeven patches.

Dit artikel bevat een patch voor het oplossen van problemen met de integratiemigratie van [!DNL SOAP] naar [!DNL RESTful API] voor Adobe Commerce 2.4.4 - 2.4.6-pX naar de verzendmethode.[!DNL United Parcel Service (UPS)]

Volgens de recentste updates aan het [!DNL UPS API] Model van de Veiligheid, [!DNL UPS] heeft een [!DNL OAuth 2.0] veiligheidsmodel voor allen [!DNL APIs] (Meer details beschikbaar in de [[!DNL UPS]  Belangrijkste Gids van de Migratie van de Toegang van het Portaal van de Ontwikkelaar ](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)) uitgevoerd om de algemene veiligheid te verbeteren om fraude te verminderen en verbeterde [!DNL API] mogelijkheden te verstrekken.

Deze wijziging is van invloed op de huidige implementatie van de [!DNL UPS] -verzendmethode in Adobe Commerce. Hiervoor moeten we onze huidige implementatie herstellen en migreren van [!DNL SOAP API] naar [!DNL RESTful API] voor ondersteuning van [!DNL OAuth 2.0] -verificatieprotocollen.

**Beginnend in Juni 2024**, zullen de handelaars van Adobe Commerce niet met onze huidige [!DNL UPS] integratie kunnen in wisselwerking staan, zodat geven wij deze hotfix vrij, die Adobe Commerce 2.4.4+/2.4.5+/2.4.6+ handelaren om aan recentste [!DNL UPS REST APIs] toestaat te migreren.

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

[!DNL UPS] vrijgegeven a [ veiligheidsupdate voor hun  [!DNL API] ](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

Als u de Europese Unie hebt (andere oorsprong kan hetzelfde probleem ondervinden) als de oorsprong van de verzending, veroorzaakt dit een fout in de aanvraag van [!DNL UPS REST] :
&quot;*de lading van A kan geen KGS/IN of LBS/CM of OZS/CM als eenheid van metingen hebben.*&quot;

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

Pak het dossier uit en zie [ hoe te om een componentenflard toe te passen die door Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=nl-NL) in onze basis van steunkennis voor instructies wordt verstrekt.

## Hoe te om te bepalen of de pleisters zijn aangebracht

Aangezien het niet mogelijk is om gemakkelijk te controleren of de kwestie werd gepatenteerd, zou u kunnen willen controleren of de flard met succes is toegepast. Dit gebruikt (Voorbeeld: *AC-9363*) als flard om te controleren.

<u> u kunt dit doen door de volgende stappen te nemen </u>:

1. [ installeer  [!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL).
1. Voer de opdracht uit:

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. U zou output gelijkend op dit moeten zien, waar AC-9363 de *Toegepaste* status terugkeert:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
