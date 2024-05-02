---
title: 'ACSD-53347: Prijsindexerende prestaties verminderen de overuren geleidelijk.'
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

De ACSD-53347-patch verhelpt het probleem dat de prestaties geleidelijk afnemen wanneer de prijzen voor een grote productcatalogus opnieuw worden berekend. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38 is geïnstalleerd. De patch-id is ACSD-53347. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het opnieuw indexeren van prijzen voor een grote productcatalogus nemen de prestaties van de vragen die tijdens het indexeringsproces worden uitgevoerd geleidelijk af.

<u>Stappen om te reproduceren</u>:

1. Maak een grote eenvoudige catalogus en wijs aangepaste opties toe aan deze producten (aangepaste opties gebruiken een tijdelijke tabel tijdens het indexeren).
1. Maak minstens 200 of meer klantengroepen om de zichtbaarheid van de uitgave te vergroten.
1. Maak tien of meer websites en wijs alle producten aan elk van deze websites toe.
1. Merk op dat de ingevoerde producten bijna identiek zijn, die slechts door SKU en naam verschillen.
1. Inschakelen **[!UICONTROL DB Logging]**.
1. Voer de `bin/magento index:reindex catalog_product_price` gebruiken.
1. Controleren op *DELETE VAN`catalog_product_index_price_opt_agr_temp`* in de `db.log`.

<u>Verwachte resultaten</u>:

De uitvoering van de *DB-query&#39;s* efficiënt wordt uitgevoerd.

<u>Werkelijke resultaten</u>:

De prestaties van de *DB-query&#39;s* op tijdelijke tabellen wordt de overuren traag , zodat de indexering van de prijzen veel tijd in beslag neemt .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
