---
title: '''BB2B-2598: Voegt caching vermogen toe om Config, currency, country, countries, availableStores GraphQl query''s op te slaan.'''
description: Pas het flard BB2B-2598 toe om caching vermogen aan storeConfig, munt, land, landen, en beschikbareStores GraphQl vragen toe te voegen.
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: Voegt caching capaciteit aan toe `storeConfig`, `currency`, `country`, `countries`, en `availableStores` GraphQl-query&#39;s

De BB2B-2598-patch biedt caching-mogelijkheden voor `storeConfig`, `currency`, `country`, `countries`, en `availableStores` GraphQl-query&#39;s. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is BB2B-2598. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7-bèta1.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`availableStores`, `countries`, `country`, `currency`, `storeConfig`, en `customAttributeMetadata` GraphQL query&#39;s zijn niet cacheable.

<u>Vereisten</u>:

* Server wijst naar [!DNL Varnish] proxying naar Adobe Commerce backend.
* Configuratie-instelling `system/full_page_cache/caching_application` is ingesteld op *2* ([!DNL Varnish]), of ga naar Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > en instellen op [!DNL Varnish].

Nadat de patch is toegepast, voert u de volgende stappen uit om ervoor te zorgen dat caching nu mogelijk is:

1. Verzenden `GET` verzoek aan om het even welke GraphQL vragen hierboven, gebruikend om het even welke willekeurige gebieden.
1. U kunt het verzoek zonder wijzigingen opnieuw verzenden. Dit verloopt veel sneller. Merk op dat het verzoek niet wordt verzonden naar het achterste deel maar volledig wordt behandeld door [!DNL Varnish] als een cache-hit.
1. Als u meer bewijs nodig hebt, voert u de ongeopende vermelding uit van `X-Magento-Debug` koptekst in onze [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227)en start vervolgens opnieuw [!DNL Varnish] en voert u de bovenstaande stappen opnieuw uit.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
