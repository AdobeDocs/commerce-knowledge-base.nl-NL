---
title: '''B2B-2674: Voegt caching vermogen aan de customAttributeMetadata GraphQL query'' toe'
description: Pas het B2B-2674 flard toe om caching vermogen aan de customAttributeMetadata GraphQL vraag toe te voegen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: Voegt caching vermogen aan toe `customAttributeMetadata` GraphQL-query

De B2B-2674-patch voegt caching-mogelijkheden toe aan de `customAttributeMetadata` GraphQL query&#39;s. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is B2B-2674. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7-bèta1.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`customAttributeMetadata` GraphQL query is not cacheable.

<u>Vereisten</u>:

* Server wijst naar [!DNL Varnish] proxying naar Adobe Commerce backend.
* Configuratie-instelling `system/full_page_cache/caching_application` is ingesteld op *2* ([!DNL Varnish]), of ga naar Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > en instellen op [!DNL Varnish].

Nadat de patch is toegepast, voert u de volgende stappen uit om ervoor te zorgen dat caching nu mogelijk is:

1. Verzenden `GET` verzoek aan de hierboven vermelde GraphQL-query, met gebruik van willekeurige velden.
1. U kunt het verzoek zonder wijzigingen opnieuw verzenden. Dit verloopt veel sneller. Merk op dat het verzoek niet wordt verzonden naar het achterste deel maar volledig wordt behandeld door [!DNL Varnish] als een cache-hit.
1. Als u meer bewijs nodig hebt, voert u de ongeopende vermelding uit van `X-Magento-Debug` koptekst in onze [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)en start vervolgens opnieuw [!DNL Varnish] en voert u de bovenstaande stappen opnieuw uit.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
