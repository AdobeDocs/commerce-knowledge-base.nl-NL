---
title: "ACSD-53098: Producten in de gedeelde catalogus weerspiegelen zich niet op frontend"
description: Pas de ACSD-53098-patch toe om het Adobe Commerce-probleem op te lossen waarbij producten die aan een gedeelde catalogus zijn toegewezen, niet op de voorgrond worden weerspiegeld bij het uitvoeren van een gedeeltelijke index.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 19c66a3a-04b2-48ee-aff3-ad2b592ff876
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-53098: Producten in gedeelde catalogus weerspiegelen zich niet op frontend

De ACSD-53098-patch verhelpt het probleem dat producten die zijn toegewezen aan een gedeelde catalogus niet op de voorgrond worden weerspiegeld wanneer een gedeeltelijke index wordt uitgevoerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-53098. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Producten die via API aan een gedeelde catalogus zijn toegewezen, worden niet op de voorkant weergegeven nadat de gedeeltelijke indexeerfunctie de uitsnijdtaak heeft uitgevoerd, gevolgd door de uitsnede voor de consument.

<u> Stappen om </u> te reproduceren:

1. Stel [!DNL RabbitMQ] in als de service in de wachtrij.
1. Schakel indexen over naar de modus **[!UICONTROL Update on Schedule]** .
1. Maak een gedeelde catalogus en wijs deze toe aan een bedrijf.
1. Maak een eenvoudig product en wijs het toe aan een categorie. De gedeeltelijke redex uitvoeren:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Gebruik de volgende API-aanvraag om het gemaakte product toe te wijzen aan de gedeelde catalogus.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Voer de volgende uitsnede uit om de rijen te wissen en voer de gedeeltelijke herdex uit:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Meld u aan bij de frontend als gebruiker van het bedrijf.
1. Controleer de voorste categoriepagina.

<u> Verwachte resultaten </u>:

De nieuw toegewezen producten verschijnen op de voorzijde.

<u> Ware resultaten </u>:

De nieuw toegewezen producten verschijnen niet op voorzijde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
