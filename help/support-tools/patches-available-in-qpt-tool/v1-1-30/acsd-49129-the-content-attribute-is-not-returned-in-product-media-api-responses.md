---
title: '''ACSD-49129: kenmerk "Content" niet geretourneerd in API-reacties voor productmedia"'
description: Pas de ACSD-49129-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het *content*-kenmerk (*base64 image code*) niet wordt geretourneerd in de reacties van de product media-API van "rest/V1/products/sku/media`.
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: kenmerk &quot;Content&quot; wordt niet geretourneerd in API-reacties voor productmedia

De ACSD-49129-patch verhelpt het probleem waarbij de *content* attribute (*[!UICONTROL base64 image code]*) wordt niet geretourneerd in het dialoogvenster `rest/V1/products/sku/media` API-reacties voor productmedia. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.30 is geïnstalleerd. De patch-id is ACSD-49129. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De *content* attribute (*[!UICONTROL base64 image code]*) wordt niet geretourneerd in het dialoogvenster `rest/V1/products/sku/media` API-reacties voor productmedia.

<u>Stappen om te reproduceren</u>:

1. Maak een product met een afbeelding.
1. Verzenden *GET REST API* verzoek om `rest/V1/products/<sku>/media` en `rest/V1/products/<sku>/media/<entryId>`.
1. Controleer de API-reacties.

<u>Verwachte resultaten</u>

De *content* -kenmerk met de gegevens is beschikbaar via REST API.

<u>Werkelijke resultaten</u>

De *content* Het kenmerk is niet aanwezig in de API-reacties.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
