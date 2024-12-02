---
title: 'ACSD-56886: configureerbaar product is niet meer beschikbaar als onderliggende producten zijn uitgeschakeld'
description: Pas de ACSD-56886-patch toe om het Adobe Commerce-probleem op te lossen waarbij het configureerbare product uit voorraad komt te zitten wanneer de producten worden uitgeschakeld.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: configureerbaar product is niet meer beschikbaar als onderliggende producten zijn uitgeschakeld

De ACSD-56886-patch verhelpt het probleem waarbij het configureerbare product uit voorraad raakt als onderliggende producten worden uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56886. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product wordt uit voorraad wanneer de kindproducten worden onbruikbaar gemaakt.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Stel alle indexen in de modus **[!UICONTROL Update By Schedule]** in.
1. Maak het volgende configureerbare product:

   * Naam = *CONFIGURABLE 1 VAN DE TEST*
   * Attribuut = *kleur*
   * Waarden = *rood* en *zwart*
   * Prijs van het **rode** kindproduct = *$100*;
   * Prijs van het &quot;zwarte&quot; onderliggende product = *$200*.

1. Maak de volgende geplande update voor het configureerbare product:

   * Datum van het begin = *3* notulen van nu.
   * Einddatum = *5* notulen na de Datum van het Begin.
   * De Naam van het product = *CONFIGURABLE 1 bewerkte TEST*.
   * Maak het **rode** kindproduct in **Configurable** sectie onbruikbaar.

1. Wacht op de Begindatum.
1. Open de configureerbare productdetails op de Storefront.

<u> Verwachte resultaten </u>:

Het configureerbare product wordt getoond als **in Voorraad** met **zo laag zoals 200** etiket.

<u> Ware resultaten </u>:

Het configureerbare product wordt getoond als **uit Voorraad**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
