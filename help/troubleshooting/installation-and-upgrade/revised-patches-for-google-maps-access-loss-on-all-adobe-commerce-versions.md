---
title: Gereviseerde patches voor Google Maps-toegangsverlies op alle Adobe Commerce-versies
description: "Dit artikel verstrekt een moeilijke situatie voor de handelaars van Adobe Commerce die niet compatibel met om het even welke recente  [!DNL Google Maps]  versies van 3.54+ zijn."
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Gereviseerde patches voor toegangsverlies van [!DNL Google Maps] voor alle Adobe Commerce-versies

Dit artikel biedt een oplossing voor Adobe Commerce-handelaren die niet compatibel zijn met recente [!DNL Google Maps] -versies van 3.54+. Met deze oplossing kunt u het probleem oplossen dat Adobe Commerce-verkopers in geen enkele versie van Adobe Commerce meer toegang hebben tot [!DNL Google Maps] .

## Betrokken versies en producten

* Versies van Adobe Commerce en/of andere gebruikte technologieën.
* Adobe Commerce *2.4.4* - *2.4.7* op Cloud en op-Premises versies.

## Probleem

Op *14 Juni, 2024* [!DNL Google Maps] versie *3.53* bereikte het eind van leven en werd uitgezet door [!DNL Google].

Zie [[!DNL Google Maps Platform: Maps JavaScript API] &#x200B;](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions) voor meer informatie.

Adobe Commerce was niet compatibel met recente [!DNL &#x200B; Google Maps] -versies van 3.54+.

De incompatibiliteit werd veroorzaakt door verouderde `prototype.js script` , die via `lib/web/legacy-build.min.js` wordt geladen en native Array.from overschrijft, wat leidt tot een direct conflict met de [!DNL &#x200B; Google Maps] API.

Zie [[!DNL Google Maps: JS Best Practices] &#x200B;](https://developers.google.com/maps/documentation/javascript/best-practices).

<u> Stappen om </u> te reproduceren:

1. Klik op **[!UICONTROL Content]** > **[!UICONTROL Pages]** > en selecteer een **[!UICONTROL New Page]** .
1. Vouw het blok Inhoud uit en klik op de knop Bewerken **[!DNL PageBuilder]** .
1. Sleep het blok Inhoud toewijzen van het menu **[!DNL PageBuilder]** naar de pagina.

<u> Verwacht resultaat:</u>

[!DNL Google Maps] zou moeten werken zoals verwacht.

<u> Werkelijk resultaat: </u>

Als u het blok Kaarten inhoud van het menu **[!DNL PageBuilder]** naar de pagina sleept, verschijnt er een foutbericht zoals *&quot;Sorry! Iets ging fout&quot;* wordt getoond.

## Oplossing

* Alle verkopers op om het even welke 2.4.4, 2.4.5, 2.4.6 of 2.4.7 flardversie zouden deze overeenkomstige flarden op hun versie moeten toepassen.

## Reparatie

Gebruik de volgende bijgevoegde patches, afhankelijk van de Adobe Commerce-versie:

**voor versies 2.4.4:**
[&#x200B; ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip &#x200B;](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**voor versies 2.4.5:**
[&#x200B; ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip &#x200B;](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**voor versies 2.4.6:**
[&#x200B; ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip &#x200B;](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**voor versies 2.4.7:**
[&#x200B; ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip &#x200B;](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**gelieve nota te nemen**

Deze kwestie zal permanent in het werkingsgebied van de veiligheid-enige flardversies van Augustus worden bevestigd:
2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Verwante lezing

[&#x200B; hoe te om een componentenflard toe te passen die door Adobe &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) wordt verstrekt