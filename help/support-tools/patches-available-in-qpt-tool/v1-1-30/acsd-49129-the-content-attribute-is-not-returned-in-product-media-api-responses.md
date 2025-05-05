---
title: '''ACSD-49129: kenmerk "Content" niet geretourneerd in API-reacties voor productmedia"'
description: Pas de ACSD-49129-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het *content*-kenmerk (*base64 image code*) niet wordt geretourneerd in de reacties van de product media-API van "rest/V1/products/sku/media&grave;.
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129: kenmerk &quot;Content&quot; wordt niet geretourneerd in API-reacties voor productmedia

Het ACSD-49129 flard bevestigt de kwestie waar het *inhouds* attribuut (*[!UICONTROL base64 image code]*) niet in de `rest/V1/products/sku/media` API van de productmedia reacties is teruggekeerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-49129. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het *inhoud* attribuut (*[!UICONTROL base64 image code]*) is niet teruggekeerd in de `rest/V1/products/sku/media` de media API reacties van het product.

<u> Stappen om </u> te reproduceren:

1. Maak een product met een afbeelding.
1. Verzend *REST API* verzoek aan `rest/V1/products/<sku>/media` en `rest/V1/products/<sku>/media/<entryId>`.
1. Controleer de API-reacties.

<u> Verwachte resultaten </u>

Het *inhouds* attribuut met het gegeven is beschikbaar via REST API.

<u> Ware resultaten </u>

Het *inhoud* attribuut is niet aanwezig in de API reacties.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
