---
title: '''ACSD-56415: Prestaties van [!UICONTROL Partial Price Indexing] vertraagd door "DELETE` query"'
description: Pas de ACSD-56415-patch toe om het Adobe Commerce-probleem op te lossen waarbij de prestaties van de [!UICONTROL Partial Price Indexing] wordt vertraagd toe te schrijven aan een "DELETE"vraag wanneer het gegevensbestand veel gedeeltelijke prijsgegevens aan index heeft.
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415: Prestaties van [!UICONTROL Partial Price Indexing] is vertraagd vanwege `DELETE` query

De ACSD-56415-patch verhelpt het probleem waarbij de prestaties van de [!UICONTROL Partial Price Indexing] is vertraagd door een `DELETE` vraag wanneer het gegevensbestand veel gedeeltelijke index van prijsgegevens heeft. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 is geïnstalleerd. De patch-id is ACSD-56023. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van [!UICONTROL Partial Price Indexing] is vertraagd door een `DELETE` vraag wanneer het gegevensbestand veel gedeeltelijke index van prijsgegevens heeft.

<u>Stappen om te reproduceren</u>:

1. Maken *300000 producten* en *10 websites* met het profiel voor grote prestaties.
1. Meld u aan bij het deelvenster Beheer.
1. Maken *10 klantengroepen*.
1. Voer hieronder vraag uit om producten aan toe te voegen `_cl` tabel:

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Voer het onderstaande bevel uit om het gedeeltelijke prijsindexeringsproces teweeg te brengen:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>Verwachte resultaten</u>:

De SQL-query DELETE `main_table` VAN `catalog_product_index_price` wordt snel uitgevoerd.

<u>Werkelijke resultaten</u>:

De SQL-query DELETE `main_table` VAN `catalog_product_index_price` zeer langzaam wordt uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
