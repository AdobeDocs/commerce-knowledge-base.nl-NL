---
title: Gereviseerde patches voor Google Maps-toegangsverlies op alle Adobe Commerce-versies
description: 'Dit artikel biedt een oplossing voor Adobe Commerce-handelaren die niet compatibel zijn met recente [!DNL Google Maps] versies van 3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: 49bc0b643c10c6597d6a905935c36251e92b18f9
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Herziene patches voor [!DNL Google Maps] toegangsverlies voor alle Adobe Commerce-versies

Dit artikel biedt een oplossing voor Adobe Commerce-handelaren die niet compatibel zijn met recente [!DNL Google Maps] versies van 3.54+. Met deze oplossing wordt het probleem opgelost dat Adobe Commerce-handelaren geen toegang hebben tot [!DNL Google Maps] in om het even welke versie van Adobe Commerce meer.

## Betrokken versies en producten

* Versies van Adobe Commerce en/of andere gebruikte technologieën.
* Adobe Commerce *2.4.4.* - *2.4.7.* in de cloudinstellingen en de ongebruikte versies.

## Probleem

Aan *14 juni 2024* [!DNL Google Maps] versie *3,53* het einde van de levensduur heeft bereikt en [!DNL Google].

Raadpleeg voor meer informatie [[!DNL Google Maps] Platform: hiermee kunt u JavaScript API [https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions] toewijzen.

Adobe Commerce is niet compatibel met recente [!DNL  Google Maps] versies van 3.54+.

De incompatibiliteit werd veroorzaakt door verouderde `prototype.js script`, die door `lib/web/legacy-build.min.js` negeert native Array.from functie, wat leidt tot een direct conflict met [!DNL  Google Maps] API.

Zie [[!DNL Google Maps: JS Best Practices]] (https://developers.google.com/maps/documentation/javascript/best-practices).

<u>Stappen om te reproduceren</u> :

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Pages]** > en klik op een **[!UICONTROL New Page]**.
1. Vouw het blok Inhoud uit en klik op Bewerken **[!DNL PageBuilder]** knop.
1. Sleep het blok met kaartinhoud vanuit het deelvenster **[!DNL PageBuilder]** aan pagina.

<u>Verwacht resultaat:</u>

[!DNL Google Maps] zou moeten werken zoals verwacht.

<u> Werkelijk resultaat:</u>

Bij het neerzetten van het blok Inhoud toewijzen uit **[!DNL PageBuilder]** aan de pagina, een foutbericht zoals *&quot;Sorry! Er is iets fout gegaan&quot;* wordt weergegeven.

## Oplossing

* Alle verkopers op om het even welke 2.4.4, 2.4.5, 2.4.6 of 2.2.7 flardversie zouden deze overeenkomstige flarden op hun versie moeten toepassen.

## Reparatie

Gebruik de volgende bijgevoegde patches, afhankelijk van de Adobe Commerce-versie:

**Voor versies 2.4.4:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Voor versies 2.4.5:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Voor versies 2.4.6:**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**Voor versies 2.4.7:**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**Let op**

Dit probleem wordt permanent vastgelegd in het bereik van alleen-beveiligingspatchreleases van augustus: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10

## Verwante lezing

[Hoe een door Adobe geleverde componentpleister aanbrengen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)