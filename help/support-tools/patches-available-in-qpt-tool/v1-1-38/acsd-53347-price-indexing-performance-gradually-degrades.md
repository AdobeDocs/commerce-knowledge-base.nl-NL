---
title: 'ACSD-53347: Prijsindexprestaties verminderen de overuren geleidelijk'
description: Pas de ACSD-53347-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prestaties geleidelijk afnemen bij het opnieuw indexeren van prijzen voor een grote productcatalogus.
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347: Prijsindexprestaties verminderen de overuren geleidelijk

De ACSD-53347-patch verhelpt het probleem dat de prestaties geleidelijk afnemen wanneer de prijzen voor een grote productcatalogus opnieuw worden berekend. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-53347. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het opnieuw indexeren van prijzen voor een grote productcatalogus nemen de prestaties van de vragen die tijdens het indexeringsproces worden uitgevoerd geleidelijk af.

<u> Stappen om </u> te reproduceren:

1. Maak een grote eenvoudige catalogus en wijs aangepaste opties toe aan deze producten (aangepaste opties gebruiken een tijdelijke tabel tijdens het indexeren).
1. Maak minstens 200 of meer klantengroepen om de zichtbaarheid van de uitgave te vergroten.
1. Maak tien of meer websites en wijs alle producten aan elk van deze websites toe.
1. Merk op dat de ingevoerde producten bijna identiek zijn, die slechts door SKU en naam verschillen.
1. Schakel **[!UICONTROL DB Logging]** in.
1. Voer de opdracht `bin/magento index:reindex catalog_product_price` uit.
1. Controleer *DELETE VAN`catalog_product_index_price_opt_agr_temp`* in `db.log`.

<u> Verwachte resultaten </u>:

De uitvoering van de *vragen van DB* loopt efficiënt.

<u> Ware resultaten </u>:

De prestaties van de *vragen van DB* op tijdelijke lijsten worden langzame overwerk, vandaar de prijs het indexeren lijst neemt veel tijd om te voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
