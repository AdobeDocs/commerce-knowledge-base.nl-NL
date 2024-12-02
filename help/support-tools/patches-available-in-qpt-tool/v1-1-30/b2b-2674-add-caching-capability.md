---
title: 'B2B-2674: voegt caching vermogen aan de customAttributeMetadata GraphQL vraag toe'
description: Pas het B2B-2674 flard toe om caching vermogen aan de customAttributeMetadata GraphQL vraag toe te voegen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: a4efb268-f811-41f2-a788-a8cfc3016f61
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# B2B-2674: voegt caching-mogelijkheden toe aan de `customAttributeMetadata` GraphQL-query

De B2B-2674-patch voegt caching-mogelijkheden toe aan de `customAttributeMetadata` GraphQL-query&#39;s. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is B2B-2674. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7-bèta1.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`customAttributeMetadata` GraphQL-query is niet cacheable.

<u> Eerste vereisten </u>:

* Server wijst naar [!DNL Varnish] proxying naar Adobe Commerce backend.
* Config het plaatsen `system/full_page_cache/caching_application` wordt geplaatst aan *2* ([!DNL Varnish]), of ga naar Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > en plaats het aan [!DNL Varnish].

Nadat de patch is toegepast, voert u de volgende stappen uit om ervoor te zorgen dat caching nu mogelijk is:

1. Verzend `GET` -aanvraag naar de hierboven vermelde GraphQL-query met willekeurige velden.
1. U kunt het verzoek zonder wijzigingen opnieuw verzenden. Dit verloopt veel sneller. Merk op dat het verzoek niet naar de achterkant wordt verzonden maar volledig door [!DNL Varnish] als geheim voorgeheugenklap wordt behandeld.
1. Als het verdere bewijs wordt vereist, commentaren uit unset van `X-Magento-Debug` kopbal huidig in onze [ VCL ](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239), dan nieuw begin [!DNL Varnish] en stel opnieuw de bovengenoemde stappen in werking.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
