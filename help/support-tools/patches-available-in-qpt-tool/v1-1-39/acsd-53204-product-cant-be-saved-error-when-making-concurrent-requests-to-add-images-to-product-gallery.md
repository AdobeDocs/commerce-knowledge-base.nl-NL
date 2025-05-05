---
title: 'ACSD-53204: *Het product kan niet worden opgeslagen* fout bij gelijktijdige aanvragen om afbeeldingen toe te voegen aan galerie'
description: Pas de ACSD-53204-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de fout *Het product kan niet worden opgeslagen* wordt gegenereerd bij gelijktijdige aanvragen om afbeeldingen aan de productgalerie toe te voegen met behulp van het eindpunt rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*het product kan niet*&quot;fout op gezamenlijke verzoeken worden bewaard om beelden aan galerij toe te voegen

ACSD-53204 flardfixes de kwestie waar &quot;*het product niet*&quot;fout kan worden bewaard wordt geworpen wanneer het maken van gezamenlijke verzoeken om beelden aan de productgalerij toe te voegen gebruikend het `rest/V1/products/<sku>/media` eindpunt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-53204. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

&quot;*het product kan niet worden bewaard*&quot;fout wordt geworpen wanneer het maken van gezamenlijke verzoeken om beelden aan de productgalerie toe te voegen gebruikend het `rest/V1/products/<sku>/media` eindpunt.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Beheer.
1. Maak een product met SKU p1.
1. Maak meerdere gelijktijdige aanvragen voor het `rest/V1/products/<sku>/media` -eindpunt om meerdere afbeeldingen tegelijk te uploaden.

<u> Verwachte resultaten </u>:

De afbeeldingen worden zonder fouten opgeslagen.

<u> Ware resultaten </u>:

&quot;*het product kan niet worden bewaard*&quot;fout is teruggekeerd van tijd tot tijd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
