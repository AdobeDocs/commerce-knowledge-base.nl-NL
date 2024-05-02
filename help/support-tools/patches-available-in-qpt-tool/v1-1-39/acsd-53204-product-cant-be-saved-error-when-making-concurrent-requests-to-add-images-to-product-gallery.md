---
title: 'ACSD-53204: *Het product kan niet worden opgeslagen* fout bij gelijktijdige aanvragen om afbeeldingen toe te voegen aan galerie'
description: Pas de ACSD-53204-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de fout *Het product kan niet worden opgeslagen* wordt gegenereerd bij gelijktijdige aanvragen om afbeeldingen aan de productgalerie toe te voegen met de rest/V1/products/&lt;sku&gt;/media-eindpunt.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204: &quot;*Het product kan niet worden opgeslagen*&quot; fout bij gelijktijdige aanvragen om afbeeldingen toe te voegen aan galerie

De ACSD-53204-patch verhelpt het probleem waarbij &quot;*Het product kan niet worden opgeslagen* Er treedt een fout op wanneer u tegelijkertijd aanvragen indient om afbeeldingen aan de productgalerie toe te voegen met de `rest/V1/products/<sku>/media` eindpunt. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.39 is geïnstalleerd. De patch-id is ACSD-53204. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

&quot;*Het product kan niet worden opgeslagen* Er treedt een fout op wanneer u tegelijkertijd aanvragen indient om afbeeldingen aan de productgalerie toe te voegen met de `rest/V1/products/<sku>/media` eindpunt.

<u>Stappen om te reproduceren</u>:

1. Meld u aan bij het deelvenster Beheer.
1. Maak een product met SKU p1.
1. Meerdere aanvragen tegelijk indienen bij de `rest/V1/products/<sku>/media` eindpunt om meerdere afbeeldingen tegelijk te uploaden.

<u>Verwachte resultaten</u>:

De afbeeldingen worden zonder fouten opgeslagen.

<u>Werkelijke resultaten</u>:

&quot;*Het product kan niet worden opgeslagen*&quot; fout wordt van tijd tot tijd geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
